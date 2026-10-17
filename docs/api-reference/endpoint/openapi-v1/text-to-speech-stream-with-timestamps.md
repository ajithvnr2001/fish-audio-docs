---
url: https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech-stream-with-timestamps/
title: Text to Speech Stream with Timestamps - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:21.519655+00:00
---

# Text to Speech Stream with Timestamps - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech-stream-with-timestamps/

Stream With Timestamps

cURL
    
    
    curl --no-buffer --request POST \
      --url https://api.fish.audio/v1/tts/stream/with-timestamp \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --header 'model: s2.1-pro-free' \
      --data '{
        "text": "[happy] I can’t believe it’s been this long. It feels like forever since we last really talked. I’ve missed hearing your voice, your stories, even the little things you used to say. How have you been? I’ve thought about calling you so many times, but I never knew where to start. Seeing you again now makes me realize just how much I’ve missed you. We have so much to catch up on, and I don’t even know which part of my life to tell you about first.",
        "format": "opus",
        "normalize": true,
        "temperature": 0.9,
        "chunk_length": 100,
        "top_p": 0.9,
        "latency": "balanced",
        "sample_rate": 48000,
        "reference_id": "fbe02f8306fc4d3d915e9871722a39d5"
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/tts/stream/with-timestamp"
    
    payload = {
        "text": "<string>",
        "temperature": 0.7,
        "top_p": 0.7,
        "references": [
            {
                "audio": "<string>",
                "text": "<string>"
            }
        ],
        "reference_id": "<string>",
        "prosody": {
            "speed": 1,
            "volume": 0,
            "normalize_loudness": True
        },
        "chunk_length": 300,
        "normalize": True,
        "language": "en",
        "format": "mp3",
        "sample_rate": 123,
        "mp3_bitrate": 128,
        "opus_bitrate": -1000,
        "latency": "normal",
        "max_new_tokens": 1024,
        "repetition_penalty": 1.2,
        "min_chunk_length": 50,
        "condition_on_previous_chunks": True,
        "early_stop_threshold": 1,
        "features": [],
        "pronunciation_dictionary": [
            {
                "id": "<string>",
                "version": "<string>"
            }
        ]
    }
    headers = {
        "Authorization": "Bearer <token>",
        "Content-Type": "application/json"
    }
    
    response = requests.post(url, json=payload, headers=headers)
    
    print(response.text)
    
    
    const options = {
      method: 'POST',
      headers: {Authorization: 'Bearer <token>', 'Content-Type': 'application/json'},
      body: JSON.stringify({
        text: '<string>',
        temperature: 0.7,
        top_p: 0.7,
        references: [{audio: '<string>', text: '<string>'}],
        reference_id: '<string>',
        prosody: {speed: 1, volume: 0, normalize_loudness: true},
        chunk_length: 300,
        normalize: true,
        language: 'en',
        format: 'mp3',
        sample_rate: 123,
        mp3_bitrate: 128,
        opus_bitrate: -1000,
        latency: 'normal',
        max_new_tokens: 1024,
        repetition_penalty: 1.2,
        min_chunk_length: 50,
        condition_on_previous_chunks: true,
        early_stop_threshold: 1,
        features: [],
        pronunciation_dictionary: [{id: '<string>', version: '<string>'}]
      })
    };
    
    fetch('https://api.fish.audio/v1/tts/stream/with-timestamp', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/tts/stream/with-timestamp",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'text' => '<string>',
        'temperature' => 0.7,
        'top_p' => 0.7,
        'references' => [
            [
                    'audio' => '<string>',
                    'text' => '<string>'
            ]
        ],
        'reference_id' => '<string>',
        'prosody' => [
            'speed' => 1,
            'volume' => 0,
            'normalize_loudness' => true
        ],
        'chunk_length' => 300,
        'normalize' => true,
        'language' => 'en',
        'format' => 'mp3',
        'sample_rate' => 123,
        'mp3_bitrate' => 128,
        'opus_bitrate' => -1000,
        'latency' => 'normal',
        'max_new_tokens' => 1024,
        'repetition_penalty' => 1.2,
        'min_chunk_length' => 50,
        'condition_on_previous_chunks' => true,
        'early_stop_threshold' => 1,
        'features' => [
            
        ],
        'pronunciation_dictionary' => [
            [
                    'id' => '<string>',
                    'version' => '<string>'
            ]
        ]
      ]),
      CURLOPT_HTTPHEADER => [
        "Authorization: Bearer <token>",
        "Content-Type: application/json"
      ],
    ]);
    
    $response = curl_exec($curl);
    $err = curl_error($curl);
    
    curl_close($curl);
    
    if ($err) {
      echo "cURL Error #:" . $err;
    } else {
      echo $response;
    }
    
    
    package main
    
    import (
    	"fmt"
    	"strings"
    	"net/http"
    	"io"
    )
    
    func main() {
    
    	url := "https://api.fish.audio/v1/tts/stream/with-timestamp"
    
    	payload := strings.NewReader("{\n  \"text\": \"<string>\",\n  \"temperature\": 0.7,\n  \"top_p\": 0.7,\n  \"references\": [\n    {\n      \"audio\": \"<string>\",\n      \"text\": \"<string>\"\n    }\n  ],\n  \"reference_id\": \"<string>\",\n  \"prosody\": {\n    \"speed\": 1,\n    \"volume\": 0,\n    \"normalize_loudness\": true\n  },\n  \"chunk_length\": 300,\n  \"normalize\": true,\n  \"language\": \"en\",\n  \"format\": \"mp3\",\n  \"sample_rate\": 123,\n  \"mp3_bitrate\": 128,\n  \"opus_bitrate\": -1000,\n  \"latency\": \"normal\",\n  \"max_new_tokens\": 1024,\n  \"repetition_penalty\": 1.2,\n  \"min_chunk_length\": 50,\n  \"condition_on_previous_chunks\": true,\n  \"early_stop_threshold\": 1,\n  \"features\": [],\n  \"pronunciation_dictionary\": [\n    {\n      \"id\": \"<string>\",\n      \"version\": \"<string>\"\n    }\n  ]\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/tts/stream/with-timestamp")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"text\": \"<string>\",\n  \"temperature\": 0.7,\n  \"top_p\": 0.7,\n  \"references\": [\n    {\n      \"audio\": \"<string>\",\n      \"text\": \"<string>\"\n    }\n  ],\n  \"reference_id\": \"<string>\",\n  \"prosody\": {\n    \"speed\": 1,\n    \"volume\": 0,\n    \"normalize_loudness\": true\n  },\n  \"chunk_length\": 300,\n  \"normalize\": true,\n  \"language\": \"en\",\n  \"format\": \"mp3\",\n  \"sample_rate\": 123,\n  \"mp3_bitrate\": 128,\n  \"opus_bitrate\": -1000,\n  \"latency\": \"normal\",\n  \"max_new_tokens\": 1024,\n  \"repetition_penalty\": 1.2,\n  \"min_chunk_length\": 50,\n  \"condition_on_previous_chunks\": true,\n  \"early_stop_threshold\": 1,\n  \"features\": [],\n  \"pronunciation_dictionary\": [\n    {\n      \"id\": \"<string>\",\n      \"version\": \"<string>\"\n    }\n  ]\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/tts/stream/with-timestamp")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"text\": \"<string>\",\n  \"temperature\": 0.7,\n  \"top_p\": 0.7,\n  \"references\": [\n    {\n      \"audio\": \"<string>\",\n      \"text\": \"<string>\"\n    }\n  ],\n  \"reference_id\": \"<string>\",\n  \"prosody\": {\n    \"speed\": 1,\n    \"volume\": 0,\n    \"normalize_loudness\": true\n  },\n  \"chunk_length\": 300,\n  \"normalize\": true,\n  \"language\": \"en\",\n  \"format\": \"mp3\",\n  \"sample_rate\": 123,\n  \"mp3_bitrate\": 128,\n  \"opus_bitrate\": -1000,\n  \"latency\": \"normal\",\n  \"max_new_tokens\": 1024,\n  \"repetition_penalty\": 1.2,\n  \"min_chunk_length\": 50,\n  \"condition_on_previous_chunks\": true,\n  \"early_stop_threshold\": 1,\n  \"features\": [],\n  \"pronunciation_dictionary\": [\n    {\n      \"id\": \"<string>\",\n      \"version\": \"<string>\"\n    }\n  ]\n}"
    
    response = http.request(request)
    puts response.read_body

