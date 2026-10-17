---
url: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/transcribe-to-captions/
title: Transcribe audio to SRT/VTT captions - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:36.451684+00:00
---

# Transcribe audio to SRT/VTT captions - Fish Audio

> Source: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/transcribe-to-captions/

## On this page

  * Prerequisites
  * Recipe
  * Related



Speech to Text

# Transcribe audio to SRT/VTT captions

Copy pageCopy page

Transcribe audio with word-level timestamps, group the words into caption cues, and write valid SRT and WebVTT files

Copy pageCopy page

## 

​

Prerequisites

Create a Fish Audio account

Sign up for a free Fish Audio account to get started with our API.

  1. Go to [fish.audio/auth/signup](https://fish.audio/auth/signup)
  2. Fill in your details to create an account, complete steps to verify your account.
  3. Log in to your account and navigate to the [API section](https://fish.audio/app/api-keys)



Get your API key

Once you have an account, you’ll need an API key to authenticate your requests.

  1. Log in to your [Fish Audio Dashboard](https://fish.audio/app/api-keys/)
  2. Navigate to the API Keys section
  3. Click “Create New Key” and give it a descriptive name, set a expiration if desired
  4. Copy your key and store it securely



Keep your API key secret! Never commit it to version control or share it publicly.

## 

​

Recipe

This recipe uses `transcribe-1-pro`, which handles recordings up to 60 minutes long. Both tabs select it with the `model` request header; without that header, the request is served and billed as `transcribe-1`. Call [`asr.transcribe()`](https://docs.fish.audio/api-reference/sdk/python/resources#transcribe) with `include_timestamps=True` (in JavaScript, `ignore_timestamps: false`) to get timed segments ([`ASRSegment`](https://docs.fish.audio/api-reference/sdk/python/types#asrsegment-objects)). Segments are word-level (one character, or a few, in Chinese and Japanese) and carry no punctuation, so group consecutive segments into caption-sized cues before you format them. Segment `start` / `end` are in **seconds** ; SRT wants `HH:MM:SS,mmm` (comma), WebVTT wants `HH:MM:SS.mmm` (dot). The recipe starts a new cue after a pause longer than 0.6 seconds, or when the cue would grow past 42 characters or 6 seconds. It joins words with a space, except between Chinese or Japanese characters, which are written without spaces. A segment can have `start` equal to `end`, so a cue with no duration gets a short one that ends no later than the next cue starts. Every cue therefore ends after it starts, as SRT and WebVTT players expect.

Python

JavaScript
    
    
    import re
    
    from fishaudio import FishAudio
    from fishaudio.core import RequestOptions
    
    client = FishAudio()
    
    MAX_CHARS = 42  # longest cue text, in characters
    MAX_MS = 6000  # longest cue, in milliseconds
    MAX_GAP_MS = 600  # a longer pause between words starts a new cue
    MIN_MS = 500  # display time for a cue whose words have no duration
    
    # Chinese and Japanese are written without spaces between words.
    NO_SPACE = re.compile(r"[\u3040-\u30ff\u3400-\u4dbf\u4e00-\u9fff]")
    
    
    def join_words(left: str, right: str) -> str:
        if NO_SPACE.match(left[-1]) and NO_SPACE.match(right[0]):
            return left + right
        return f"{left} {right}"
    
    
    def group_cues(segments) -> list[dict]:
        """Group word-level segments into cues, with start and end in milliseconds."""
        cues = []
        for segment in segments:
            word = segment.text.strip()
            if not word:
                continue
            start, end = round(segment.start * 1000), round(segment.end * 1000)
            if cues:
                cue = cues[-1]
                text = join_words(cue["text"], word)
                if (
                    start - cue["end"] <= MAX_GAP_MS
                    and len(text) <= MAX_CHARS
                    and end - cue["start"] <= MAX_MS
                ):
                    cue["text"], cue["end"] = text, max(cue["end"], end)
                    continue
            cues.append({"start": start, "end": end, "text": word})
    
        # A segment can have start == end. Give a cue with no duration a short one,
        # ending no later than the next cue starts, so every cue ends after it starts.
        for i, cue in enumerate(cues):
            if cue["end"] <= cue["start"]:
                end = cue["start"] + MIN_MS
                if i + 1 < len(cues):
                    end = min(end, cues[i + 1]["start"])
                cue["end"] = max(end, cue["start"] + 1)
        return cues
    
    
    def format_timestamp(ms: int, separator: str) -> str:
        """HH:MM:SS,mmm for SRT (separator ","), HH:MM:SS.mmm for WebVTT (".")."""
        hours, ms = divmod(ms, 3_600_000)
        minutes, ms = divmod(ms, 60_000)
        seconds, ms = divmod(ms, 1000)
        return f"{hours:02d}:{minutes:02d}:{seconds:02d}{separator}{ms:03d}"
    
    
    with open("speech.wav", "rb") as f:
        result = client.asr.transcribe(
            audio=f.read(),
            include_timestamps=True,
            request_options=RequestOptions(
                timeout=900,  # long recordings can take several minutes
                additional_headers={"model": "transcribe-1-pro"},
            ),
        )
    
    cues = group_cues(result.segments)
    
    # SRT: 1-based index, comma decimal separator, blank line between cues.
    with open("captions.srt", "w", encoding="utf-8") as srt:
        for i, cue in enumerate(cues, start=1):
            start = format_timestamp(cue["start"], ",")
            end = format_timestamp(cue["end"], ",")
            srt.write(f"{i}\n{start} --> {end}\n{cue['text']}\n\n")
    
    # WebVTT: same cues, "WEBVTT" header, dot decimal separator.
    with open("captions.vtt", "w", encoding="utf-8") as vtt:
        vtt.write("WEBVTT\n\n")
        for cue in cues:
            start = format_timestamp(cue["start"], ".")
            end = format_timestamp(cue["end"], ".")
            vtt.write(f"{start} --> {end}\n{cue['text']}\n\n")
    
    print(f"Wrote {len(cues)} cues to captions.srt and captions.vtt")
    
    
    
    import { FishAudioClient } from "fish-audio";
    import { readFile, writeFile } from "fs/promises";
    
    const client = new FishAudioClient({ apiKey: process.env.FISH_API_KEY });
    
    const MAX_CHARS = 42; // longest cue text, in characters
    const MAX_MS = 6000; // longest cue, in milliseconds
    const MAX_GAP_MS = 600; // a longer pause between words starts a new cue
    const MIN_MS = 500; // display time for a cue whose words have no duration
    
    // Chinese and Japanese are written without spaces between words.
    const NO_SPACE = /[\u3040-\u30ff\u3400-\u4dbf\u4e00-\u9fff]/;
    
    function joinWords(left, right) {
      if (NO_SPACE.test(left.at(-1)) && NO_SPACE.test(right[0])) {
        return left + right;
      }
      return `${left} ${right}`;
    }
    
    // Group word-level segments into cues, with start and end in milliseconds.
    function groupCues(segments) {
      const cues = [];
      for (const segment of segments) {
        const word = segment.text.trim();
        if (!word) continue;
        const start = Math.round(segment.start * 1000);
        const end = Math.round(segment.end * 1000);
        const cue = cues.at(-1);
        if (cue) {
          const text = joinWords(cue.text, word);
          if (
            start - cue.end <= MAX_GAP_MS &&
            text.length <= MAX_CHARS &&
            end - cue.start <= MAX_MS
          ) {
            cue.text = text;
            cue.end = Math.max(cue.end, end);
            continue;
          }
        }
        cues.push({ start, end, text: word });
      }
    
      // A segment can have start == end. Give a cue with no duration a short one,
      // ending no later than the next cue starts, so every cue ends after it starts.
      cues.forEach((cue, i) => {
        if (cue.end <= cue.start) {
          let end = cue.start + MIN_MS;
          if (i + 1 < cues.length) end = Math.min(end, cues[i + 1].start);
          cue.end = Math.max(end, cue.start + 1);
        }
      });
      return cues;
    }
    
    // HH:MM:SS,mmm for SRT (separator ","), HH:MM:SS.mmm for WebVTT (".").
    function formatTimestamp(ms, separator) {
      const pad = (n, width) => String(n).padStart(width, "0");
      const hours = Math.floor(ms / 3_600_000);
      const minutes = Math.floor((ms % 3_600_000) / 60_000);
      const seconds = Math.floor((ms % 60_000) / 1000);
      const millis = ms % 1000;
      return `${pad(hours, 2)}:${pad(minutes, 2)}:${pad(seconds, 2)}${separator}${pad(millis, 3)}`;
    }
    
    const result = await client.speechToText.convert(
      {
        audio: new File([await readFile("speech.wav")], "speech.wav"),
        ignore_timestamps: false,
      },
      {
        headers: { model: "transcribe-1-pro" },
        timeoutInSeconds: 900, // long recordings can take several minutes
      }
    );
    
    const cues = groupCues(result.segments);
    const timing = (cue, separator) =>
      `${formatTimestamp(cue.start, separator)} --> ${formatTimestamp(cue.end, separator)}`;
    
    // SRT: 1-based index, comma decimal separator, blank line between cues.
    const srt = cues.map(
      (cue, i) => `${i + 1}\n${timing(cue, ",")}\n${cue.text}\n\n`
    );
    await writeFile("captions.srt", srt.join(""), "utf-8");
    
    // WebVTT: same cues, "WEBVTT" header, dot decimal separator.
    const vtt = cues.map(cue => `${timing(cue, ".")}\n${cue.text}\n\n`);
    await writeFile("captions.vtt", "WEBVTT\n\n" + vtt.join(""), "utf-8");
    
    console.log(`Wrote ${cues.length} cues to captions.srt and captions.vtt`);
    

Both tabs send the same request and write the same `captions.srt` and `captions.vtt`. Long recordings can take several minutes to transcribe, so both tabs set a 15-minute request timeout, longer than the SDKs’ default; in Node.js, also see the note below. Tune `MAX_CHARS`, `MAX_MS`, and `MAX_GAP_MS` for your player and audience. `segments` is empty when no speech was found or word timing was temporarily unavailable, and the files then contain no cues, so check the cue count before you publish them.

In Node.js, the built-in `fetch` that the JavaScript SDK uses stops waiting for a response after 5 minutes, even with a longer `timeoutInSeconds`. To wait longer, install `undici@7` and, once at startup, call its `setGlobalDispatcher(new Agent({ headersTimeout: 900_000, bodyTimeout: 900_000 }))`. See [Processing time and timeouts](https://docs.fish.audio/features/speech-to-text#processing-time-and-timeouts).

Captions built from `segments` have no punctuation. Because this recipe requests timestamps from `transcribe-1-pro`, the response also includes `speaker_turns`, with each turn’s punctuated text and its start and end time. To keep speakers in separate cues, start a new cue at each turn boundary. In JavaScript, read `result.speaker_turns`; it is not in the SDK’s TypeScript type. The Python SDK does not return `speaker_turns`; to read it from the API, see [Speaker turns](https://docs.fish.audio/features/speech-to-text#speaker-turns).

## 

​

Related

  * [Speech-to-Text guide](https://docs.fish.audio/features/speech-to-text)
  * [ASR Types Reference](https://docs.fish.audio/api-reference/sdk/python/types#fishaudio.types.asr)



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/sdk-guide/cookbook/transcribe-to-captions.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/sdk-guide/cookbook/transcribe-to-captions)

[Telephony-grade audio (8 kHz) for IVR and phone](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/telephony-8khz-audio)[Batch-transcribe files with a language hint](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/batch-transcribe-with-language-hint)
