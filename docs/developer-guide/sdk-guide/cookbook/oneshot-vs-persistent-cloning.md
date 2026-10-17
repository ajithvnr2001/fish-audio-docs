---
url: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/oneshot-vs-persistent-cloning/
title: One-shot vs persistent cloning: pick the right approach - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:35.614775+00:00
---

# One-shot vs persistent cloning: pick the right approach - Fish Audio

> Source: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/oneshot-vs-persistent-cloning/

## On this page

  * Prerequisites
  * Recipe
  * Train a persistent voice once, reuse forever
  * Which to choose
  * Related



Voice Cloning

# One-shot vs persistent cloning: pick the right approach

Copy pageCopy page

Choose between instant per-request cloning and a saved, reusable voice model

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

There are two ways to clone a voice. Pick by how often you’ll reuse it:

  * **One-shot (instant)** : pass a [`ReferenceAudio`](https://docs.fish.audio/api-reference/sdk/python/types#referenceaudio-objects) (raw bytes + exact transcript) on each `convert` call. Nothing is stored server-side; the clone lives only for that request.
  * **Persistent** : call `voices.create` once to train a model, then reuse its id as `reference_id` on every request. No reference upload per call, and the same voice is shared across processes.

Start with one-shot. Below, a single reference clip is cloned inline:

Synchronous

Asynchronous

JavaScript
    
    
    from fishaudio import FishAudio
    from fishaudio.types import ReferenceAudio
    from fishaudio.utils import save
    
    client = FishAudio()
    
    with open("reference.wav", "rb") as f:
        audio = client.tts.convert(
            text="This line is spoken in the cloned voice, no model required.",
            references=[ReferenceAudio(
                audio=f.read(),
                text="Exact transcript of what is said in reference.wav.",
            )],
        )
    
    save(audio, "oneshot.mp3")
    
    
    
    import asyncio
    from fishaudio import AsyncFishAudio
    from fishaudio.types import ReferenceAudio
    from fishaudio.utils import save
    
    async def main():
        async with AsyncFishAudio() as client:
            with open("reference.wav", "rb") as f:
                audio = await client.tts.convert(
                    text="This line is spoken in the cloned voice, no model required.",
                    references=[ReferenceAudio(
                        audio=f.read(),
                        text="Exact transcript of what is said in reference.wav.",
                    )],
                )
        save(audio, "oneshot.mp3")
    
    asyncio.run(main())
    
    
    
    import { FishAudioClient } from "fish-audio";
    import { readFile, writeFile } from "fs/promises";
    
    const client = new FishAudioClient({ apiKey: process.env.FISH_API_KEY });
    
    // One-shot: clone inline by sending the reference bytes + exact transcript.
    // Nothing is stored server-side; the clone lives only for this request.
    const reference = await readFile("reference.wav");
    
    const stream = await client.textToSpeech.convert(
      {
        text: "This line is spoken in the cloned voice, no model required.",
        references: [
          {
            audio: new File([reference], "reference.wav"),
            text: "Exact transcript of what is said in reference.wav.",
          },
        ],
        format: "mp3",
      },
      "s2-pro"
    );
    
    const chunks = [];
    for await (const chunk of stream) chunks.push(Buffer.from(chunk));
    await writeFile("oneshot.mp3", Buffer.concat(chunks));
    

One-shot re-sends the reference bytes on every request, so it’s ideal for one-off or rarely-repeated voices. Once a voice is used more than a handful of times, switch to a persistent model to skip the per-call upload.

## 

​

Train a persistent voice once, reuse forever

Call [`voices.create`](https://docs.fish.audio/api-reference/sdk/python/resources#create) to train a model, then pass `voice.id` as `reference_id`. The same id works from any process and across SDK and REST.
    
    
    with open("reference.wav", "rb") as f:
        voice = client.voices.create(title="My Narrator", voices=[f.read()])
    
    # reuse the same id on every later request; no reference upload
    audio = client.tts.convert(
        text="Reusing my saved voice across many requests.",
        reference_id=voice.id,
    )
    save(audio, "persistent.mp3")
    

Already have a trained voice id? Skip training and pass it directly:
    
    
    audio = client.tts.convert(text="Hello again.", reference_id="<voice-id>")
    

## 

​

Which to choose

| One-shot| Persistent  
---|---|---  
Setup| None| One `voices.create` call  
Per request| Re-uploads reference bytes| Sends only `reference_id`  
Stored server-side| No| Yes (manage with `voices.update` / `voices.delete`)  
Best for| One-off or experimental clones| Voices reused many times or across services  
  
For either path, give the reference 10–30 s of clean speech and make the transcript match the audio exactly (including punctuation) for the best prosody.

## 

​

Related

  * [Instant voice cloning](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/instant-voice-cloning)
  * [Voice Cloning guide](https://docs.fish.audio/features/voice-cloning)
  * [Manage voices](https://docs.fish.audio/features/manage-voices)



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/sdk-guide/cookbook/oneshot-vs-persistent-cloning.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/sdk-guide/cookbook/oneshot-vs-persistent-cloning)

[Clone a voice and wait until it is ready](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/clone-and-wait-until-ready)[Realtime: LLM tokens → speech](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-llm-to-speech)
