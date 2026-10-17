---
url: https://docs.fish.audio/developer-guide/getting-started/migration/
title: Migrate to Fish Audio - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:31.590382+00:00
---

# Migrate to Fish Audio - Fish Audio

> Source: https://docs.fish.audio/developer-guide/getting-started/migration/

## On this page

  * From a framework
  * Models
  * Voices
  * Going further



Get Started

# Migrate to Fish Audio

Copy pageCopy page

Run your existing OpenAI, OpenRouter, ElevenLabs, or Groq code on Fish Audio.

Copy pageCopy page

Your SDK| Base URL  
---|---  
OpenAI| `https://api.fish.audio/compat/v1`  
OpenRouter| `https://api.fish.audio/compat/api/v1`  
ElevenLabs| `https://api.fish.audio/compat/elevenlabs`  
Groq| `https://api.fish.audio/compat`  
  
  * OpenAI

  * OpenRouter

  * ElevenLabs

  * Groq




1

Set your API key

Store your [Fish Audio API key](https://docs.fish.audio/developer-guide/getting-started/api-key) as an environment variable:
    
    
    export FISH_AUDIO_API_KEY="your_api_key"
    

2

Swap the base URL and generate

Python

Node

curl
    
    
    import os
    from openai import OpenAI
    
    client = OpenAI(
        base_url="https://api.fish.audio/compat/v1",
        api_key=os.environ["FISH_AUDIO_API_KEY"],
    )
    
    with client.audio.speech.with_streaming_response.create(
        model="fish-audio/s2.1-pro",
        input="Hello from Fish Audio!",
        voice="",  # "" = default voice; see Voices below to pick one
        response_format="mp3",
    ) as response:
        response.stream_to_file("hello.mp3")
    
    
    
    import OpenAI from "openai";
    import fs from "node:fs";
    
    const client = new OpenAI({
      baseURL: "https://api.fish.audio/compat/v1",
      apiKey: process.env.FISH_AUDIO_API_KEY,
    });
    
    const response = await client.audio.speech.create({
      model: "fish-audio/s2.1-pro",
      input: "Hello from Fish Audio!",
      voice: "", // "" = default voice; see Voices below to pick one
      response_format: "mp3",
    });
    fs.writeFileSync("hello.mp3", Buffer.from(await response.arrayBuffer()));
    
    
    
    curl https://api.fish.audio/compat/v1/audio/speech \
      -H "Authorization: Bearer $FISH_AUDIO_API_KEY" \
      -H "Content-Type: application/json" \
      -d '{"model": "fish-audio/s2.1-pro",
           "input": "Hello from Fish Audio!",
           "response_format": "mp3"}' \
      --output hello.mp3
    