200

first_event

data: {"audio_base64": "SUQzBAAAAAAA...", "content": "I can’t believe it’s been this long. It feels like forever since we last really talked. I’ve missed hearing your voice, your stories, even the little things you used to say. How have you been? I’ve thought about calling you so many times, but I never knew where to start.", "alignment": {"segments": [{"text": "I", "start": 0.0, "end": 0.16}, {"text": "can't", "start": 0.16, "end": 0.48}, {"text": "believe", "start": 0.48, "end": 0.8}, {"text": "its", "start": 0.8, "end": 1.12}, {"text": "been", "start": 1.2, "end": 1.44}, {"text": "this", "start": 1.44, "end": 1.76}, {"text": "long", "start": 1.76, "end": 2.48}, {"text": "It", "start": 2.56, "end": 2.64}, {"text": "feels", "start": 2.72, "end": 3.04}, {"text": "like", "start": 3.12, "end": 3.28}, {"text": "forever", "start": 3.36, "end": 4.0}, {"text": "since", "start": 4.0, "end": 4.32}, {"text": "we", "start": 4.32, "end": 4.48}, {"text": "last", "start": 4.48, "end": 4.96}, {"text": "really", "start": 4.96, "end": 5.28}, {"text": "talked", "start": 5.28, "end": 5.84}, {"text": "Ive", "start": 6.0, "end": 6.24}, {"text": "missed", "start": 6.24, "end": 6.64}, {"text": "hearing", "start": 6.64, "end": 6.96}, {"text": "your", "start": 6.96, "end": 7.2}, {"text": "voice", "start": 7.2, "end": 7.76}, {"text": "your", "start": 7.76, "end": 7.92}, {"text": "stories", "start": 7.92, "end": 8.48}, {"text": "even", "start": 8.48, "end": 8.72}, {"text": "the", "start": 8.72, "end": 8.8}, {"text": "little", "start": 8.8, "end": 9.2}, {"text": "things", "start": 9.2, "end": 9.52}, {"text": "you", "start": 9.52, "end": 9.68}, {"text": "used", "start": 9.68, "end": 10.0}, {"text": "to", "start": 10.0, "end": 10.08}, {"text": "say", "start": 10.08, "end": 10.64}, {"text": "How", "start": 10.64, "end": 10.96}, {"text": "have", "start": 10.96, "end": 11.12}, {"text": "you", "start": 11.12, "end": 11.36}, {"text": "been", "start": 11.36, "end": 11.92}, {"text": "Ive", "start": 12.0, "end": 12.24}, {"text": "thought", "start": 12.24, "end": 12.48}, {"text": "about", "start": 12.48, "end": 12.8}, {"text": "calling", "start": 12.8, "end": 13.2}, {"text": "you", "start": 13.2, "end": 13.36}, {"text": "so", "start": 13.36, "end": 13.68}, {"text": "many", "start": 13.68, "end": 13.92}, {"text": "times", "start": 13.92, "end": 14.56}, {"text": "but", "start": 14.56, "end": 14.72}, {"text": "I", "start": 14.72, "end": 14.88}, {"text": "never", "start": 14.88, "end": 15.2}, {"text": "knew", "start": 15.2, "end": 15.36}, {"text": "where", "start": 15.36, "end": 15.6}, {"text": "to", "start": 15.6, "end": 15.6}, {"text": "start", "start": 15.68, "end": 16.24}], "audio_duration": 16.24}, "chunk_seq": 0, "chunk_audio_offset_sec": 0.0} 

