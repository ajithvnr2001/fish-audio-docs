---
url: https://docs.fish.audio/features/speech-to-text/realtime/
title: Realtime Speech to Text - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-21T13:05:10.999367+00:00
---

# Realtime Speech to Text - Fish Audio

> Source: https://docs.fish.audio/features/speech-to-text/realtime/

## On this page

  * When to use it
  * Quick start
  * How a session works
  * Smart Turn Detection
    * Eager end of turn
    * Backchannel detection
    * Background awareness
    * Room to think
  * History Aware Transcription
  * Turn detection modes
  * Languages
  * Latency
  * Implementation details
    * Audio
    * Speakers
    * Keys and browsers
    * Limits
    * Pricing
  * Going further



Speech to Text

# Realtime Speech to Text

Copy pageCopy page

Transcribe live audio turn by turn with transcribe-stream-1: turn detection that knows when the user has finished, backchannel and background awareness, and conversation context

Copy pageCopy page

Stream live audio over a WebSocket and get the transcript turn by turn while people speak. `transcribe-stream-1` does more than transcribe: it decides when the user has finished their turn, usually tells the user talking to your app apart from background sound, and notices when a “mm-hm” is only an acknowledgement. This helps your voice agent decide when to answer, when to keep talking and when to stop. Connect to `wss://api.fish.audio/v1/asr/realtime`, send audio as you capture it, and read the events the server sends back.

`transcribe-stream-1` is in preview.

## API reference

Every message, field, error and limit.

## Quickstart

Stream a file or a browser microphone.

## Voice agent guide

Turn-taking, interruptions and backchannels.

## 

​

When to use it

## Voice agents

Know when the user has finished, start replies early, and handle interruptions.

## Live captions

Show live drafts as people speak, then the final text for each turn.

## Voice commands

Act on what the user said as soon as the turn ends, or on button release with push-to-talk.

## Phone calls

Stream 8 kHz call audio as it arrives. Decode μ-law or A-law audio to 16-bit PCM first; the server converts the sample rate.

