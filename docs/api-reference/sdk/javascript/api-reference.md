---
url: https://docs.fish.audio/api-reference/sdk/javascript/api-reference/
title: JavaScript SDK Reference - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:23.152812+00:00
---

# JavaScript SDK Reference - Fish Audio

> Source: https://docs.fish.audio/api-reference/sdk/javascript/api-reference/

## On this page

  * Client
  * Text to Speech
    * convert()
    * convertRealtime()
  * Speech to Text
    * convert()
  * Voices
    * search()
    * get()
    * ivc.create()
    * update()
    * delete()
  * User
    * get_api_credit()
    * get_package()
  * Request Classes
    * TTSRequest
    * STTRequest
    * ReferenceAudio
    * Prosody
    * Backends
  * Response Classes
    * STTResponse
    * ASRSegment
    * ModelEntity
    * ModelListResponse
    * APICreditResponse
    * PackageResponse
  * WebSocket Classes
    * RealtimeEvents
  * Event Classes
    * StartEvent
    * TextEvent
    * FlushEvent
    * CloseEvent
  * Exceptions
    * FishAudioError
    * FishAudioTimeoutError



JavaScript SDK

# JavaScript SDK Reference

Copy pageCopy page

Complete reference for Fish Audio JavaScript SDK

Copy pageCopy page

## 

​

Client

Import and initialize the client:
    
    
    import { FishAudioClient } from "fish-audio";
    const fishAudio = new FishAudioClient({ apiKey: process.env.FISH_API_KEY });
    

## 

​

Text to Speech

### 

​

convert()

Generate speech from text.
    
    
    const audio = await fishAudio.textToSpeech.convert({ text: "Hello" });
    

Parameters: `request` (TTSRequest), `model?` (Backends)   
Returns: `Promise<ReadableStream<Uint8Array>>`

### 

​

convertRealtime()

Realtime streaming TTS over WebSocket.
    
    
    async function* textStream() { yield "Hello, "; yield "world!"; }
    const conn = await fishAudio.textToSpeech.convertRealtime({ text: "" }, textStream());
    

Parameters: `request` (TTSRequest with `text: ""`), `textStream` (`AsyncIterable<string>`), `backend?` (Backends)   
Returns: `RealtimeConnection` (`EventEmitter`-like connection) emitting `RealtimeEvents`

## 

​

Speech to Text

### 

​

convert()

Transcribe audio to text.
    
    
    const res = await fishAudio.speechToText.convert(
      { audio: myAudio },
      { headers: { model: "transcribe-1-pro" } }
    );
    console.log(res.text);
    