TTS (v1)

# Text to Speech Stream with Timestamps

Copy pageCopy page

Stream generated speech with timestamp alignment snapshots

Copy pageCopy page

POST

/

v1

/

tts

/

stream

/

with-timestamp

Try it

Stream With Timestamps

cURL
    
    
    curl --no-buffer --request POST \
      --url https://api.fish.audio/v1/tts/stream/with-timestamp \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --header 'model: s2.1-pro-free' \
      --data '{
        "text": "[happy] I can’t believe it’s been this long. It feels like forever since we last really talked. I’ve missed hearing your voice, your stories, even the little things you used to say. How have you been? I’ve thought about calling you so many times, but I never knew where to start. Seeing you again now makes me realize just how much I’ve missed you. We have so much to catch up on, and I don’t even know which part of my life to tell you about first.",
        "format": "opus",
        "normalize": true,
        "temperature": 0.9,
        "chunk_length": 100,
        "top_p": 0.9,
        "latency": "balanced",
        "sample_rate": 48000,
        "reference_id": "fbe02f8306fc4d3d915e9871722a39d5"
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/tts/stream/with-timestamp"
    
    payload = {
        "text": "<string>",
        "temperature": 0.7,
        "top_p": 0.7,
        "references": [
            {
                "audio": "<string>",
                "text": "<string>"
            }
        ],
        "reference_id": "<string>",
        "prosody": {
            "speed": 1,
            "volume": 0,
            "normalize_loudness": True
        },
        "chunk_length": 300,
        "normalize": True,
        "language": "en",
        "format": "mp3",
        "sample_rate": 123,
        "mp3_bitrate": 128,
        "opus_bitrate": -1000,
        "latency": "normal",
        "max_new_tokens": 1024,
        "repetition_penalty": 1.2,
        "min_chunk_length": 50,
        "condition_on_previous_chunks": True,
        "early_stop_threshold": 1,
        "features": [],
        "pronunciation_dictionary": [
            {
                "id": "<string>",
                "version": "<string>"
            }
        ]
    }
    headers = {
        "Authorization": "Bearer <token>",
        "Content-Type": "application/json"
    }
    
    response = requests.post(url, json=payload, headers=headers)
    
    print(response.text)
    
    
    const options = {
      method: 'POST',
      headers: {Authorization: 'Bearer <token>', 'Content-Type': 'application/json'},
      body: JSON.stringify({
        text: '<string>',
        temperature: 0.7,
        top_p: 0.7,
        references: [{audio: '<string>', text: '<string>'}],
        reference_id: '<string>',
        prosody: {speed: 1, volume: 0, normalize_loudness: true},
        chunk_length: 300,
        normalize: true,
        language: 'en',
        format: 'mp3',
        sample_rate: 123,
        mp3_bitrate: 128,
        opus_bitrate: -1000,
        latency: 'normal',
        max_new_tokens: 1024,
        repetition_penalty: 1.2,
        min_chunk_length: 50,
        condition_on_previous_chunks: true,
        early_stop_threshold: 1,
        features: [],
        pronunciation_dictionary: [{id: '<string>', version: '<string>'}]
      })
    };
    
    fetch('https://api.fish.audio/v1/tts/stream/with-timestamp', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/tts/stream/with-timestamp",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'text' => '<string>',
        'temperature' => 0.7,
        'top_p' => 0.7,
        'references' => [
            [
                    'audio' => '<string>',
                    'text' => '<string>'
            ]
        ],
        'reference_id' => '<string>',
        'prosody' => [
            'speed' => 1,
            'volume' => 0,
            'normalize_loudness' => true
        ],
        'chunk_length' => 300,
        'normalize' => true,
        'language' => 'en',
        'format' => 'mp3',
        'sample_rate' => 123,
        'mp3_bitrate' => 128,
        'opus_bitrate' => -1000,
        'latency' => 'normal',
        'max_new_tokens' => 1024,
        'repetition_penalty' => 1.2,
        'min_chunk_length' => 50,
        'condition_on_previous_chunks' => true,
        'early_stop_threshold' => 1,
        'features' => [
            
        ],
        'pronunciation_dictionary' => [
            [
                    'id' => '<string>',
                    'version' => '<string>'
            ]
        ]
      ]),
      CURLOPT_HTTPHEADER => [
        "Authorization: Bearer <token>",
        "Content-Type: application/json"
      ],
    ]);
    
    $response = curl_exec($curl);
    $err = curl_error($curl);
    
    curl_close($curl);
    
    if ($err) {
      echo "cURL Error #:" . $err;
    } else {
      echo $response;
    }
    
    
    package main
    
    import (
    	"fmt"
    	"strings"
    	"net/http"
    	"io"
    )
    
    func main() {
    
    	url := "https://api.fish.audio/v1/tts/stream/with-timestamp"
    
    	payload := strings.NewReader("{\n  \"text\": \"<string>\",\n  \"temperature\": 0.7,\n  \"top_p\": 0.7,\n  \"references\": [\n    {\n      \"audio\": \"<string>\",\n      \"text\": \"<string>\"\n    }\n  ],\n  \"reference_id\": \"<string>\",\n  \"prosody\": {\n    \"speed\": 1,\n    \"volume\": 0,\n    \"normalize_loudness\": true\n  },\n  \"chunk_length\": 300,\n  \"normalize\": true,\n  \"language\": \"en\",\n  \"format\": \"mp3\",\n  \"sample_rate\": 123,\n  \"mp3_bitrate\": 128,\n  \"opus_bitrate\": -1000,\n  \"latency\": \"normal\",\n  \"max_new_tokens\": 1024,\n  \"repetition_penalty\": 1.2,\n  \"min_chunk_length\": 50,\n  \"condition_on_previous_chunks\": true,\n  \"early_stop_threshold\": 1,\n  \"features\": [],\n  \"pronunciation_dictionary\": [\n    {\n      \"id\": \"<string>\",\n      \"version\": \"<string>\"\n    }\n  ]\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/tts/stream/with-timestamp")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"text\": \"<string>\",\n  \"temperature\": 0.7,\n  \"top_p\": 0.7,\n  \"references\": [\n    {\n      \"audio\": \"<string>\",\n      \"text\": \"<string>\"\n    }\n  ],\n  \"reference_id\": \"<string>\",\n  \"prosody\": {\n    \"speed\": 1,\n    \"volume\": 0,\n    \"normalize_loudness\": true\n  },\n  \"chunk_length\": 300,\n  \"normalize\": true,\n  \"language\": \"en\",\n  \"format\": \"mp3\",\n  \"sample_rate\": 123,\n  \"mp3_bitrate\": 128,\n  \"opus_bitrate\": -1000,\n  \"latency\": \"normal\",\n  \"max_new_tokens\": 1024,\n  \"repetition_penalty\": 1.2,\n  \"min_chunk_length\": 50,\n  \"condition_on_previous_chunks\": true,\n  \"early_stop_threshold\": 1,\n  \"features\": [],\n  \"pronunciation_dictionary\": [\n    {\n      \"id\": \"<string>\",\n      \"version\": \"<string>\"\n    }\n  ]\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/tts/stream/with-timestamp")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"text\": \"<string>\",\n  \"temperature\": 0.7,\n  \"top_p\": 0.7,\n  \"references\": [\n    {\n      \"audio\": \"<string>\",\n      \"text\": \"<string>\"\n    }\n  ],\n  \"reference_id\": \"<string>\",\n  \"prosody\": {\n    \"speed\": 1,\n    \"volume\": 0,\n    \"normalize_loudness\": true\n  },\n  \"chunk_length\": 300,\n  \"normalize\": true,\n  \"language\": \"en\",\n  \"format\": \"mp3\",\n  \"sample_rate\": 123,\n  \"mp3_bitrate\": 128,\n  \"opus_bitrate\": -1000,\n  \"latency\": \"normal\",\n  \"max_new_tokens\": 1024,\n  \"repetition_penalty\": 1.2,\n  \"min_chunk_length\": 50,\n  \"condition_on_previous_chunks\": true,\n  \"early_stop_threshold\": 1,\n  \"features\": [],\n  \"pronunciation_dictionary\": [\n    {\n      \"id\": \"<string>\",\n      \"version\": \"<string>\"\n    }\n  ]\n}"
    
    response = http.request(request)
    puts response.read_body

