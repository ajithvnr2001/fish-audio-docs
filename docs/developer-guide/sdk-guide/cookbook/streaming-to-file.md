---
url: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/streaming-to-file/
title: Stream TTS to a file - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:35.803449+00:00
---

# Stream TTS to a file - Fish Audio

> Source: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/streaming-to-file/

## On this page

  * Prerequisites
  * Recipe
  * Collect instead of iterate
  * Related



Text to Speech

# Stream TTS to a file

Copy pageCopy page

Generate long audio and write it to disk chunk-by-chunk, without buffering it all in memory

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

For long text, use [`stream()`](https://docs.fish.audio/api-reference/sdk/python/resources#stream) and write each chunk as it arrives instead of holding the whole file in memory.

Synchronous

Asynchronous

JavaScript
    
    
    from fishaudio import FishAudio
    
    client = FishAudio()
    
    with open("output.mp3", "wb") as f:
        for chunk in client.tts.stream(text="A very long passage of text..."):
            f.write(chunk)
    
    
    
    import asyncio
    from fishaudio import AsyncFishAudio
    
    async def main():
        async with AsyncFishAudio() as client:
            audio_stream = await client.tts.stream(text="A very long passage of text...")
            with open("output.mp3", "wb") as f:
                async for chunk in audio_stream:
                    f.write(chunk)
    
    asyncio.run(main())
    
    
    
    import { FishAudioClient } from "fish-audio";
    import { createWriteStream } from "fs";
    
    const client = new FishAudioClient({ apiKey: process.env.FISH_API_KEY });
    
    // convert() returns a ReadableStream<Uint8Array>. Iterate it and write each
    // chunk as it arrives, so you never hold the whole file in memory.
    const stream = await client.textToSpeech.convert(
      { text: "A very long passage of text...", format: "mp3" },
      "s2-pro"
    );
    
    const file = createWriteStream("output.mp3");
    for await (const chunk of stream) {
      file.write(Buffer.from(chunk));
    }
    file.end();
    

## 

​

Collect instead of iterate

If you just want the full bytes, call `.collect()`:
    
    
    audio = client.tts.stream(text="Hello!").collect()  # -> bytes
    

`convert()` already returns the complete audio as `bytes`. Reach for `stream()` when you want to start writing/forwarding bytes before generation finishes, or to avoid buffering large files.

## 

​

Related

  * [Text-to-Speech guide](https://docs.fish.audio/features/text-to-speech)
  * [Realtime: LLM tokens → speech](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-llm-to-speech)



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/sdk-guide/cookbook/streaming-to-file.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/sdk-guide/cookbook/streaming-to-file)

[Errors & Retries](https://docs.fish.audio/developer-guide/sdk-guide/python/errors)[Telephony-grade audio (8 kHz) for IVR and phone](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/telephony-8khz-audio)
