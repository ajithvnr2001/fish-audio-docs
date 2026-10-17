---
url: https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech/
title: Text to Speech - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:20.840749+00:00
---

# Text to Speech - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech/

cURL

Single Speaker
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/tts \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --header 'model: s2.1-pro-free' \
      --data '{
        "text": "Hello! Welcome to Fish Audio.",
        "reference_id": "model-id",
        "temperature": 0.7,
        "top_p": 0.7,
        "prosody": {
          "speed": 1,
          "volume": 0,
          "normalize_loudness": true
        },
        "chunk_length": 300,
        "normalize": true,
        "format": "mp3",
        "sample_rate": 44100,
        "mp3_bitrate": 128,
        "latency": "normal",
        "max_new_tokens": 1024,
        "repetition_penalty": 1.2,
        "min_chunk_length": 50,
        "condition_on_previous_chunks": true,
        "early_stop_threshold": 1
      }'

401

402

503
    
    
    {
      "status": 123,
      "message": "<string>",
      "reason": "<string>"
    }
    
    
    {
      "status": 123,
      "message": "<string>",
      "reason": "<string>"
    }
    
    
    {
      "status": 123,
      "message": "<string>",
      "reason": "<string>"
    }

TTS (v1)

# Text to Speech

Copy pageCopy page

Convert text to speech

Copy pageCopy page

POST

/

v1

/

tts

Try it

cURL

Single Speaker
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/tts \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --header 'model: s2.1-pro-free' \
      --data '{
        "text": "Hello! Welcome to Fish Audio.",
        "reference_id": "model-id",
        "temperature": 0.7,
        "top_p": 0.7,
        "prosody": {
          "speed": 1,
          "volume": 0,
          "normalize_loudness": true
        },
        "chunk_length": 300,
        "normalize": true,
        "format": "mp3",
        "sample_rate": 44100,
        "mp3_bitrate": 128,
        "latency": "normal",
        "max_new_tokens": 1024,
        "repetition_penalty": 1.2,
        "min_chunk_length": 50,
        "condition_on_previous_chunks": true,
        "early_stop_threshold": 1
      }'

401

402

503
    
    
    {
      "status": 123,
      "message": "<string>",
      "reason": "<string>"
    }
    
    
    {
      "status": 123,
      "message": "<string>",
      "reason": "<string>"
    }
    
    
    {
      "status": 123,
      "message": "<string>",
      "reason": "<string>"
    }