200

first_event

data: {"audio_base64": "SUQzBAAAAAAA...", "content": "I can’t believe it’s been this long. It feels like forever since we last really talked. I’ve missed hearing your voice, your stories, even the little things you used to say. How have you been? I’ve thought about calling you so many times, but I never knew where to start.", "alignment": {"segments": [{"text": "I", "start": 0.0, "end": 0.16}, {"text": "can't", "start": 0.16, "end": 0.48}, {"text": "believe", "start": 0.48, "end": 0.8}, {"text": "its", "start": 0.8, "end": 1.12}, {"text": "been", "start": 1.2, "end": 1.44}, {"text": "this", "start": 1.44, "end": 1.76}, {"text": "long", "start": 1.76, "end": 2.48}, {"text": "It", "start": 2.56, "end": 2.64}, {"text": "feels", "start": 2.72, "end": 3.04}, {"text": "like", "start": 3.12, "end": 3.28}, {"text": "forever", "start": 3.36, "end": 4.0}, {"text": "since", "start": 4.0, "end": 4.32}, {"text": "we", "start": 4.32, "end": 4.48}, {"text": "last", "start": 4.48, "end": 4.96}, {"text": "really", "start": 4.96, "end": 5.28}, {"text": "talked", "start": 5.28, "end": 5.84}, {"text": "Ive", "start": 6.0, "end": 6.24}, {"text": "missed", "start": 6.24, "end": 6.64}, {"text": "hearing", "start": 6.64, "end": 6.96}, {"text": "your", "start": 6.96, "end": 7.2}, {"text": "voice", "start": 7.2, "end": 7.76}, {"text": "your", "start": 7.76, "end": 7.92}, {"text": "stories", "start": 7.92, "end": 8.48}, {"text": "even", "start": 8.48, "end": 8.72}, {"text": "the", "start": 8.72, "end": 8.8}, {"text": "little", "start": 8.8, "end": 9.2}, {"text": "things", "start": 9.2, "end": 9.52}, {"text": "you", "start": 9.52, "end": 9.68}, {"text": "used", "start": 9.68, "end": 10.0}, {"text": "to", "start": 10.0, "end": 10.08}, {"text": "say", "start": 10.08, "end": 10.64}, {"text": "How", "start": 10.64, "end": 10.96}, {"text": "have", "start": 10.96, "end": 11.12}, {"text": "you", "start": 11.12, "end": 11.36}, {"text": "been", "start": 11.36, "end": 11.92}, {"text": "Ive", "start": 12.0, "end": 12.24}, {"text": "thought", "start": 12.24, "end": 12.48}, {"text": "about", "start": 12.48, "end": 12.8}, {"text": "calling", "start": 12.8, "end": 13.2}, {"text": "you", "start": 13.2, "end": 13.36}, {"text": "so", "start": 13.36, "end": 13.68}, {"text": "many", "start": 13.68, "end": 13.92}, {"text": "times", "start": 13.92, "end": 14.56}, {"text": "but", "start": 14.56, "end": 14.72}, {"text": "I", "start": 14.72, "end": 14.88}, {"text": "never", "start": 14.88, "end": 15.2}, {"text": "knew", "start": 15.2, "end": 15.36}, {"text": "where", "start": 15.36, "end": 15.6}, {"text": "to", "start": 15.6, "end": 15.6}, {"text": "start", "start": 15.68, "end": 16.24}], "audio_duration": 16.24}, "chunk_seq": 0, "chunk_audio_offset_sec": 0.0} 

