---
url: https://docs.fish.audio/api-reference/endpoint/model/create-model/
title: Create Model - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:18.041832+00:00
---

# Create Model - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/model/create-model/

Create Model for Users via API

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/model \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "type": "tts",
      "title": "<string>",
      "train_mode": "fast",
      "voices": [
        "<string>"
      ],
      "visibility": "private",
      "description": "<string>",
      "cover_image": "<string>",
      "texts": [
        "<string>"
      ],
      "voice_design_signatures": [
        "<string>"
      ],
      "tags": [
        "<string>"
      ],
      "enhance_audio_quality": true,
      "generate_sample": false
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/model"
    
    payload = {
        "type": "tts",
        "title": "<string>",
        "train_mode": "fast",
        "voices": ["<string>"],
        "visibility": "private",
        "description": "<string>",
        "cover_image": "<string>",
        "texts": ["<string>"],
        "voice_design_signatures": ["<string>"],
        "tags": ["<string>"],
        "enhance_audio_quality": True,
        "generate_sample": False
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
        type: 'tts',
        title: '<string>',
        train_mode: 'fast',
        voices: ['<string>'],
        visibility: 'private',
        description: '<string>',
        cover_image: '<string>',
        texts: ['<string>'],
        voice_design_signatures: ['<string>'],
        tags: ['<string>'],
        enhance_audio_quality: true,
        generate_sample: false
      })
    };
    
    fetch('https://api.fish.audio/model', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/model",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'type' => 'tts',
        'title' => '<string>',
        'train_mode' => 'fast',
        'voices' => [
            '<string>'
        ],
        'visibility' => 'private',
        'description' => '<string>',
        'cover_image' => '<string>',
        'texts' => [
            '<string>'
        ],
        'voice_design_signatures' => [
            '<string>'
        ],
        'tags' => [
            '<string>'
        ],
        'enhance_audio_quality' => true,
        'generate_sample' => false
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
    
    	url := "https://api.fish.audio/model"
    
    	payload := strings.NewReader("{\n  \"type\": \"tts\",\n  \"title\": \"<string>\",\n  \"train_mode\": \"fast\",\n  \"voices\": [\n    \"<string>\"\n  ],\n  \"visibility\": \"private\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"texts\": [\n    \"<string>\"\n  ],\n  \"voice_design_signatures\": [\n    \"<string>\"\n  ],\n  \"tags\": [\n    \"<string>\"\n  ],\n  \"enhance_audio_quality\": true,\n  \"generate_sample\": false\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/model")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"type\": \"tts\",\n  \"title\": \"<string>\",\n  \"train_mode\": \"fast\",\n  \"voices\": [\n    \"<string>\"\n  ],\n  \"visibility\": \"private\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"texts\": [\n    \"<string>\"\n  ],\n  \"voice_design_signatures\": [\n    \"<string>\"\n  ],\n  \"tags\": [\n    \"<string>\"\n  ],\n  \"enhance_audio_quality\": true,\n  \"generate_sample\": false\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/model")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"type\": \"tts\",\n  \"title\": \"<string>\",\n  \"train_mode\": \"fast\",\n  \"voices\": [\n    \"<string>\"\n  ],\n  \"visibility\": \"private\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"texts\": [\n    \"<string>\"\n  ],\n  \"voice_design_signatures\": [\n    \"<string>\"\n  ],\n  \"tags\": [\n    \"<string>\"\n  ],\n  \"enhance_audio_quality\": true,\n  \"generate_sample\": false\n}"
    
    response = http.request(request)
    puts response.read_body

201

401

