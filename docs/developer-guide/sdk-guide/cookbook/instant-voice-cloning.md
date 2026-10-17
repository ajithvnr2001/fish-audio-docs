---
url: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/instant-voice-cloning/
title: Instant voice cloning - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:35.136932+00:00
---

# Instant voice cloning - Fish Audio

> Source: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/instant-voice-cloning/

## On this page

  * Prerequisites
  * Recipe
  * Reuse a voice across many requests
  * Related



Voice Cloning

# Instant voice cloning

Copy pageCopy page

Clone a voice on the fly from a short reference clip, with no model to manage

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

Pass a [`ReferenceAudio`](https://docs.fish.audio/api-reference/sdk/python/types#referenceaudio-objects) (raw audio bytes + an exact transcript) on the `convert` call. Nothing is saved server-side; the clone applies to that request only.

Synchronous

Asynchronous

JavaScript
    
    
    from fishaudio import FishAudio
    from fishaudio.types import ReferenceAudio
    from fishaudio.utils import save
    
    client = FishAudio()
    
    with open("reference.wav", "rb") as f:
        audio = client.tts.convert(
            text="This sentence is spoken in the cloned voice.",
            references=[ReferenceAudio(
                audio=f.read(),
                text="Exact transcript of what is said in reference.wav.",
            )],
        )
    
    save(audio, "cloned.mp3")
    
    
    
    import asyncio
    from fishaudio import AsyncFishAudio
    from fishaudio.types import ReferenceAudio
    from fishaudio.utils import save
    
    async def main():
        async with AsyncFishAudio() as client:
            with open("reference.wav", "rb") as f:
                audio = await client.tts.convert(
                    text="This sentence is spoken in the cloned voice.",
                    references=[ReferenceAudio(
                        audio=f.read(),
                        text="Exact transcript of what is said in reference.wav.",
                    )],
                )
        save(audio, "cloned.mp3")
    
    asyncio.run(main())
    
    
    
    import { FishAudioClient } from "fish-audio";
    import { readFile, writeFile } from "fs/promises";
    
    const client = new FishAudioClient({ apiKey: process.env.FISH_API_KEY });
    
    const reference = new File(
      [await readFile("reference.wav")],
      "reference.wav",
    );
    
    const stream = await client.textToSpeech.convert(
      {
        text: "This sentence is spoken in the cloned voice.",
        references: [
          {
            audio: reference,
            text: "Exact transcript of what is said in reference.wav.",
          },
        ],
        format: "mp3",
      },
      "s2-pro",
    );
    
    const chunks = [];
    for await (const chunk of stream) chunks.push(Buffer.from(chunk));
    
    await writeFile("cloned.mp3", Buffer.concat(chunks));
    

Use 10–30 s of clean speech, and make `text` match the audio exactly (including punctuation) for the best prosody.

## 

​

Reuse a voice across many requests

If you’ll use the voice repeatedly, create a persistent model once and pass its id as `reference_id`. See the [Voice Cloning guide](https://docs.fish.audio/features/voice-cloning).
    
    
    with open("sample.wav", "rb") as f:
        voice = client.voices.create(title="My Voice", voices=[f.read()])
    
    audio = client.tts.convert(text="Reusing my saved voice.", reference_id=voice.id)
    

## 

​

Related

  * [Voice Cloning guide](https://docs.fish.audio/features/voice-cloning)
  * [Stream TTS to a file](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/streaming-to-file)



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/sdk-guide/cookbook/instant-voice-cloning.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/sdk-guide/cookbook/instant-voice-cloning)

[Batch-transcribe files with a language hint](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/batch-transcribe-with-language-hint)[Clone a voice and wait until it is ready](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/clone-and-wait-until-ready)