This endpoint returns `text/event-stream`. Each SSE `message` event contains one JSON payload with a base64-encoded audio chunk.

Use this endpoint when you need both progressive audio delivery and text-to-audio alignment data, such as karaoke-style highlighting, word or phrase progress indicators, captions synchronized to generated speech, or timeline editing.

## 

​

How the Stream Works

The response is a Server-Sent Events stream. Every event includes:

Field| Type| Description  
---|---|---  
`audio_base64`| `string`| One base64-encoded audio chunk. Concatenate all chunks in arrival order to reconstruct the complete audio.  
`content`| `string`| Text content described by this event’s latest alignment snapshot. Long input can be split into multiple content chunks.  
`alignment`| `object | null`| Latest cumulative timestamp snapshot for `chunk_seq`. When present, replace the previous snapshot for that `chunk_seq`; do not append segments.  
`chunk_seq`| `integer`| Sequence number of the text chunk described by `alignment`. Bucket alignment snapshots by this value.  
`chunk_audio_offset_sec`| `number`| Absolute start time of this text chunk within the full audio, in seconds. Add this to segment-local `start` and `end` values for a global audio timeline.  
  
`audio_base64` is the transport stream. `alignment` is a metadata snapshot for `chunk_seq`. They are delivered together in the same SSE event, but the alignment is not a per-audio-packet delta. When `latency` is set to `balanced`, long input can be split into several text chunks. A chunk may produce multiple non-null alignment snapshots as more audio is rendered. Each newer snapshot supersedes the previous snapshot for the same `chunk_seq`.