This endpoint only accepts `application/json` and `application/msgpack`.For best results, upload reference audio using the [create model](https://docs.fish.audio/api-reference/endpoint/model/create-model) before using this one. This improves speech quality and reduces latency.To upload audio clips directly, without pre-uploading, serialize the request body with MessagePack as per the [instructions](https://docs.fish.audio/features/text-to-speech#direct-api-messagepack).

Audio formats supported:

  * WAV / PCM 
    * Sample Rate: 8kHz, 16kHz, 24kHz, 32kHz, 44.1kHz
    * Default Sample Rate: 44.1kHz
    * 16-bit, mono
  * MP3 
    * Sample Rate: 32kHz, 44.1kHz
    * Default Sample Rate: 44.1kHz
    * mono
    * Bitrate: 64kbps, 128kbps (default), 192kbps
  * Opus 
    * Sample Rate: 48kHz
    * Default Sample Rate: 48kHz
    * mono
    * Bitrate: -1000 (auto), 24kbps, 32kbps (default), 48kbps, 64kbps



#### Authorizations

​

Authorization

string

header

required

Bearer authentication header of the form `Bearer <token>`, where `<token>` is your auth token.

#### Headers

​

model

enum<string>

default:s2.1-pro

Specify which TTS model to use. Use `s2.1-pro-free` for the free developer tier. If omitted or set to an unrecognized value, the request falls back to `s2.1-pro`.

Available options: 

`s1`, 

`s2-pro`, 

`s2.1-pro`, 

`s2.1-pro-free`, 

`drama-3`

#### Body

application/jsonapplication/msgpackapplication/jsonapplication/msgpack

Request body for text-to-speech synthesis. Supports single-speaker synthesis on all compatible TTS models. Multi-speaker dialogue synthesis is available with the S2 family (`s2-pro`, `s2.1-pro`, `s2.1-pro-free`) and `drama-3`, not `s1`.

## Single Speaker

Provide either `reference_id` (string) pointing to a voice model, or `references` (array of ReferenceAudio) for zero-shot cloning.

## Multiple Speakers (Dialogue — S2 family and `drama-3`)

For multi-speaker synthesis, provide:

  * `reference_id`: array of voice model IDs, e.g., ["speaker-0-id", "speaker-1-id"]
  * `text`: use speaker tags `<|speaker:0|>`, `<|speaker:1|>`, etc. to indicate speaker changes, e.g., "<|speaker:0|>Hello!<|speaker:1|>Hi there!"



Alternatively, for zero-shot multi-speaker:

  * `references`: 2D array where each inner array contains references for one speaker
  * `reference_id`: array of identifiers (can be arbitrary strings for zero-shot)



## Example (Multi-Speaker with Model IDs)
    
    
    {  
      "text": "<|speaker:0|>Good morning!<|speaker:1|>Good morning! How are you?<|speaker:0|>I'm great, thanks!",  
      "reference_id": ["model-id-alice", "model-id-bob"]  
    }

​

text

string

required

Text to convert to speech.

​

temperature

number

default:0.7

Controls expressiveness. Higher is more varied, lower is more consistent.

Required range: `0 <= x <= 1`

​

top_p

number

default:0.7

Controls diversity via nucleus sampling.

Required range: `0 <= x <= 1`

​

references

ReferenceAudio · object[]ReferenceAudio · object[][]ReferenceAudio · object[]ReferenceAudio · object[][]

Single speaker: array of reference audio samples

Show child attributes

​

reference_id

stringstring[]stringstring[]

Single speaker: voice model ID string

​

prosody

ProsodyControl · object | null

Speed and volume adjustments for the output.

Show child attributes

​

chunk_length

integer

default:300

Text segment size for processing.

Required range: `100 <= x <= 300`

​

normalize

boolean

default:true

Rewrites numbers, dates, units and symbols as spoken words before synthesis, improving stability. Uses `language` when it is set and otherwise detects the language of each text chunk.

​

language

string | null

BCP-47 language tag of the text, for example `en`, `es-MX` or `zh-CN`. Case-insensitive, and `_` is read as `-`. Used only by text normalization (how numbers, dates, units and symbols are spelled out before synthesis) and by word-timestamp alignment. It is not passed to the speech model and does not change the voice, accent or audio quality; a wrong tag only changes how those tokens are spelled out. Omit it, or send `auto` or an empty string, to detect the language per chunk. A tag without dedicated normalization rules skips normalization instead of failing. Without a region, Spanish follows Spain conventions; send `es-MX` for Mexican readings. When `normalize` is false it only affects word timestamps. For text that mixes languages, leave it unset.

Maximum string length: `35`

Pattern: `^[A-Za-z0-9_-]*$`

Example:

`"en"`

​

format

enum<string>

default:mp3

Output audio format.

Available options: 

`wav`, 

`pcm`, 

`mp3`, 

`opus`

​

sample_rate

integer | null

Audio sample rate in Hz. When null, uses the format's default (44100 Hz for most formats, 48000 Hz for opus).

​

mp3_bitrate

enum<integer>

default:128

MP3 bitrate in kbps. Only applies when format is mp3.

Available options: 

`64`, 

`128`, 

`192`

​

opus_bitrate

enum<integer>

default:-1000

Opus bitrate in bps. -1000 for automatic. Only applies when format is opus.

Available options: 

`-1000`, 

`24000`, 

`32000`, 

`48000`, 

`64000`

​

latency

enum<string>

default:normal

Latency-quality trade-off. normal: best quality, balanced: reduced latency, low: lowest latency.

Available options: 

`low`, 

`normal`, 

`balanced`

​

max_new_tokens

integer

default:1024

Maximum audio tokens to generate per text chunk.

​

repetition_penalty

number

default:1.2

Penalty for repeating audio patterns. Values above 1.0 reduce repetition.

​

min_chunk_length

integer

default:50

Minimum characters before splitting into a new chunk.

Required range: `0 <= x <= 100`

​

condition_on_previous_chunks

boolean

default:true

Use previous audio as context for voice consistency.

​

early_stop_threshold

number

default:1

Early stopping threshold for batch processing.

Required range: `0 <= x <= 1`

​

features

string[]

Optional request-scoped TTS feature flags forwarded verbatim to the inference backend. Use ["quality-guard"] to enable the quality guard for this synthesis request. Feature availability is determined by the inference backend.

​

pronunciation_dictionary

PronunciationDictionaryRef · object

Reference to a server-managed pronunciation dictionary. The server resolves contents via the platform pronunciation-dictionaries API and forwards the full merged dictionary to the inference engine, which performs the substitution.

  * PronunciationDictionaryRef · object[]

  * PronunciationDictionaryInline · object[]




Show child attributes

#### Response

200

Request fulfilled, document follows

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/openapi-v1/text-to-speech.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/openapi-v1/text-to-speech)

[Update Model](https://docs.fish.audio/api-reference/endpoint/model/update-model)[Text to Speech Stream with Timestamps](https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech-stream-with-timestamps)
