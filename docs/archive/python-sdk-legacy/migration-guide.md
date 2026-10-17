---
url: https://docs.fish.audio/archive/python-sdk-legacy/migration-guide/
title: Migration Guide - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:46.092565+00:00
---

# Migration Guide - Fish Audio

> Source: https://docs.fish.audio/archive/python-sdk-legacy/migration-guide/

## On this page

  * Quick Migration
  * Key Changes at a Glance
  * Text-to-Speech Migration
  * Voice Cloning Migration
  * Speech-to-Text Migration
  * WebSocket Streaming Migration
  * Error Handling Migration
  * Async Support
  * Breaking Changes Summary
  * Common Issues
  * Next Steps
  * Need Help?



# Migration Guide

Copy pageCopy page

Migrate from the legacy Session-based API to the modern client-based Fish Audio Python SDK

Copy pageCopy page

This guide helps you migrate from the legacy `fish_audio_sdk` (Session-based API) to the new `fishaudio` (client-based API) available in `fish-audio-sdk` v1.0+.

## 

​

Quick Migration

1

Uninstall and reinstall the package
    
    
    pip uninstall fish-audio-sdk
    pip install fish-audio-sdk
    

The package name stays the same, but the import changes from `fish_audio_sdk` to `fishaudio`.You can still keep using the `fish_audio_sdk` package if you’d like though. Just be aware that it will not receive any new features or updates.Since this is a versioning jump from `v2025.6.3` to `v1.0.0`, you may need to pin the version explicitly with `fish-audio-sdk==1.0.0`.

2

Update imports
    
    
    # Before
    from fish_audio_sdk import Session, TTSRequest, ASRRequest
    
    # After
    from fishaudio import FishAudio
    from fishaudio.types import TTSConfig, ReferenceAudio
    

3

Replace Session with Client
    
    
    # Before
    session = Session("your_api_key")
    
    # After
    client = FishAudio(api_key="your_api_key")
    # Or use environment variable
    client = FishAudio()  # Reads from FISH_API_KEY
    

4

Update API calls

See the quick reference below for common operations.

## 

​

Key Changes at a Glance

Legacy| New| Notes  
---|---|---  
`Session()`| `FishAudio()`| Client-based architecture  
`session.tts()`| `client.tts.convert()`| Returns complete audio bytes  
`session.asr()`| `client.asr.transcribe()`| Clearer method name  
`session.create_model()`| `client.voices.create()`| ”Model” → “Voice” terminology  
`session.list_models()`| `client.voices.list()`| Resource namespacing  
`TTSRequest(...)`| Direct parameters| No request objects  
`WebSocketSession`| `client.tts.stream_websocket()`| Integrated into client  
`HttpCodeErr`| Specific exceptions| Better error handling  
  
## 

​

Text-to-Speech Migration

Legacy

New
    
    
    from fish_audio_sdk import Session, TTSRequest
    
    session = Session("your_api_key")
    
    # Basic TTS - returns chunks
    audio = b""
    for chunk in session.tts(TTSRequest(text="Hello, world!")):
        audio += chunk
    
    with open("output.mp3", "wb") as f:
        f.write(audio)
    
    
    
    from fishaudio import FishAudio
    from fishaudio.utils import save
    
    client = FishAudio()
    
    # Basic TTS - returns complete audio
    audio = client.tts.convert(text="Hello, world!")
    save(audio, "output.mp3")
    

The new SDK’s `convert()` returns complete audio bytes instead of chunks. Use `stream()` for chunk-by-chunk transfer or `stream_websocket()` for real-time streaming.

## 

​

Voice Cloning Migration

Legacy

New
    
    
    from fish_audio_sdk import Session, TTSRequest, ReferenceAudio
    
    session = Session("your_api_key")
    
    # Instant cloning
    with open("voice.wav", "rb") as f:
        request = TTSRequest(
            text="Cloned voice",
            references=[ReferenceAudio(
                audio=f.read(),
                text="Reference transcript"
            )]
        )
        audio = b"".join(session.tts(request))
    
    # Create voice model
    model = session.create_model(
        title="My Voice",
        voices=[voice_data],
        texts=["Sample text"]
    )
    
    
    
    from fishaudio import FishAudio
    from fishaudio.types import ReferenceAudio
    
    client = FishAudio()
    
    # Instant cloning
    with open("voice.wav", "rb") as f:
        audio = client.tts.convert(
            text="Cloned voice",
            references=[ReferenceAudio(
                audio=f.read(),
                text="Reference transcript"
            )]
        )
    
    # Create voice model
    voice = client.voices.create(
        title="My Voice",
        voices=[voice_data],
        texts=["Sample text"]
    )
    

## 

​

Speech-to-Text Migration

Legacy