Store alignments in a map keyed by `chunk_seq`. On every non-null `alignment`, replace the stored value for that key. Do not collect every non-null alignment as a separate final result.

## 

​

Alignment Shape

Each non-null `alignment` contains the current cumulative timing segments for a single text chunk:
    
    
    {
      "audio_base64": "SUQzBAAAAAAA...",
      "content": "Hello world",
      "chunk_seq": 0,
      "chunk_audio_offset_sec": 0.0,
      "alignment": {
        "audio_duration": 0.86,
        "segments": [
          {
            "text": "Hello",
            "start": 0,
            "end": 0.42
          },
          {
            "text": "world",
            "start": 0.42,
            "end": 0.86
          }
        ]
      }
    }
    

`start` and `end` are measured in seconds from the start of that text chunk’s generated audio. Add `chunk_audio_offset_sec` to get timestamps on the complete audio timeline. `alignment` can be `null` before the first snapshot is available or when alignment is unavailable. After a snapshot exists, later audio events may repeat the latest snapshot so clients can continue using a simple latest-wins update model.

## 

​

Minimal Request
    
    
    curl --no-buffer --request POST \
      --url https://api.fish.audio/v1/tts/stream/with-timestamp \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --header 'model: s2-pro' \
      --data '{
        "text": "Hello! Welcome to Fish Audio.",
        "reference_id": "model-id",
        "format": "opus",
        "latency": "balanced"
      }'
    

