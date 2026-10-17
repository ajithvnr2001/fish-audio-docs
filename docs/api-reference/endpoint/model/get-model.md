---
url: https://docs.fish.audio/api-reference/endpoint/model/get-model/
title: Get Model - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:18.588796+00:00
---

# Get Model - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/model/get-model/

Get Model

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/model/{id} \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/model/{id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/model/{id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/model/{id}",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "GET",
      CURLOPT_HTTPHEADER => [
        "Authorization: Bearer <token>"
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
    	"net/http"
    	"io"
    )
    
    func main() {
    
    	url := "https://api.fish.audio/model/{id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/model/{id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/model/{id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

403

404
    
    
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

# Get Model

Copy pageCopy page

Get details of a specific model

Copy pageCopy page

GET

/

model

/

{id}

Try it

Get Model

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/model/{id} \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/model/{id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/model/{id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/model/{id}",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "GET",
      CURLOPT_HTTPHEADER => [
        "Authorization: Bearer <token>"
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
    	"net/http"
    	"io"
    )
    
    func main() {
    
    	url := "https://api.fish.audio/model/{id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/model/{id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/model/{id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

403

404
    
    
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

#### Authorizations

​

Authorization

string

header

required

Bearer authentication header of the form `Bearer <token>`, where `<token>` is your auth token.

#### Path Parameters

​

id

string

required

#### Response

200

application/json

Request fulfilled, document follows

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

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/model/get-model.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/model/get-model)

[Create Model](https://docs.fish.audio/api-reference/endpoint/model/create-model)[Delete Model](https://docs.fish.audio/api-reference/endpoint/model/delete-model)