New
    
    
    from fish_audio_sdk import Session, ASRRequest
    
    session = Session("your_api_key")
    
    with open("audio.mp3", "rb") as f:
        response = session.asr(ASRRequest(
            audio=f.read(),
            language="en",
            ignore_timestamps=False
        ))
    
    print(response.text)
    
    # Timestamps in SECONDS
    for segment in response.segments:
        print(f"[{segment.start}s - {segment.end}s]")
    
    
    
    from fishaudio import FishAudio
    
    client = FishAudio()
    
    with open("audio.mp3", "rb") as f:
        result = client.asr.transcribe(
            audio=f.read(),
            language="en"
        )
    
    print(result.text)
    
    # Timestamps in SECONDS (unchanged)
    for segment in result.segments:
        print(f"[{segment.start}s - {segment.end}s]")
    

## 

​

WebSocket Streaming Migration

Legacy

New
    
    
    from fish_audio_sdk import WebSocketSession, TTSRequest
    
    ws_session = WebSocketSession("your_api_key")
    
    def text_stream():
        yield "Hello, "
        yield "streaming!"
    
    with ws_session:
        for chunk in ws_session.tts(TTSRequest(text=""), text_stream()):
            # Process audio chunks
            pass
    
    
    
    from fishaudio import FishAudio
    
    client = FishAudio()
    
    def text_chunks():
        yield "Hello, "
        yield "streaming!"
    
    # No empty text required, no context manager needed
    audio_stream = client.tts.stream_websocket(text_chunks())
    for chunk in audio_stream:
        # Process audio chunks
        pass
    

## 

​

Error Handling Migration

Legacy

New
    
    
    from fish_audio_sdk.exceptions import HttpCodeErr
    
    try:
        audio = session.tts(request)
    except HttpCodeErr as e:
        if e.status_code == 429:
            print("Rate limited")
        elif e.status_code == 401:
            print("Auth failed")
    
    
    
    from fishaudio.exceptions import (
        RateLimitError,
        AuthenticationError,
        FishAudioError
    )
    
    try:
        audio = client.tts.convert(text="...")
    except RateLimitError as e:
        print(f"Rate limited. Retry after {e.retry_after}s")
    except AuthenticationError:
        print("Auth failed")
    except FishAudioError as e:
        print(f"General error: {e}")
    

## 

​

Async Support

The new SDK has full async support with `AsyncFishAudio`:
    
    
    import asyncio
    from fishaudio import AsyncFishAudio
    
    async def main():
        client = AsyncFishAudio()
    
        # All methods work with await
        audio = await client.tts.convert(text="Async speech")
        result = await client.asr.transcribe(audio=audio_bytes)
        voices = await client.voices.list()
    
    asyncio.run(main())
    

## 

​

Breaking Changes Summary

TTS now returns complete audio, not chunks

**Before:** Iterator of chunks
    
    
    audio = b""
    for chunk in session.tts(request):
        audio += chunk
    

**After:** Complete audio bytes
    
    
    audio = client.tts.convert(text="...")
    

Use `stream()` or `stream_websocket()` if you need chunks.

No more request objects (TTSRequest, ASRRequest)

**Before:**
    
    
     request = TTSRequest(text="...", format="mp3")
    audio = session.tts(request)
    

**After:**
    
    
     audio = client.tts.convert(text="...", format="mp3")
    

Pass parameters directly to methods.

Model terminology changed to Voice

  * `session.create_model()` → `client.voices.create()`
  * `session.list_models()` → `client.voices.list()`
  * `session.get_model()` → `client.voices.get()`

Plus new methods: `client.voices.update()` and `client.voices.delete()`

## 

​

Common Issues

ModuleNotFoundError: No module named 'fishaudio'

Upgrade the package:
    
    
    pip install --upgrade fish-audio-sdk
    python -c "import fishaudio; print(fishaudio.__version__)"
    

Code expects TTS chunks but gets complete audio

The new `convert()` returns complete audio. Use `stream()` for chunks:
    
    
    audio_stream = client.tts.stream(text="...")
    for chunk in audio_stream:
        process_chunk(chunk)
    

WebSocket requires empty text parameter

Remove the empty text. Just pass your generator:
    
    
    # Before
    ws_session.tts(TTSRequest(text=""), text_stream())
    
    # After
    client.tts.stream_websocket(text_stream())
    

## 

​

Next Steps

## Python SDK Guide

Complete guide for the new SDK

## API Reference

Detailed API documentation

## Text-to-Speech

TTS features and examples

## Voice Cloning

Clone voices and manage models

## 

​

Need Help?

  * [GitHub Repository](https://github.com/fishaudio/fish-audio-python) \- Report issues or request features
  * [Discord Community](https://discord.gg/fishaudio) \- Get help from the community
  * [PyPI Package](https://pypi.org/project/fish-audio-sdk/) \- Package information



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/archive/python-sdk-legacy/migration-guide.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/archive/python-sdk-legacy/migration-guide)
