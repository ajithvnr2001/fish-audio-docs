---
url: https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech-live-with-timestamps/
title: WebSocket TTS with Timestamps - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:19.945421+00:00
---

# WebSocket TTS with Timestamps - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech-live-with-timestamps/

Messages

Start TTS Session
    
    
    {  
      "event": "start",  
      "request": {  
        "text": "",  
        "format": "mp3",  
        "chunk_length": 300,  
        "reference_id": "9a9cf47702da476aa4629e2506d4a857",  
        "latency": "normal"  
      }  
    }

Send Text Chunk
    
    
    {  
      "event": "text",  
      "text": "Hello, this is streaming text. "  
    }

Flush Buffered Text
    
    
    {  
      "event": "flush"  
    }

End TTS Session
    
    
    {  
      "event": "stop"  
    }

Audio Chunk with Timestamps
    
    
    {  
      "event": "audio",  
      "audio": "<binary audio data>",  
      "content": "Hello there.",  
      "alignment": {  
        "segments": [  
          {  
            "text": "Hello",  
            "start": 0,  
            "end": 0.42  
          },  
          {  
            "text": "there.",  
            "start": 0.42,  
            "end": 0.86  
          }  
        ],  
        "audio_duration": 0.86  
      },  
      "chunk_seq": 0,  
      "chunk_audio_offset_sec": 0,  
      "time": 920  
    }

Timestamped Session Complete
    
    
    {  
      "event": "finish",  
      "reason": "stop",  
      "time": 5460  
    }

Request Error
    
    
    {  
      "event": "error",  
      "error": "Concurrency limit exceeded",  
      "max_concurrency": 8  
    }

TTS (v1)

# WebSocket TTS with Timestamps

Copy pageCopy page

Stream text and receive speech with word-level timestamps over WebSocket

Copy pageCopy page

WSS

/

v1

/

tts

/

live

/

with-timestamp

Connect to `wss://api.fish.audio/v1/tts/live/with-timestamp` with a WebSocket client. The endpoint requires a WebSocket upgrade and returns MessagePack binary frames. A normal HTTP GET request does not start synthesis.

## 

​

Before you start

You need a [Fish Audio API key](https://docs.fish.audio/developer-guide/getting-started/api-key) and a WebSocket client that supports custom authentication headers. To run the Python example on this page, install its dependencies:
    
    
    pip install ormsgpack websockets
    

Replace `<token>` in the example with your API key and set `reference_id` to your voice model ID. The `start.request` object accepts the same parameters as the [Text to Speech API](https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech). Send text and receive audio concurrently, then keep reading after sending `stop` until the server sends `finish`.

## 

​

Preserve the final timestamps

Process alignment metadata even when an `audio` event contains empty audio bytes: a trailing event can carry a final alignment correction. Store each non-null `alignment` by `chunk_seq`, replacing its previous snapshot. A null alignment does not erase a snapshot you already received. Add `chunk_audio_offset_sec` to each segment’s `start` and `end` to place it on the session’s audio timeline. The optional `time` field measures elapsed server session time in milliseconds; use the segment timestamps for captions. After `finish`, you can send another `start` on the same socket. Reset your audio buffer and stored alignment snapshots for the new session.

## 

​

Related endpoints

  * [Text to Speech Stream with Timestamps](https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech-stream-with-timestamps): send the full text in one HTTP request and receive audio and timestamps over SSE.
  * [WebSocket TTS Streaming](https://docs.fish.audio/api-reference/endpoint/websocket/tts-live): stream text and audio without timestamps.



Messages

Start TTS Session
    
    
    {  
      "event": "start",  
      "request": {  
        "text": "",  
        "format": "mp3",  
        "chunk_length": 300,  
        "reference_id": "9a9cf47702da476aa4629e2506d4a857",  
        "latency": "normal"  
      }  
    }

Send Text Chunk
    
    
    {  
      "event": "text",  
      "text": "Hello, this is streaming text. "  
    }

Flush Buffered Text
    
    
    {  
      "event": "flush"  
    }

End TTS Session
    
    
    {  
      "event": "stop"  
    }

Audio Chunk with Timestamps
    
    
    {  
      "event": "audio",  
      "audio": "<binary audio data>",  
      "content": "Hello there.",  
      "alignment": {  
        "segments": [  
          {  
            "text": "Hello",  
            "start": 0,  
            "end": 0.42  
          },  
          {  
            "text": "there.",  
            "start": 0.42,  
            "end": 0.86  
          }  
        ],  
        "audio_duration": 0.86  
      },  
      "chunk_seq": 0,  
      "chunk_audio_offset_sec": 0,  
      "time": 920  
    }

Timestamped Session Complete
    
    
    {  
      "event": "finish",  
      "reason": "stop",  
      "time": 5460  
    }

Request Error
    
    
    {  
      "event": "error",  
      "error": "Concurrency limit exceeded",  
      "max_concurrency": 8  
    }

Security Schemes

bearerAuth

type:http

API key authentication using Bearer token.

Get your API key from <https://fish.audio/app/api-keys>

Pass the token in the Authorization header: `Authorization: Bearer YOUR_API_KEY`

Bindings

headers

type:object

hide 1 property

model

type:enum

TTS model to use for this session. If omitted or set to an unrecognized value, the session falls back to `s2.1-pro`. `s1` is deprecated and will be retired on December 31, 2026. After that date, requests that specify `s1` are served by `s2.1-pro`.

Available options: `s1`, `s2-pro`, `s2.1-pro`, `s2.1-pro-free`, `drama-3`

Send

Start TTS Session

type:object

show 2 properties

Initiates a TTS streaming session with configuration.

This must be the first message sent after connecting. It contains all the configuration for voice, audio format, and generation parameters.

The `request` payload uses the same fields as the HTTP TTS API. In WebSocket mode, `request.text` is typically empty in the StartEvent and the actual text is streamed through subsequent TextEvent messages.

For full parameter details, examples, and model-specific guidance, see the HTTP [Text to Speech API](https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech).

Send Text Chunk

type:object

show 2 properties

Sends a chunk of text for synthesis.

You can send multiple TextEvent messages in sequence. The server will buffer and synthesize text according to the chunk_length parameter from StartEvent.

Flush Buffered Text

type:object

show 1 property

Forces immediate synthesis of all buffered text.

Use this when you want audio generated immediately without waiting for more text or for the buffer to fill up. Useful for ensuring low latency in interactive applications.

End TTS Session

type:object

show 1 property

Signals the end of the text stream.

After sending this event, the server will finish synthesizing any remaining buffered text and send a FinishEvent before closing the connection.

Receive

Audio Chunk with Timestamps

type:object

show 7 properties

Contains generated audio bytes and the latest word-level alignment snapshot.

Concatenate every `audio` payload in arrival order to reconstruct the complete audio. Alignment is cumulative for each `chunk_seq`, and segment times are relative to that chunk.

Timestamped Session Complete

type:object

show 4 properties

Signals that the timestamped TTS session has completed. After receiving this event, you can send another StartEvent on the same connection.

Request Error

type:object

show 3 properties

Reports a request-level failure, such as an invalid StartEvent, a missing voice reference, or a concurrency refusal. The socket closes afterwards.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/openapi-v1/text-to-speech-live-with-timestamps.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/openapi-v1/text-to-speech-live-with-timestamps)

[WebSocket TTS Streaming](https://docs.fish.audio/api-reference/endpoint/websocket/tts-live)[Speech to Text](https://docs.fish.audio/api-reference/endpoint/openapi-v1/speech-to-text)