503
    
    
    {
      "_id": "<string>",
      "type": "svc",
      "title": "<string>",
      "state": "created",
      "tags": [
        "<string>"
      ],
      "created_at": "2023-11-07T05:31:56Z",
      "updated_at": "2023-11-07T05:31:56Z",
      "visibility": "public",
      "like_count": 123,
      "mark_count": 123,
      "shared_count": 123,
      "task_count": 123,
      "author": {
        "_id": "<string>",
        "nickname": "<string>",
        "avatar": "<string>"
      },
      "description": "",
      "cover_image": "",
      "train_mode": "full",
      "samples": [],
      "languages": [],
      "lock_visibility": false,
      "dmca_taken_down": false,
      "takedown_category": "dmca",
      "default_text": "",
      "source": "<string>",
      "licensed": false,
      "pvc_release_state": "released",
      "pvc_notice_period_months": 123,
      "pvc_released_at": "2023-11-07T05:31:56Z",
      "pvc_retire_requested_at": "2023-11-07T05:31:56Z",
      "pvc_retire_effective_at": "2023-11-07T05:31:56Z",
      "quality": {
        "created_at": "2023-11-07T05:31:56Z",
        "updated_at": "2023-11-07T05:31:56Z",
        "audios": [
          {
            "filename": "<string>",
            "duration_ms": 123,
            "language": "unknown",
            "quality": {},
            "quality_passed": false,
            "quality_reason": ""
          }
        ]
      },
      "unliked": false,
      "liked": false,
      "marked": false
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

Voice Models

# Create Model

Copy pageCopy page

Create a new voice model

Copy pageCopy page

POST

/

model

Try it

Create Model for Users via API

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/model \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "type": "tts",
      "title": "<string>",
      "train_mode": "fast",
      "voices": [
        "<string>"
      ],
      "visibility": "private",
      "description": "<string>",
      "cover_image": "<string>",
      "texts": [
        "<string>"
      ],
      "voice_design_signatures": [
        "<string>"
      ],
      "tags": [
        "<string>"
      ],
      "enhance_audio_quality": true,
      "generate_sample": false
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/model"
    
    payload = {
        "type": "tts",
        "title": "<string>",
        "train_mode": "fast",
        "voices": ["<string>"],
        "visibility": "private",
        "description": "<string>",
        "cover_image": "<string>",
        "texts": ["<string>"],
        "voice_design_signatures": ["<string>"],
        "tags": ["<string>"],
        "enhance_audio_quality": True,
        "generate_sample": False
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
        type: 'tts',
        title: '<string>',
        train_mode: 'fast',
        voices: ['<string>'],
        visibility: 'private',
        description: '<string>',
        cover_image: '<string>',
        texts: ['<string>'],
        voice_design_signatures: ['<string>'],
        tags: ['<string>'],
        enhance_audio_quality: true,
        generate_sample: false
      })
    };
    
    fetch('https://api.fish.audio/model', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/model",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'type' => 'tts',
        'title' => '<string>',
        'train_mode' => 'fast',
        'voices' => [
            '<string>'
        ],
        'visibility' => 'private',
        'description' => '<string>',
        'cover_image' => '<string>',
        'texts' => [
            '<string>'
        ],
        'voice_design_signatures' => [
            '<string>'
        ],
        'tags' => [
            '<string>'
        ],
        'enhance_audio_quality' => true,
        'generate_sample' => false
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
    
    	url := "https://api.fish.audio/model"
    
    	payload := strings.NewReader("{\n  \"type\": \"tts\",\n  \"title\": \"<string>\",\n  \"train_mode\": \"fast\",\n  \"voices\": [\n    \"<string>\"\n  ],\n  \"visibility\": \"private\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"texts\": [\n    \"<string>\"\n  ],\n  \"voice_design_signatures\": [\n    \"<string>\"\n  ],\n  \"tags\": [\n    \"<string>\"\n  ],\n  \"enhance_audio_quality\": true,\n  \"generate_sample\": false\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/model")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"type\": \"tts\",\n  \"title\": \"<string>\",\n  \"train_mode\": \"fast\",\n  \"voices\": [\n    \"<string>\"\n  ],\n  \"visibility\": \"private\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"texts\": [\n    \"<string>\"\n  ],\n  \"voice_design_signatures\": [\n    \"<string>\"\n  ],\n  \"tags\": [\n    \"<string>\"\n  ],\n  \"enhance_audio_quality\": true,\n  \"generate_sample\": false\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/model")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"type\": \"tts\",\n  \"title\": \"<string>\",\n  \"train_mode\": \"fast\",\n  \"voices\": [\n    \"<string>\"\n  ],\n  \"visibility\": \"private\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"texts\": [\n    \"<string>\"\n  ],\n  \"voice_design_signatures\": [\n    \"<string>\"\n  ],\n  \"tags\": [\n    \"<string>\"\n  ],\n  \"enhance_audio_quality\": true,\n  \"generate_sample\": false\n}"
    
    response = http.request(request)
    puts response.read_body

201

401

