---
url: https://docs.fish.audio/features/voice-cloning/
title: Voice Cloning - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:40.128385+00:00
---

# Voice Cloning - Fish Audio

> Source: https://docs.fish.audio/features/voice-cloning/

## On this page

  * When to use it
  * Quick start
  * Use your cloned voice
  * Implementation details
    * Sample quality
    * Multiple samples
    * Visibility
  * Instant vs. persistent clones
  * Sample audio requirements
  * Model state
  * Going further



Core Features

# Voice Cloning

Copy pageCopy page

Create a custom voice from audio samples, then speak with it

Copy pageCopy page

Build a reusable voice model from your own audio, then use it anywhere you generate speech. You get back a voice **id**. Pass it as `reference_id` to [Text to Speech](https://docs.fish.audio/features/text-to-speech) and every generation speaks in that voice. Works from the API directly, the Python library, or JavaScript.

## Use it in the web app

No code: clone a voice in the browser.

## Professional Voice Clone

Verified, studio-quality clone you can release and earn from. Web app only.

## API reference

Every field for `POST /model`.

## Cookbooks

Instant clones, training, and reuse.

## 

​

When to use it

## Brand voice

One consistent voice across product, ads, and IVR.

## Personal voice

Clone your own voice for narration or assistants.

## Characters

Distinct voices for games, stories, and dialogue.

## Dubbing & localization

Keep a speaker’s identity across languages.

## 

​

Quick start

Send one or more audio samples, get back a voice model. Choose your implementation:

Python

API (curl)

JavaScript
    
    
    from fishaudio import FishAudio
    
    client = FishAudio()  # reads FISH_API_KEY
    
    with open("sample.wav", "rb") as f:
        voice = client.voices.create(
            title="My Voice",
            voices=[f.read()],
            description="Cloned from a studio sample",
            visibility="private",
        )
    
    print(voice.id, voice.state)
    
    
    
    curl --request POST https://api.fish.audio/model \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --form type=tts \
      --form title="My Voice" \
      --form "description=Cloned from a studio sample" \
      --form visibility=private \
      --form train_mode=fast \
      --form voices=@sample.wav
    
    # Returns the new model, including its "_id" and "state".
    
    
    
    import { FishAudioClient } from "fish-audio";
    import { readFile } from "fs/promises";
    
    const client = new FishAudioClient({ apiKey: process.env.FISH_API_KEY });
    
    const sample = await readFile("reference.wav");
    
    const voice = await client.voices.ivc.create({
      title: "My Voice",
      voices: [new File([sample], "reference.wav")],
      description: "Cloned from a studio sample",
      visibility: "private",
    });
    
    console.log(voice._id, voice.state);
    

## 

​

Use your cloned voice

Pass the voice **id** as `reference_id` to Text to Speech, exactly like any other voice.

Python

API (curl)
    
    
    audio = client.tts.convert(
        text="Now I speak in my cloned voice.",
        reference_id=voice.id,
    )
    
    
    
    curl --request POST https://api.fish.audio/v1/tts \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --header "model: s2-pro" \
      --data '{ "text": "Now I speak in my cloned voice.", "reference_id": "YOUR_VOICE_ID" }' \
      --output out.mp3
    

## 

​

Implementation details

### 

​

Sample quality

Clean, mono, single-speaker audio gives the best result. A short clip works for a quick clone; a minute or two of clear speech improves fidelity. Avoid background music, reverb, and overlapping voices.

### 

​

Multiple samples

Pass several clips to capture more range. You can also supply the matching transcripts as `texts` to sharpen pronunciation.

Python

API (curl)
    
    
    voice = client.voices.create(
        title="My Voice",
        voices=[open("a.wav", "rb").read(), open("b.wav", "rb").read()],
        texts=["Transcript of clip A.", "Transcript of clip B."],
    )
    
    
    
    curl --request POST https://api.fish.audio/model \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --form type=tts \
      --form title="My Voice" \
      --form voices=@a.wav \
      --form voices=@b.wav
    

### 

​

Visibility

Models are `private` by default. Set `unlist` for a shareable link, or `public` to publish to the [Voice Library](https://docs.fish.audio/overview/platform). You can change this later in [Manage Voices](https://docs.fish.audio/features/manage-voices).

## 

​

Instant vs. persistent clones

There are two ways to clone:

  * **Persistent model** (above): train once with `voices.create()`, get back a reusable `id`. Best when you’ll use the same voice repeatedly.
  * **Instant clone** : pass reference audio inline on each generation with no model to manage. Best for one-off or per-request voices.

For an instant clone, send the reference audio (and its transcript) directly to Text to Speech via `references` instead of `reference_id`:

Python
    
    
    from fishaudio import FishAudio
    from fishaudio.types import ReferenceAudio
    
    client = FishAudio()
    
    with open("reference.wav", "rb") as f:
        audio = client.tts.convert(
            text="This will sound like the reference voice.",
            references=[ReferenceAudio(
                audio=f.read(),
                text="The exact words spoken in the reference clip.",
            )],
        )
    

Pass several `ReferenceAudio` entries to capture more range, just as you would with multiple samples in a persistent model. The matching `text` for each clip sharpens pronunciation.

## 

​

Sample audio requirements

Samples can be `.wav`, `.mp3`, `.m4a`, or `.opus`. Aim for at least 10 seconds per clip; a minute or two of clear, single-speaker speech improves fidelity. `enhance_audio_quality` (on by default) removes background noise and normalizes levels before training:

Python
    
    
    voice = client.voices.create(
        title="My Voice",
        voices=[open("sample.wav", "rb").read()],
        enhance_audio_quality=True,
    )
    

Leave it on for noisy or lower-quality recordings. If your audio is already clean and studio-grade, turning it off (`enhance_audio_quality=False`) avoids any extra processing.

## 

​

Model state

A new model reports a `state` field that moves from `created` to `trained` (or `failed`). With `train_mode="fast"` (the default) the voice is usable almost immediately, so most clones return already `trained`.

Python
    
    
    voice = client.voices.create(title="My Voice", voices=[sample])
    print(voice.state)  # "trained"
    

If a generation rejects the `reference_id`, re-fetch the model and confirm its state before using it in Text to Speech:

Python
    
    
    voice = client.voices.get(voice.id)
    if voice.state == "trained":
        audio = client.tts.convert(text="Hello.", reference_id=voice.id)
    

## 

​

Going further

## Speak with your voice

Use `reference_id` in any generation.

## Manage your voices

List, update, and delete your voice models.

## Cloning best practices

Get the most natural results from your samples.

## Create Model API

Every field for `POST /model`.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/features/voice-cloning.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/features/voice-cloning)

[Voice Design](https://docs.fish.audio/features/voice-design)[Realtime Streaming](https://docs.fish.audio/features/realtime-streaming)
