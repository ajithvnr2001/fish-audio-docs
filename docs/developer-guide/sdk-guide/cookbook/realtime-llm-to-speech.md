---
url: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-llm-to-speech/
title: Realtime: LLM tokens \u2192 speech - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:35.378715+00:00
---

# Realtime: LLM tokens → speech - Fish Audio

> Source: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-llm-to-speech/

## On this page

  * Prerequisites
  * Recipe
  * Force generation at a boundary
  * Related



Realtime Streaming

# Realtime: LLM tokens → speech

Copy pageCopy page

Pipe a streaming LLM response straight into speech over a WebSocket as tokens arrive

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

[`stream_websocket()`](https://docs.fish.audio/api-reference/sdk/python/resources#stream_websocket) takes an iterable of text chunks and yields audio chunks in real time. Feed it your LLM’s token stream and play or forward the audio as it’s produced.

Synchronous

Asynchronous
    
    
    from fishaudio import FishAudio
    from fishaudio.utils import play
    
    client = FishAudio()
    
    def llm_tokens():
        # Replace with your real streaming LLM call
        for token in ["The ", "first ", "move ", "sets ", "everything ", "in ", "motion."]:
            yield token
    
    audio_stream = client.tts.stream_websocket(llm_tokens(), reference_id="<voice-id>")
    play(audio_stream)  # or: for chunk in audio_stream: send_to_client(chunk)
    
    
    
    import asyncio
    from fishaudio import AsyncFishAudio
    
    async def llm_tokens():
        for token in ["The ", "first ", "move ", "sets ", "everything ", "in ", "motion."]:
            yield token
    
    async def main():
        async with AsyncFishAudio() as client:
            audio_stream = client.tts.stream_websocket(llm_tokens())
            with open("out.mp3", "wb") as f:
                async for chunk in audio_stream:
                    f.write(chunk)
    
    asyncio.run(main())
    

## 

​

Force generation at a boundary

By default the engine buffers text until it has enough for natural prosody. Yield a [`FlushEvent`](https://docs.fish.audio/api-reference/sdk/python/types#flushevent-objects) to force synthesis of what’s buffered, useful for turn-taking in a conversation:
    
    
    from fishaudio.types import TextEvent, FlushEvent
    
    def turns():
        yield TextEvent(text="Are you ready?")
        yield FlushEvent()              # speak the question now
        yield TextEvent(text="Let's begin.")
    

The SDK sends the start/stop frames for you.

Errors mid-stream surface as `WebSocketError`. Reconnect with a fresh call rather than retrying on the same socket.

## 

​

Related

  * [Realtime WebSocket guide](https://docs.fish.audio/features/realtime-streaming)
  * [Errors & Retries](https://docs.fish.audio/developer-guide/sdk-guide/python/errors)



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/sdk-guide/cookbook/realtime-llm-to-speech.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/sdk-guide/cookbook/realtime-llm-to-speech)

[One-shot vs persistent cloning: pick the right approach](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/oneshot-vs-persistent-cloning)[Build a voice agent loop: speech in, reply, speech out](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/voice-agent-loop)