## 

​

Parsing the Stream

The stream payload uses standard SSE framing. Parse each `data:` line as JSON, append every decoded `audio_base64` chunk to your audio buffer, and replace the latest alignment snapshot for `chunk_seq` whenever `alignment` is non-null.

  * Python

  * Node.js



    
    
    import base64
    import json
    import requests
    
    response = requests.post(
        "https://api.fish.audio/v1/tts/stream/with-timestamp",
        headers={
            "Authorization": "Bearer <token>",
            "Content-Type": "application/json",
            "model": "s2-pro",
        },
        json={
            "text": "Hello! Welcome to Fish Audio.",
            "reference_id": "model-id",
            "format": "opus",
            "latency": "balanced",
        },
        stream=True,
    )
    
    audio_chunks = []
    alignment_by_chunk = {}
    
    for line in response.iter_lines(decode_unicode=True):
        if not line or not line.startswith("data: "):
            continue
    
        event = json.loads(line.removeprefix("data: "))
        audio_chunks.append(base64.b64decode(event["audio_base64"]))
    
        if event["alignment"] is not None:
            alignment_by_chunk[event["chunk_seq"]] = {
                "content": event["content"],
                "offset": event["chunk_audio_offset_sec"],
                "alignment": event["alignment"],
            }
    
    audio = b"".join(audio_chunks)
    
    
    
    const response = await fetch(
      "https://api.fish.audio/v1/tts/stream/with-timestamp",
      {
        method: "POST",
        headers: {
          Authorization: "Bearer <token>",
          "Content-Type": "application/json",
          model: "s2-pro",
        },
        body: JSON.stringify({
          text: "Hello! Welcome to Fish Audio.",
          reference_id: "model-id",
          format: "opus",
          latency: "balanced",
        }),
      }
    );
    
    const audioChunks = [];
    const alignmentByChunk = new Map();
    const decoder = new TextDecoder();
    let buffer = "";
    
    for await (const chunk of response.body) {
      buffer += decoder.decode(chunk, { stream: true });
      const events = buffer.split("\n\n");
      buffer = events.pop() ?? "";
    
      for (const eventText of events) {
        const dataLine = eventText
          .split("\n")
          .find((line) => line.startsWith("data: "));
    
        if (!dataLine) continue;
    
        const event = JSON.parse(dataLine.slice(6));
        audioChunks.push(Buffer.from(event.audio_base64, "base64"));
    
        if (event.alignment !== null) {
          alignmentByChunk.set(event.chunk_seq, {
            content: event.content,
            offset: event.chunk_audio_offset_sec,
            alignment: event.alignment,
          });
        }
      }
    }
    
    const audio = Buffer.concat(audioChunks);
    

## 

​

Handling Split Content Chunks

Long input can produce multiple text chunks. Treat audio and alignment as two related streams:

  1. Append every decoded `audio_base64` chunk in event order. Do this even when `alignment` is `null`.
  2. For non-null `alignment`, replace the stored snapshot for `chunk_seq`.
  3. Convert each snapshot’s local segment times into global times by adding `chunk_audio_offset_sec`.



`audio_base64` chunks are transport chunks, not sentence or word boundaries. Do not try to align each audio chunk individually. Use `alignment.segments` plus `chunk_audio_offset_sec` for text timing.

