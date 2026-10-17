---
url: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/batch-transcribe-with-language-hint/
title: Batch-transcribe files with a language hint - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:34.555967+00:00
---

# Batch-transcribe files with a language hint - Fish Audio

> Source: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/batch-transcribe-with-language-hint/

## On this page

  * Prerequisites
  * Recipe
  * Related



Speech to Text

# Batch-transcribe files with a language hint

Copy pageCopy page

Loop over local audio files and transcribe each with an explicit language, collecting text and duration per file

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

This recipe uses `transcribe-1-pro`, which handles recordings up to 60 minutes long. Every tab selects it with the `model` request header; without that header, the request is served and billed as `transcribe-1`. Read each file’s bytes from disk and pass them to [`asr.transcribe()`](https://docs.fish.audio/api-reference/sdk/python/resources#transcribe) with `language` set to a lowercase ISO 639-1 code such as `en`, `zh`, or `ja`. Other forms, such as `en-US` or `English`, may be rejected with 400. Pass `language` when you know the source language. Detection still runs, and the hint does not force the transcript into that language; the hint is reported as `language_code` when the language cannot be determined. See [Language](https://docs.fish.audio/features/speech-to-text#language) for details. Collect one result row per file as you go. If a file cannot be read, its request fails with a network error such as a timeout, or the API returns an error for it, record the error in that file’s row and move on to the next file.

Synchronous

Asynchronous

JavaScript
    
    
    import httpx
    from fishaudio import FishAudio
    from fishaudio.core import RequestOptions
    from fishaudio.exceptions import APIError
    
    client = FishAudio()
    
    paths = ["speech.wav"]  # add more file paths here
    language = "en"
    options = RequestOptions(
        timeout=900,  # long recordings can take several minutes
        additional_headers={"model": "transcribe-1-pro"},
    )
    
    results = []
    for path in paths:
        try:
            with open(path, "rb") as f:
                audio = f.read()
            transcript = client.asr.transcribe(
                audio=audio,
                language=language,
                include_timestamps=False,
                request_options=options,
            )
        except (OSError, httpx.HTTPError, APIError) as e:
            # Record the failure and continue with the next file.
            results.append({"file": path, "error": f"{type(e).__name__}: {e}"})
            continue
        results.append({
            "file": path,
            "text": transcript.text,
            "duration": transcript.duration,  # seconds
        })
    
    failed = [row for row in results if "error" in row]
    for row in results:
        if "error" in row:
            print(f"{row['file']}: FAILED: {row['error']}")
        else:
            print(f"{row['file']} ({row['duration']:.1f}s): {row['text']}")
    
    if failed:
        raise SystemExit(f"{len(failed)} of {len(results)} files failed")
    
    
    
    import asyncio
    
    import httpx
    from fishaudio import AsyncFishAudio
    from fishaudio.core import RequestOptions
    from fishaudio.exceptions import APIError
    
    async def main():
        async with AsyncFishAudio() as client:
            paths = ["speech.wav"]  # add more file paths here
            language = "en"
            options = RequestOptions(
                timeout=900,  # long recordings can take several minutes
                additional_headers={"model": "transcribe-1-pro"},
            )
    
            results = []
            for path in paths:
                try:
                    with open(path, "rb") as f:
                        audio = f.read()
                    transcript = await client.asr.transcribe(
                        audio=audio,
                        language=language,
                        include_timestamps=False,
                        request_options=options,
                    )
                except (OSError, httpx.HTTPError, APIError) as e:
                    # Record the failure and continue with the next file.
                    results.append({"file": path, "error": f"{type(e).__name__}: {e}"})
                    continue
                results.append({
                    "file": path,
                    "text": transcript.text,
                    "duration": transcript.duration,  # seconds
                })
        return results
    
    results = asyncio.run(main())
    
    failed = [row for row in results if "error" in row]
    for row in results:
        if "error" in row:
            print(f"{row['file']}: FAILED: {row['error']}")
        else:
            print(f"{row['file']} ({row['duration']:.1f}s): {row['text']}")
    
    if failed:
        raise SystemExit(f"{len(failed)} of {len(results)} files failed")
    
    
    
    import { FishAudioClient } from "fish-audio";
    import { readFile } from "fs/promises";
    
    const client = new FishAudioClient({ apiKey: process.env.FISH_API_KEY });
    
    const paths = ["speech.wav"]; // add more file paths here
    const language = "en";
    const options = {
      headers: { model: "transcribe-1-pro" },
      timeoutInSeconds: 900, // long recordings can take several minutes
    };
    
    const results = [];
    for (const path of paths) {
      try {
        const audio = new File([await readFile(path)], path);
        const transcript = await client.speechToText.convert(
          { audio, language },
          options
        );
        results.push({
          file: path,
          text: transcript.text,
          duration: transcript.duration, // seconds
        });
      } catch (err) {
        // Record the failure and continue with the next file.
        const error = err.statusCode
          ? `HTTP ${err.statusCode}: ${err.body?.message ?? "(no JSON body)"}`
          : err.message;
        results.push({ file: path, error });
      }
    }
    
    const failed = results.filter(row => row.error);
    for (const row of results) {
      if (row.error) {
        console.log(`${row.file}: FAILED: ${row.error}`);
      } else {
        console.log(`${row.file} (${row.duration.toFixed(1)}s): ${row.text}`);
      }
    }
    
    if (failed.length > 0) {
      console.error(`${failed.length} of ${results.length} files failed`);
      // Exit now: a request that failed with a network error can leave its timeout running.
      process.exit(1);
    }
    

Each call returns an [`ASRResponse`](https://docs.fish.audio/api-reference/sdk/python/types#asrresponse-objects) with `.text` and `.duration` (seconds). With `transcribe-1-pro`, `text` can contain inline speaker markers such as `<|speaker:0|>` and cues such as `[laughter]`; see [Speaker markers](https://docs.fish.audio/features/speech-to-text#speaker-markers) to split it into turns. This recipe skips timestamps; pass `include_timestamps=True` (Python) or `ignore_timestamps: false` (JavaScript) for word-level `.segments`. The Python SDK currently returns only `text`, `duration`, and `segments`; to read `language_code`, call the API directly (see [Direct API](https://docs.fish.audio/features/speech-to-text#direct-api-messagepack)). A file that fails is recorded with its error, and the loop continues. After the summary, the script exits with a non-zero status if any file failed, so a scheduled job does not report success. A file that failed with 429, a 5xx status, or a network error such as a timeout is worth retrying later with backoff; for other 4xx errors, fix the file or the request first. Long recordings can take several minutes to transcribe, so every tab sets a 15-minute request timeout, longer than the SDKs’ default; in Node.js, also see the note below.

In Node.js, the built-in `fetch` that the JavaScript SDK uses stops waiting for a response after 5 minutes, even with a longer `timeoutInSeconds`. To wait longer, install `undici@7` and, once at startup, call its `setGlobalDispatcher(new Agent({ headersTimeout: 900_000, bodyTimeout: 900_000 }))`. See [Processing time and timeouts](https://docs.fish.audio/features/speech-to-text#processing-time-and-timeouts).

Use one `language` per batch; split mixed-language files into separate lists.

## 

​

Related

  * [Speech-to-Text guide](https://docs.fish.audio/features/speech-to-text)
  * [Instant voice cloning](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/instant-voice-cloning)



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/sdk-guide/cookbook/batch-transcribe-with-language-hint.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/sdk-guide/cookbook/batch-transcribe-with-language-hint)

[Transcribe audio to SRT/VTT captions](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/transcribe-to-captions)[Instant voice cloning](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/instant-voice-cloning)
