---
url: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/voice-agent-loop/
title: Build a voice agent loop: speech in, reply, speech out - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-20T12:52:00.954778+00:00
---

# Build a voice agent loop: speech in, reply, speech out - Fish Audio

> Source: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/voice-agent-loop/

## On this page

  * Prerequisites
  * Recipe
  * Reply in the caller’s voice
  * Related



Realtime Streaming

# Build a voice agent loop: speech in, reply, speech out

Copy pageCopy page

Transcribe an utterance, generate a reply with your own LLM, and stream that reply back out as speech

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

A voice agent is three stages chained together: [`asr.transcribe()`](https://docs.fish.audio/api-reference/sdk/python/resources#transcribe) turns the caller’s audio into text, your own LLM turns that text into a reply, and [`tts.stream()`](https://docs.fish.audio/api-reference/sdk/python/resources#stream) turns the reply back into speech. The transcript and the reply are just strings, so the only Fish Audio-specific parts are the first and last calls. Streaming the reply lets you start writing (or forwarding) audio before the whole sentence is synthesized. The recipe transcribes with `transcribe-1-pro`. Every tab selects it with the `model` request header; without that header, the request is served and billed as `transcribe-1`.

Synchronous

Asynchronous

JavaScript
    
    
    import re
    
    from fishaudio import FishAudio
    from fishaudio.core import RequestOptions
    from fishaudio.utils import save
    
    client = FishAudio()
    
    def reply_from_llm(text: str) -> str:
        # ---- PLACEHOLDER ----
        # Call your own LLM here and return its reply as a string.
        # e.g. return openai_client.chat.completions.create(...).choices[0].message.content
        return f"You said: {text}. How can I help?"
    
    def voice_agent_turn(audio_path: str, out_path: str) -> str:
        with open(audio_path, "rb") as f:
            heard = client.asr.transcribe(
                audio=f.read(),
                include_timestamps=False,
                request_options=RequestOptions(
                    additional_headers={"model": "transcribe-1-pro"}
                ),
            )
    
        # Drop speaker markers such as <|speaker:0|>; keep cues such as [laughter].
        said = re.sub(r"\s*<\|speaker:\d+\|>\s*", " ", heard.text).strip()
        reply = reply_from_llm(said)
    
        audio_stream = client.tts.stream(text=reply, reference_id="<voice-id>")
        save(audio_stream, out_path)  # writes chunks as they arrive
        return reply
    
    reply = voice_agent_turn("speech.wav", "reply.mp3")
    print("Agent:", reply)
    
    
    
    import asyncio
    import re
    
    from fishaudio import AsyncFishAudio
    from fishaudio.core import RequestOptions
    from fishaudio.utils import save
    
    def reply_from_llm(text: str) -> str:
        # ---- PLACEHOLDER ----
        # Call your own LLM here and return its reply as a string.
        return f"You said: {text}. How can I help?"
    
    async def main():
        async with AsyncFishAudio() as client:
            with open("speech.wav", "rb") as f:
                heard = await client.asr.transcribe(
                    audio=f.read(),
                    include_timestamps=False,
                    request_options=RequestOptions(
                        additional_headers={"model": "transcribe-1-pro"}
                    ),
                )
    
            # Drop speaker markers such as <|speaker:0|>; keep cues such as [laughter].
            said = re.sub(r"\s*<\|speaker:\d+\|>\s*", " ", heard.text).strip()
            reply = reply_from_llm(said)
    
            audio_stream = await client.tts.stream(text=reply, reference_id="<voice-id>")
            with open("reply.mp3", "wb") as out:
                async for chunk in audio_stream:
                    out.write(chunk)
            print("Agent:", reply)
    
    asyncio.run(main())
    
    
    
    import { FishAudioClient } from "fish-audio";
    import { readFile, writeFile } from "fs/promises";
    
    const client = new FishAudioClient({ apiKey: process.env.FISH_API_KEY });
    
    function replyFromLlm(text) {
      // ---- PLACEHOLDER ----
      // Call your own LLM here and return its reply as a string.
      // e.g. return openaiClient.chat.completions.create(...).choices[0].message.content
      return `You said: ${text}. How can I help?`;
    }
    
    async function voiceAgentTurn(audioPath, outPath) {
      const heard = await client.speechToText.convert(
        {
          audio: new File([await readFile(audioPath)], audioPath),
          language: "en",
        },
        { headers: { model: "transcribe-1-pro" } }
      );
    
      // Drop speaker markers such as <|speaker:0|>; keep cues such as [laughter].
      const said = heard.text.replace(/\s*<\|speaker:\d+\|>\s*/g, " ").trim();
      const reply = replyFromLlm(said);
    
      const stream = await client.textToSpeech.convert(
        { text: reply, reference_id: "<voice-id>", format: "mp3" },
        "s2-pro"
      );
      const chunks = [];
      for await (const chunk of stream) chunks.push(Buffer.from(chunk));
      await writeFile(outPath, Buffer.concat(chunks));
      return reply;
    }
    
    const reply = await voiceAgentTurn("speech.wav", "reply.mp3");
    console.log("Agent:", reply);
    

`heard` is an [`ASRResponse`](https://docs.fish.audio/api-reference/sdk/python/types#asrresponse-objects): `heard.text` is the full transcript and `heard.duration` is the clip length in seconds. With `transcribe-1-pro`, `heard.text` can contain inline speaker markers such as `<|speaker:0|>` and cues such as `[laughter]`. The recipe removes the speaker markers before it calls your LLM and keeps the cues as context; see [Speaker markers](https://docs.fish.audio/features/speech-to-text#speaker-markers). The Python calls pass `include_timestamps=False` because the loop needs only the text, and word timestamps add processing time. Pass `language="en"` as a hint when you know the caller’s language; see [Language](https://docs.fish.audio/features/speech-to-text#language).

For the lowest latency, feed your LLM’s token stream straight into [`stream_websocket()`](https://docs.fish.audio/api-reference/sdk/python/resources#stream_websocket) instead of waiting for the full reply string. See [Realtime: LLM tokens → speech](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-llm-to-speech).

## 

​

Reply in the caller’s voice

`reference_id` points the reply at a saved voice. Drop it to use the default voice, or clone the caller’s voice from the same clip you just transcribed by passing `references` instead. See [Instant voice cloning](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/instant-voice-cloning).

This recipe handles one recorded utterance at a time. To listen to a live conversation, with turn detection, interruptions and backchannels, see [Build a realtime voice agent](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-voice-agent).

## 

​

Related

  * [Speech-to-Text guide](https://docs.fish.audio/features/speech-to-text)
  * [Build a realtime voice agent](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-voice-agent)
  * [Realtime: LLM tokens → speech](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-llm-to-speech)
  * [Stream TTS to a file](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/streaming-to-file)



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/sdk-guide/cookbook/voice-agent-loop.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/sdk-guide/cookbook/voice-agent-loop)

[Realtime: LLM tokens → speech](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-llm-to-speech)[Build a realtime voice agent: streaming speech in, reply, speech out](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-voice-agent)