For example, if an event has `chunk_audio_offset_sec: 16.24`, add `16.24` seconds to every segment in that event’s `alignment` before rendering it on the complete audio timeline.

  * Python

  * Node.js



    
    
    def build_global_timeline(alignment_by_chunk):
        timeline = []
    
        for chunk_seq, item in sorted(alignment_by_chunk.items()):
            offset_seconds = item["offset"]
            alignment = item["alignment"]
    
            for segment in alignment["segments"]:
                timeline.append({
                    "text": segment["text"],
                    "start": segment["start"] + offset_seconds,
                    "end": segment["end"] + offset_seconds,
                    "chunk_seq": chunk_seq,
                })
    
        return timeline
    
    
    
    function buildGlobalTimeline(alignmentByChunk) {
      const timeline = [];
    
      for (const [chunkSeq, item] of [...alignmentByChunk.entries()].sort(
        ([a], [b]) => a - b
      )) {
        for (const segment of item.alignment.segments) {
          timeline.push({
            text: segment.text,
            start: segment.start + item.offset,
            end: segment.end + item.offset,
            chunk_seq: chunkSeq,
          });
        }
      }
    
      return timeline;
    }
    

## 

​

Format Guidance

For timestamped streaming, we recommend `opus` with the default 48 kHz sample rate when your client supports it. Opus is designed for streaming and gives the best balance of quality, latency, and bandwidth for this endpoint. `wav` and `pcm` avoid lossy codec artifacts and are straightforward to align, but they produce much larger payloads. Use them when you need uncompressed audio, direct sample-level processing, or a playback pipeline that already expects raw audio.

Use `mp3` only when broad playback compatibility is more important than the cleanest streaming boundaries. MP3 encoding uses overlapping audio windows, so its encoded chunks may not line up as neatly with timestamp snapshot updates as Opus.

This endpoint accepts the same TTS request fields as the [Text to Speech API](https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech), including `reference_id`, `references`, `prosody`, `temperature`, `top_p`, `chunk_length`, `format`, and `latency`.

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

Request body for streaming text-to-speech synthesis with timestamp alignment. The request fields match the standard TTS endpoint, but the response is delivered as a Server-Sent Events stream. Each SSE payload includes an audio chunk and, when available, the latest cumulative alignment snapshot for a `chunk_seq`. Clients should concatenate `audio_base64` chunks in arrival order and replace the stored alignment for each `chunk_seq` whenever a newer snapshot is received.

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

text/event-stream

Server-Sent Events stream. Each `message` event contains a JSON payload with one base64 audio chunk. Concatenate every `audio_base64` chunk in arrival order to reconstruct the complete audio. `alignment` is the latest cumulative timestamp snapshot for `chunk_seq`; clients should replace the previous snapshot for that chunk instead of appending segments. `chunk_audio_offset_sec` can be added to segment times to derive absolute timestamps in the full audio.

One Server-Sent Events message payload for streaming TTS with timestamps. Each event contains one audio chunk. Concatenate all `audio_base64` chunks in arrival order to reconstruct the complete audio. `alignment` is the latest cumulative timestamp snapshot for the reported `chunk_seq`; clients should replace the previous snapshot for that chunk instead of appending segments.

​

audio_base64

string

required

Base64 encoded audio chunk. Concatenate every chunk in event order to reconstruct the full audio.

​

content

string

required

Text content described by this event's latest alignment snapshot. Long input may be split into multiple content chunks in one stream.

​

alignment

TTSTimestampAlignment · object | null

required

Latest cumulative timestamp snapshot for `chunk_seq`. When present, replace the previous alignment for the same `chunk_seq`; do not append segments. Null means no alignment snapshot has been produced yet or alignment is unavailable.

Show child attributes

​

chunk_seq

integer

required

Sequence number of the text chunk described by `alignment`. Clients should bucket alignment snapshots by this value.

Required range: `x >= 0`

​

chunk_audio_offset_sec

number

required

Absolute start time of this text chunk within the full audio, in seconds.

Required range: `x >= 0`

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/openapi-v1/text-to-speech-stream-with-timestamps.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/openapi-v1/text-to-speech-stream-with-timestamps)

[Text to Speech](https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech)[WebSocket TTS Streaming](https://docs.fish.audio/api-reference/endpoint/websocket/tts-live)
