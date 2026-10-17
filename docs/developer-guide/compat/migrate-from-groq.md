---
url: https://docs.fish.audio/developer-guide/compat/migrate-from-groq/
title: Migrate from Groq - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:27.984410+00:00
---

# Migrate from Groq - Fish Audio

> Source: https://docs.fish.audio/developer-guide/compat/migrate-from-groq/

## On this page

  * Text to speech
  * Transcription
  * Model catalog
  * Error handling
  * Going further



Compatible APIs

# Migrate from Groq

Copy pageCopy page

Point the official Groq SDKs at Fish Audio: TTS, transcription, and the model catalog.

Copy pageCopy page

Configure the client once. The Groq SDK speaks the OpenAI protocol and appends `/openai/v1` to its base URL itself, so give it the bare `/compat` base:

Python

Node
    
    
    import os
    
    from groq import Groq
    
    client = Groq(
        base_url="https://api.fish.audio/compat",
        api_key=os.environ["FISH_AUDIO_API_KEY"],
    )
    
    
    
    import Groq from "groq-sdk";
    
    const client = new Groq({
      apiKey: process.env.FISH_AUDIO_API_KEY,
      baseURL: "https://api.fish.audio/compat",
    });
    

`/openai/v1` speaks the same protocol the OpenAI SDK uses, so everything in [Migrate from OpenAI](https://docs.fish.audio/developer-guide/compat/migrate-from-openai) applies here too. Model names your Groq code already sends keep working: `playai-tts` maps to `fish-audio/s2.1-pro`, and `whisper-large-v3`, `whisper-large-v3-turbo`, and `distil-whisper-large-v3-en` map to `fish-audio/transcribe-1`. Anything outside the catalog returns a 400.

Feature| Supported  
---|---  
Text to speech (streamed)| ✓  
Speech to text + word timestamps| ✓  
Model catalog (list)| ✓  
Realtime WebSocket| via the OpenAI SDK  
TTS character timestamps| –  
Speech translation| –  
Voice library listing| –  
  
## 

​

Text to speech

Python

Node

curl
    
    
    resp = client.audio.speech.create(
        model="fish-audio/s2.1-pro",
        input="Hello from Fish Audio!",
        voice="",  # a voice ID from your Fish voice library; "" = model default
        response_format="mp3",
    )
    open("hello.mp3", "wb").write(resp.read())
    
    
    
    import fs from "node:fs";
    
    const resp = await client.audio.speech.create({
      model: "fish-audio/s2.1-pro",
      input: "Hello from Fish Audio!",
      voice: "", // a voice ID from your Fish voice library; "" = model default
      response_format: "mp3",
    });
    fs.writeFileSync("hello.mp3", Buffer.from(await resp.arrayBuffer()));
    
    
    
    curl https://api.fish.audio/compat/openai/v1/audio/speech \
      -H "Authorization: Bearer $FISH_AUDIO_API_KEY" \
      -H "Content-Type: application/json" \
      -d '{"model": "fish-audio/s2.1-pro",
           "input": "Hello from Fish Audio!",
           "response_format": "mp3"}' \
      --output hello.mp3
    

Audio streams as it is synthesized. Set `response_format` explicitly; it defaults to `pcm` on this endpoint, not `mp3`. `voice` is a Fish voice ID, not a vendor preset; see [Voices](https://docs.fish.audio/developer-guide/getting-started/migration#voices). The accepted formats are `mp3`, `pcm`, `pcm16`, `wav`, and `opus`, the same set as the rest of `/openai/v1`; the `flac`, `mulaw`, and `ogg` the SDK types also offer are formats Fish cannot produce and return a 400. `sample_rate` (Hz) is accepted as an extension field on the request body (untyped: `extra_body` in Python, an extra property in Node; defaults to 44100); asking for a rate the codec doesn’t take is a 400, and the per-codec rate table is in [Audio formats](https://docs.fish.audio/developer-guide/compat/capabilities#audio-formats).

Groq SDK type quirks: casting pcm, pcm16, opus, and srt, vtt

The SDK’s `response_format` types omit `pcm`, `pcm16`, and `opus`, and the same `Literal` narrows the Python SDK, so type checkers flag them there too. Cast at the call site:

Python

TypeScript
    
    
    response_format="opus",  # type: ignore[arg-type]
    
    
    
    response_format: "opus" as SpeechCreateParams["response_format"],
    

The transcription side types `response_format` as `json | text | verbose_json`, so `srt`/`vtt` need the same cast, and the SDK hands the subtitle document back as a plain string even though the method is typed to return `Transcription`.

## 

​

Transcription

Python

Node

curl
    
    
    tr = client.audio.transcriptions.create(
        model="fish-audio/transcribe-1",
        file=open("hello.mp3", "rb"),
    )
    print(tr.text)
    
    
    
    import fs from "node:fs";
    
    const buf = fs.readFileSync("hello.mp3");
    const tr = await client.audio.transcriptions.create({
      model: "fish-audio/transcribe-1",
      file: new File([buf], "hello.mp3"),
    });
    console.log(tr.text);
    
    
    
    curl https://api.fish.audio/compat/openai/v1/audio/transcriptions \
      -H "Authorization: Bearer $FISH_AUDIO_API_KEY" \
      -F model=fish-audio/transcribe-1 \
      -F file=@hello.mp3
    

`verbose_json`, word-level timestamp granularity, and the subtitle formats (`srt`, `vtt`) work as they do on the OpenAI protocol; details and placeholder-field caveats in [Migrate from OpenAI](https://docs.fish.audio/developer-guide/compat/migrate-from-openai#transcription); `srt`/`vtt` need the SDK type cast shown above. Translation has no counterpart: Fish has no translation model, so `client.audio.translations` returns a 404. Transcribe in the source language and translate the text downstream.

## 

​

Model catalog

Python

Node

curl
    
    
    ids = [m.id for m in client.models.list().data]
    # ["fish-audio/s2.1-pro", "fish-audio/s2.1-pro-free", ...]
    
    
    
    const models = await client.models.list();
    const ids = models.data.map(m => m.id);
    // ["fish-audio/s2.1-pro", "fish-audio/s2.1-pro-free", ...]
    
    
    
    # No auth required
    curl https://api.fish.audio/compat/openai/v1/models
    

Entries follow the OpenRouter model schema: `id` and `created` are populated, but the Groq SDK’s other declared `Model` fields (`object`, `owned_by`, `active`, `context_window`) come back `undefined`, and the richer Fish fields (`pricing`, `architecture`, `supported_parameters`) are present but untyped. Listing only: there is no per-model route, so `models.retrieve(...)` returns a 404.

## 

​

Error handling

Errors map to the Groq SDK’s typed exceptions (`AuthenticationError`, `RateLimitError`, …) with the same envelope as the OpenAI protocol: the HTTP status as an integer `error.code` on every error. Failures from the Fish Audio API keep their original status with `type: "provider_error"` and add `metadata.provider_name: "fish-audio"`; errors from the compatibility layer itself carry no `metadata`.

## 

​

Going further

## Migrate from OpenAI

Everything behind `/openai/v1`: chat-modality audio, Realtime WebSocket, error mapping.

## Compatibility

The full contract: mappings, limits, and explicit refusals.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/compat/migrate-from-groq.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/compat/migrate-from-groq)

[From ElevenLabs](https://docs.fish.audio/developer-guide/compat/migrate-from-elevenlabs)[Compatibility](https://docs.fish.audio/developer-guide/compat/capabilities)