Full guide: [Migrate from OpenAI](https://docs.fish.audio/developer-guide/compat/migrate-from-openai), covering transcription, chat audio, the Realtime WebSocket, and what each feature supports.

1

Set your API key

Store your [Fish Audio API key](https://docs.fish.audio/developer-guide/getting-started/api-key) as an environment variable:
    
    
    export FISH_AUDIO_API_KEY="your_api_key"
    

2

Swap the base URL and generate

From Python, use the OpenAI SDK against the same `/api/v1` base; that is how OpenRouter itself is used from Python.

Node

Python

curl
    
    
    import { OpenRouter } from "@openrouter/sdk";
    import fs from "node:fs";
    
    const client = new OpenRouter({
      apiKey: process.env.FISH_AUDIO_API_KEY,
      serverURL: "https://api.fish.audio/compat/api/v1",
    });
    
    const stream = await client.tts.createSpeech({
      speechRequest: {
        model: "fish-audio/s2.1-pro",
        input: "Hello from Fish Audio!",
        responseFormat: "mp3",
      },
    });
    const chunks = [];
    for await (const chunk of stream) chunks.push(chunk);
    fs.writeFileSync("hello.mp3", Buffer.concat(chunks));
    
    
    
    import os
    from openai import OpenAI
    
    client = OpenAI(
        base_url="https://api.fish.audio/compat/api/v1",
        api_key=os.environ["FISH_AUDIO_API_KEY"],
    )
    
    with client.audio.speech.with_streaming_response.create(
        model="fish-audio/s2.1-pro",
        input="Hello from Fish Audio!",
        voice="",  # "" = default voice; see Voices below to pick one
        response_format="mp3",
    ) as response:
        response.stream_to_file("hello.mp3")
    
    
    
    curl https://api.fish.audio/compat/api/v1/audio/speech \
      -H "Authorization: Bearer $FISH_AUDIO_API_KEY" \
      -H "Content-Type: application/json" \
      -d '{"model": "fish-audio/s2.1-pro",
           "input": "Hello from Fish Audio!",
           "response_format": "mp3"}' \
      --output hello.mp3
    

Full guide: [Migrate from OpenRouter](https://docs.fish.audio/developer-guide/compat/migrate-from-openrouter), covering transcription, the model catalog, and what each feature supports.

1

Set your API key

Store your [Fish Audio API key](https://docs.fish.audio/developer-guide/getting-started/api-key) as an environment variable:
    
    
    export FISH_AUDIO_API_KEY="your_api_key"
    

2

Swap the base URL and generate

The key is sent as the standard `xi-api-key` header:

Python

Node

curl
    
    
    import os
    from elevenlabs import ElevenLabs
    
    client = ElevenLabs(
        base_url="https://api.fish.audio/compat/elevenlabs",
        api_key=os.environ["FISH_AUDIO_API_KEY"],
    )
    
    audio = b"".join(client.text_to_speech.convert(
        voice_id="default",  # "default" = default voice; see Voices below
        text="Hello from Fish Audio!",
        model_id="fish-audio/s2.1-pro",
        output_format="mp3_44100_128",
    ))
    open("hello.mp3", "wb").write(audio)
    
    
    
    import { ElevenLabsClient } from "@elevenlabs/elevenlabs-js";
    import fs from "node:fs";
    
    const client = new ElevenLabsClient({
      baseUrl: "https://api.fish.audio/compat/elevenlabs",
      apiKey: process.env.FISH_AUDIO_API_KEY,
    });
    
    // "default" = default voice; see Voices below to pick one
    const stream = await client.textToSpeech.convert("default", {
      text: "Hello from Fish Audio!",
      modelId: "fish-audio/s2.1-pro",
      outputFormat: "mp3_44100_128",
    });
    const chunks = [];
    for await (const chunk of stream) chunks.push(chunk);
    fs.writeFileSync("hello.mp3", Buffer.concat(chunks));
    
    
    
    curl "https://api.fish.audio/compat/elevenlabs/v1/text-to-speech/default?output_format=mp3_44100_128" \
      -H "xi-api-key: $FISH_AUDIO_API_KEY" \
      -H "Content-Type: application/json" \
      -d '{"text": "Hello from Fish Audio!",
           "model_id": "fish-audio/s2.1-pro"}' \
      --output hello.mp3
    

Full guide: [Migrate from ElevenLabs](https://docs.fish.audio/developer-guide/compat/migrate-from-elevenlabs), covering speech-to-text, timestamps, realtime streaming, your voice library, and what each feature supports.

1

Set your API key

Store your [Fish Audio API key](https://docs.fish.audio/developer-guide/getting-started/api-key) as an environment variable:
    
    
    export FISH_AUDIO_API_KEY="your_api_key"
    

2

Swap the base URL and generate

The Groq SDK appends `/openai/v1` itself, so give it the bare `/compat` base:

Python

Node

curl
    
    
    import os
    from groq import Groq
    
    client = Groq(
        base_url="https://api.fish.audio/compat",
        api_key=os.environ["FISH_AUDIO_API_KEY"],
    )
    
    resp = client.audio.speech.create(
        model="fish-audio/s2.1-pro",
        input="Hello from Fish Audio!",
        voice="",  # "" = default voice; see Voices below to pick one
        response_format="mp3",
    )
    open("hello.mp3", "wb").write(resp.read())
    
    
    
    import Groq from "groq-sdk";
    import fs from "node:fs";
    
    const client = new Groq({
      apiKey: process.env.FISH_AUDIO_API_KEY,
      baseURL: "https://api.fish.audio/compat",
    });
    
    const resp = await client.audio.speech.create({
      model: "fish-audio/s2.1-pro",
      input: "Hello from Fish Audio!",
      voice: "", // "" = default voice; see Voices below to pick one
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
    

Full guide: [Migrate from Groq](https://docs.fish.audio/developer-guide/compat/migrate-from-groq), covering transcription, the model catalog, and what each feature supports.

## 

​

From a framework

Frameworks that speak the OpenAI protocol work the same way: point them at `/compat/v1`:

LangChain

Vercel AI SDK
    
    
    import base64
    import os
    from langchain_openai import ChatOpenAI
    
    llm = ChatOpenAI(
        base_url="https://api.fish.audio/compat/v1",
        api_key=os.environ["FISH_AUDIO_API_KEY"],
        model="fish-audio/s2.1-pro",
        model_kwargs={"modalities": ["text", "audio"],
                      "audio": {"voice": "", "format": "mp3"}},
    )
    
    resp = llm.invoke("Hello from Fish Audio!")
    audio = base64.b64decode(resp.additional_kwargs["audio"]["data"])
    open("hello.mp3", "wb").write(audio)
    
    
    
    import { experimental_generateSpeech as generateSpeech } from "ai";
    import { createOpenAI } from "@ai-sdk/openai";
    import fs from "node:fs";
    
    const openai = createOpenAI({
      baseURL: "https://api.fish.audio/compat/v1",
      apiKey: process.env.FISH_AUDIO_API_KEY,
    });
    
    const { audio } = await generateSpeech({
      model: openai.speech("fish-audio/s2.1-pro"),
      text: "Hello from Fish Audio!",
      voice: "",
      outputFormat: "mp3",
    });
    fs.writeFileSync("hello.mp3", audio.uint8Array);
    

Building a voice agent with Pipecat or LiveKit? Fish Audio has [native integrations](https://docs.fish.audio/developer-guide/integrations/pipecat) for those.

## 

​

Models

Model| What it is  
---|---  
`fish-audio/s2.1-pro`| Production multilingual TTS with voice cloning (recommended)  
`fish-audio/s2.1-pro-free`| Free tier of S2.1 Pro, for prototyping (no latency guarantee)  
`fish-audio/s2-pro`| Expressive TTS for narration and multi-speaker content  
`fish-audio/s1`| Multilingual TTS (deprecated; retires December 31, 2026)  
`fish-audio/transcribe-1`| Multilingual speech-to-text with word-level timestamps  
  
`transcribe-1` needs no language hint. The `language` field in a transcription response echoes what you sent: empty when you sent none, never a detection result (the [ElevenLabs protocol](https://docs.fish.audio/developer-guide/compat/migrate-from-elevenlabs#speech-to-text) echoes `language_code` the same way). For speaker turns, long recordings, and inline emotion cues, use `transcribe-1-pro` on the native [Speech to Text API](https://docs.fish.audio/features/speech-to-text).

## 

​

Voices

The examples above use the model’s default voice. To pick a specific one, pass a **voice ID** : browse the [Voice Library](https://docs.fish.audio/overview/platform) and copy the id of any voice, or make your own with [Voice Cloning](https://docs.fish.audio/features/voice-cloning) or [Voice Design](https://docs.fish.audio/features/voice-design). Vendor preset names (`nova`, `echo`, `Rachel`, …) don’t exist here.
    
    
    voice="9a9cf47702da476aa4629e2506d4a857"      # OpenAI / OpenRouter / Groq
    voice_id="9a9cf47702da476aa4629e2506d4a857"   # ElevenLabs
    

## 

​

Going further

Wondering whether an option you rely on is supported? See [Compatibility](https://docs.fish.audio/developer-guide/compat/capabilities). Starting fresh instead? The [native API](https://docs.fish.audio/api-reference/introduction) and [official SDK](https://docs.fish.audio/developer-guide/sdk-guide/quickstart) expose every Fish Audio capability directly.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/getting-started/migration.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/getting-started/migration)

[Quick Start](https://docs.fish.audio/developer-guide/getting-started/quickstart)[Coding Assistants](https://docs.fish.audio/developer-guide/resources/agent-quickstart)