To transcribe a recording you already have, use [`POST /v1/asr`](https://docs.fish.audio/features/speech-to-text) with `transcribe-1-pro` instead:

| Realtime (`/v1/asr/realtime`)| File (`POST /v1/asr`)  
---|---|---  
Model| `transcribe-stream-1` (Preview)| `transcribe-1-pro`  
Input| Live 16-bit PCM over a WebSocket| A complete audio file (WAV, MP3, Opus, and more)  
Output| Events per turn: drafts, turn signals and the final transcript| One transcript, with optional timestamps and speaker turns  
Turn detection| Yes| No  
Session length| Up to 60 minutes| Recordings up to 60 minutes  
  
The realtime endpoints of the [compatible APIs](https://docs.fish.audio/developer-guide/compat/capabilities) are separate from this endpoint. They use manual commit and have no server-side turn detection.

## 

​

Quick start

The SDKs do not wrap this endpoint; you connect with any WebSocket client and exchange MessagePack messages.

1

Connect

Open `wss://api.fish.audio/v1/asr/realtime` from your server with the header `Authorization: Bearer <API key>`.

2

Configure the session

Send a `config` message with your audio format and options, and wait for `session_started`.

3

Stream audio

Send `audio` messages with 16-bit mono PCM, 80–100 ms each, as you capture it.

4

Read the transcript

Each turn ends with one `committed` message holding its final text. Answer it if `user_turn` is `true`.

5

Finish

Send `audio_done`. The server commits the last turn, sends `session_done` and closes the connection.
    
    
    {
      "type": "config",
      "audio": { "format": "pcm_s16le", "sample_rate": 16000, "channels": 1 },
      "turn_detection": { "mode": "auto", "eager": true },
      "results": { "drafts": true }
    }
    

[Transcribe a live audio stream](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-transcription) has complete, tested clients in Python and Node.js, and a browser microphone page with a server relay.

## 

​

How a session works

Audio is divided into turns. A turn opens when voice activity begins (`speech_start`), usually before the server knows what the sound is: the user speaking, a short acknowledgement, noise or another voice. It ends with exactly one `committed` message, which holds the final transcript and says why the turn ended. In between, you can receive live `draft` text and turn signals that tell you what the turn is. In the default `auto` mode, with `results.drafts` and `turn_detection.eager` turned on as in the example above:
    
    
    The user's turn:
      speech_start → draft … → user_turn_taken → draft … → eager_end_of_turn → committed (user_turn: true)
    
    "Mm-hm" from the user while your agent speaks:
      speech_start → draft … → user_backchannel → draft … → committed (user_turn: false, turn_kind: "backchannel")
    
    Noise, a TV or another voice:
      speech_start → draft … → committed (user_turn: false, turn_kind: "other")
    

  * `draft`: the turn’s text so far. Drafts come in every kind of turn, so a draft does not mean the user is talking.
  * `user_turn_taken`: the server judged that the user is taking their turn.
  * `user_backchannel`: while your agent is speaking (see Backchannel detection), the user only acknowledged; keep talking. If the user goes on to take the turn, `user_turn_taken` follows, and the turn that holds the acknowledgement is the user’s. That can be a new turn, with its own `speech_start`.
  * `eager_end_of_turn`: the turn has probably ended; its text equals the final transcript unless `turn_resumed` follows. Only the user’s turns get it, and not every one does.
  * `committed`: the final transcript. `user_turn` says whether it was the user’s turn, and `turn_kind` what it was otherwise.

So do not stop your agent on `speech_start` or on a `draft`: noise opens turns and gets drafts too. Wait for `user_turn_taken`. In `vad` and `manual` mode there is no `user_turn_taken`: every turn is a user turn, so stop on `speech_start` there (see Turn detection modes).

## 

​

Smart Turn Detection

In the default `auto` mode, the server’s turn detection decides when a turn ends, from what was said and how, not from silence alone.

### 

​

Eager end of turn

With `turn_detection.eager: true`, you receive `eager_end_of_turn` as soon as the turn has probably ended, before the final transcript. Its text is exactly the text `committed` will have, unless `turn_resumed` follows because the user went on. A voice agent can start its LLM on the eager text and save that time.

### 

​

Backchannel detection

Tell the server when your agent is speaking with `agent_speaking`. While it speaks, a short “mm-hm”, “yeah”, “right” or “uh-huh” from the user produces `user_backchannel`: the agent keeps talking. A real interruption produces `user_turn_taken`: the agent stops.

### 

​

Background awareness

Noise, a TV or side conversations usually become non-user turns, committed with `user_turn: false`, so your agent does not answer them.

### 

​

Room to think

Short pauses in the middle of a sentence usually do not end the turn, so people can stop to think. When a speaker stops mid-sentence and does not go on, the turn ends about 2 seconds later. As a further safety net, a user turn with no voice activity for `silence_timeout_ms` (default 5 seconds) always ends.

## 

​

History Aware Transcription

The server uses the conversation to recognize names and follow-ups.

  * **Custom vocabulary:** list names, products and jargon in `context.terms`, up to 100 terms of up to 32 characters. Update the list during the session with `configure`.
  * **What the agent just said:** send each line your agent speaks with `context_add` as an `assistant` item, so the user’s answer is heard in context.
  * **Conversation history:** recent turns of the session are used as context, and speaker labels such as `<|speaker:0|>` stay the same for the whole session.
  * **Prior conversation:** start a session with earlier lines in `context.history`.



## 

​

Turn detection modes

Mode| A turn ends when| Use it for  
---|---|---  
`auto` (default)| Turn detection judges that the user has finished.| Voice agents and conversations.  
`vad`| A fixed silence has passed (`silence_timeout_ms`, default 700 ms).| Simple silence-based endpointing.  
`manual`| You send `finalize`.| Push-to-talk, or your own endpointing.  
  
Eager end of turn, backchannel detection and background awareness are available in `auto` mode, when the session starts in `auto` (the default). In `vad` and `manual` mode, and after a later switch to `auto` from another mode, every turn is a user turn. See [Turn detection modes](https://docs.fish.audio/api-reference/endpoint/websocket/asr-realtime#turn-detection-modes) for details.

## 

​

Languages

Smart Turn Detection, including eager end of turn, backchannel detection and background awareness, works on speech in every language. In some languages, a turn can end a little later after the speaker stops. `draft`, `eager_end_of_turn` and `committed` carry the language of their own text as `language_code` when it can be identified, one of 29 [supported codes](https://docs.fish.audio/api-reference/endpoint/websocket/asr-realtime#language).

## 

​

Latency

Measured on the production service with synthetic speech:

  * The first text, a `draft` (with `results.drafts: true`), arrives about 0.5 seconds after speech starts.
  * `eager_end_of_turn` arrives about 0.6 seconds after the speaker stops.
  * `committed` arrives about 1.1 seconds after the speaker stops.

Your network and how you send audio add to these times. Send audio as you capture it, in 80–100 ms messages.

## 

​

Implementation details

### 

​

Audio

Send 16-bit little-endian PCM, mono, at 8000, 12000, 16000, 22050, 24000, 32000, 44100 or 48000 Hz. The server converts the sample rate, so you never need to resample. Compressed formats such as Opus or MP3 are not accepted on this endpoint.

### 

​

Speakers

Transcripts contain speaker tags such as `<|speaker:0|>`, stable within a session. Strip them, or send `results.diarize: false` for plain text. Whitespace right after a tag can vary, so trim the text after you strip the tags. Transcripts can also contain sound tags such as `[laughter]` or `[pause]`; see [Sound tags](https://docs.fish.audio/api-reference/endpoint/websocket/asr-realtime#sound-tags).

### 

​

Keys and browsers

Your API key travels in a request header. Connect from your server, never from a web page. To transcribe a browser microphone, relay the audio through your server, as shown in the [quickstart](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/realtime-transcription#capture-from-a-browser-microphone).

### 

​

Limits

A session lasts up to 60 minutes and a turn up to 60 seconds. Each open connection counts against the same concurrency limit as your other API requests, from the moment it opens until it closes, even while you send no audio; see [Concurrent request limits](https://docs.fish.audio/developer-guide/models-pricing/pricing-and-rate-limits#concurrent-request-limits). See [Limits](https://docs.fish.audio/api-reference/endpoint/websocket/asr-realtime#limits) for the full list.

### 

​

Pricing

`transcribe-stream-1` costs $0.36 per hour, billed per second of session duration as its own line item, Realtime ASR. See [ASR pricing](https://docs.fish.audio/developer-guide/models-pricing/pricing-and-rate-limits#automatic-speech-recognition-asr-models).

## 

​

Going further

## Build a voice agent

The agent loop: eager replies, interruptions and backchannels.

## Stream speech back

Speak your agent’s replies with streaming text to speech.

## Transcribe files

Recordings up to 60 minutes with `transcribe-1-pro`.

## WebSocket reference

Messages, errors, close codes and limits.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/features/speech-to-text/realtime.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/features/speech-to-text/realtime)

[Overview](https://docs.fish.audio/features/speech-to-text)[Voice Design](https://docs.fish.audio/features/voice-design)