Parameters: `request` (STTRequest), `requestOptions?` (for example `headers` and `timeoutInSeconds`)   
Returns: `STTResponse` Select the model with the `model` header in `requestOptions.headers`. Without it, the request is served and billed as `transcribe-1`. See [Speech to Text](https://docs.fish.audio/features/speech-to-text).

## 

​

Voices

### 

​

search()

List/search available voice models.
    
    
    const results = await fishAudio.voices.search();
    

Parameters: `request?` (ModelListRequest)   
Returns: `ModelListResponse`

### 

​

get()

Get model details.
    
    
    const model = await fishAudio.voices.get("model_id");
    

Parameters: `voiceId` (string)   
Returns: `ModelEntity`

### 

​

ivc.create()

Create a new voice model from audio samples.
    
    
    const res = await fishAudio.voices.ivc.create({ title, voices: [file], cover_image: file });
    

Parameters: `request` (ModelCreateRequest)   
Returns: `ModelEntity`

### 

​

update()

Update model metadata.
    
    
    await fishAudio.voices.update("model_id", { title: "New Title" });
    

Parameters: `voiceId` (string), `request` (UpdateModelRequest)   
Returns: `UpdateVoiceResponse`

### 

​

delete()

Delete a model.
    
    
    await fishAudio.voices.delete("model_id");
    

Parameters: `voiceId` (string)   
Returns: `DeleteVoiceResponse`

## 

​

User

### 

​

get_api_credit()

Check API credit balance.
    
    
    await fishAudio.user.get_api_credit();
    

Returns: `APICreditResponse`

### 

​

get_package()

Get subscription package details.
    
    
    await fishAudio.user.get_package();
    

Returns: `PackageResponse`

## 

​

Request Classes

### 

​

TTSRequest

Text-to-speech parameters.
    
    
    {
      text: "Hello",
      reference_id: "model_id",
      references: [ { audio: File, text: "sample" } ],
      format: "mp3",
      prosody: { speed: 1.0, volume: 0 },
    }
    

Fields: `text`, `reference_id`, `references`, `format`, `mp3_bitrate`, `opus_bitrate`, `sample_rate`, `prosody`, `latency`, `chunk_length`, `normalize`, `temperature`, `top_p`

### 

​

STTRequest

Speech-to-text parameters.
    
    
    { audio: File, language?: "en", ignore_timestamps?: boolean }
    

Fields: `audio`, `language?`, `ignore_timestamps?`

### 

​

ReferenceAudio

Reference audio for voice cloning.
    
    
    { audio: File, text: "spoken text" }
    

Fields: `audio`, `text`

### 

​

Prosody

Speed and volume control.
    
    
    { speed: 1.2, volume: 5 }
    

Fields: `speed` (0.5–2.0), `volume` (-20 to 20)

### 

​

Backends

The backend model to use.
    
    
    Backends = 's1' | 's2-pro';
    

The API also accepts `s2.1-pro` and `s2.1-pro-free`; the SDK’s `Backends` type has not been updated yet, so pass them with a type assertion (for example `'s2.1-pro' as Backends`) or call the [REST API](https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech) directly.

## 

​

Response Classes

### 

​

STTResponse

Transcription result.
    
    
    response.text      // Complete transcription
    response.duration  // Duration in seconds
    response.segments  // ASRSegment[]
    

### 

​

ASRSegment

Timestamped text segment. Fields: `text` (string), `start` (number, seconds), `end` (number, seconds)

### 

​

ModelEntity

Voice model information. Fields: `_id`, `title`, `description`, `visibility`, `created_at`, `updated_at`, `tags`

### 

​

ModelListResponse

List response for voices. Fields: `items` (ModelEntity[]), `total` (number)

### 

​

APICreditResponse

API credit information. Fields: `_id` (string), `user_id` (string), `credit` (string), `created_at` (string), `updated_at` (string), `has_phone_sha256` (boolean), `has_free_credit?` (boolean)

### 

​

PackageResponse

Subscription package details. Fields: `user_id` (string), `type` (string), `total` (number), `balance` (number), `created_at` (string), `updated_at` (string), `finished_at` (string)

## 

​

WebSocket Classes

### 

​

RealtimeEvents

Events emitted by `convertRealtime` connections.

Event| Meaning  
---|---  
`OPEN`| Connection established  
`AUDIO_CHUNK`| Audio chunk received  
`ERROR`| Error occurred  
`CLOSE`| Connection closed  
  
## 

​

Event Classes

### 

​

StartEvent

Stream start event. Fields: `event` (“start”), `request` (TTSRequest)

### 

​

TextEvent

Text chunk event. Fields: `event` (“text”), `text` (string)

### 

​

FlushEvent

Flush text chunks event. Fields: `event` (“flush”)

### 

​

CloseEvent

Stream close event. Fields: `event` (“stop”)

## 

​

Exceptions

### 

​

FishAudioError

Generic error with status code, body, rawResponse.

### 

​

FishAudioTimeoutError

Connection timeout error.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/sdk/javascript/api-reference.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/sdk/javascript/api-reference)

[Legacy](https://docs.fish.audio/archive/python-sdk-legacy)