503
    
    
    {
      "_id": "<string>",
      "type": "svc",
      "title": "<string>",
      "state": "created",
      "tags": [
        "<string>"
      ],
      "created_at": "2023-11-07T05:31:56Z",
      "updated_at": "2023-11-07T05:31:56Z",
      "visibility": "public",
      "like_count": 123,
      "mark_count": 123,
      "shared_count": 123,
      "task_count": 123,
      "author": {
        "_id": "<string>",
        "nickname": "<string>",
        "avatar": "<string>"
      },
      "description": "",
      "cover_image": "",
      "train_mode": "full",
      "samples": [],
      "languages": [],
      "lock_visibility": false,
      "dmca_taken_down": false,
      "takedown_category": "dmca",
      "default_text": "",
      "source": "<string>",
      "licensed": false,
      "pvc_release_state": "released",
      "pvc_notice_period_months": 123,
      "pvc_released_at": "2023-11-07T05:31:56Z",
      "pvc_retire_requested_at": "2023-11-07T05:31:56Z",
      "pvc_retire_effective_at": "2023-11-07T05:31:56Z",
      "quality": {
        "created_at": "2023-11-07T05:31:56Z",
        "updated_at": "2023-11-07T05:31:56Z",
        "audios": [
          {
            "filename": "<string>",
            "duration_ms": 123,
            "language": "unknown",
            "quality": {},
            "quality_passed": false,
            "quality_reason": ""
          }
        ]
      },
      "unliked": false,
      "liked": false,
      "marked": false
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

Since this endpoint uploads files, use `multipart/form-data` for regular REST requests. Let your HTTP client set the multipart `Content-Type` boundary automatically.

#### Authorizations

​

Authorization

string

header

required

Bearer authentication header of the form `Bearer <token>`, where `<token>` is your auth token.

#### Body

application/jsonapplication/x-www-form-urlencodedmultipart/form-dataapplication/msgpackapplication/jsonapplication/x-www-form-urlencodedmultipart/form-dataapplication/msgpack

​

type

string

required

Model type, tts is for text to speech

Allowed value: `"tts"`

​

title

string

required

Model title or name

​

train_mode

string

required

Model train mode, for TTS model, fast means model instantly available after creation

Allowed value: `"fast"`

​

voices

file[]filefile[]file

required

Upload voices files that will be used to tune the model

Required array length: `1 - 20` elements

​

visibility

enum<string>

default:private

Model visibility. Public requests are downgraded to private; use the web publish flow to publish publicly. Unlist allows anyone with the link to access, while private is visible only to the creator.

Available options: 

`public`, 

`unlist`, 

`private`

​

description

string | null

Model description

​

cover_image

file | null

Model cover image, this is required if the model is public

​

texts

string[]stringstring[]string

Texts corresponding to the voices, if unspecified, ASR will be performed on the voices

Maximum array length: `20`

​

voice_design_signatures

string[]stringstring[]string

Signatures from /v1/voice-design candidates, one per voice in the same order. When every uploaded voice verifies, the model is stamped source=voice_design; an invalid signature rejects the request.

​

tags

string[]stringstring[]string

Model tags

​

enhance_audio_quality

boolean

default:true

Enhance audio quality

​

generate_sample

boolean

default:false

Generate default text

#### Response

201

application/json

Document created, URL follows

​

_id

string

required

​

type

enum<string>

required

Available options: 

`svc`, 

`tts`

​

title

string

required

​

state

enum<string>

required

Available options: 

`created`, 

`training`, 

`trained`, 

`failed`

​

tags

string[]

required

​

created_at

string<date-time>

required

​

updated_at

string<date-time>

required

​

visibility

enum<string>

required

Available options: 

`public`, 

`unlist`, 

`private`

​

like_count

integer

required

​

mark_count

integer

required

​

shared_count

integer

required

​

task_count

integer

required

​

author

AuthorEntity · object

required

Show child attributes

​

description

string

default:""

​

cover_image

string

default:""

​

train_mode

enum<string>

default:full

Available options: 

`fast`, 

`full`

​

samples

SampleEntity · object[]

Show child attributes

​

languages

string[]

​

lock_visibility

boolean

default:false

​

dmca_taken_down

boolean | null

default:false

​

takedown_category

enum<string> | null

Available options: 

`dmca`, 

`policy`

​

default_text

string

default:""

​

source

string | null

​

licensed

boolean

default:false

​

pvc_release_state

enum<string> | null

Available options: 

`released`, 

`retiring`

​

pvc_notice_period_months

integer | null

​

pvc_released_at

string<date-time> | null

​

pvc_retire_requested_at

string<date-time> | null

​

pvc_retire_effective_at

string<date-time> | null

​

quality

ModelQualityEntity · object | null

Show child attributes

​

unliked

boolean

default:false

​

liked

boolean

default:false

​

marked

boolean

default:false

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/model/create-model.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/model/create-model)

[List Models](https://docs.fish.audio/api-reference/endpoint/model/list-models)[Get Model](https://docs.fish.audio/api-reference/endpoint/model/get-model)
