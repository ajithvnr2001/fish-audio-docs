---
url: https://docs.fish.audio/api-reference/endpoint/model/list-models/
title: List Models - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:19.442799+00:00
---

# List Models - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/model/list-models/

List Models

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/model \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/model"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
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
    
    	url := "https://api.fish.audio/model"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/model")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/model")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200
    
    
    {
      "total": 123,
      "items": [
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
      ],
      "max_offset": 123,
      "accessible_upper_bound": 123,
      "window_limited": false,
      "total_is_exact": true,
      "has_more": true
    }

Voice Models

# List Models

Copy pageCopy page

Get a list of all models

Copy pageCopy page

GET

/

model

Try it

List Models

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/model \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/model"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
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
    
    	url := "https://api.fish.audio/model"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/model")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/model")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200
    
    
    {
      "total": 123,
      "items": [
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
      ],
      "max_offset": 123,
      "accessible_upper_bound": 123,
      "window_limited": false,
      "total_is_exact": true,
      "has_more": true
    }

#### Authorizations

​

Authorization

string

header

required

Bearer authentication header of the form `Bearer <token>`, where `<token>` is your auth token.

#### Query Parameters

​

page_size

integer

default:10

Page size

Required range: `1 <= x <= 100`

​

page_number

integer

default:1

Page number

Required range: `x >= 1`

​

title

string | null

Title to filter models

​

tag

string[]stringstring[]string

Tag to filter models

​

self

boolean

default:false

If True, return models owned by the active workspace

​

author_id

string | null

Author ID to filter public models; ignored if self is True

​

language

string[]stringstring[]string

Language to filter models

​

title_language

string[]stringstring[]string

Title language to filter models

​

licensed

boolean

default:false

If True, only voices licensed by Fish Audio (rights secured from the voice owner) are returned; ignored if self is True

​

sort_by

enum<string>

default:score

Available options: 

`score`, 

`task_count`, 

`created_at`

#### Response

200 - application/json

Request fulfilled, document follows

​

total

integer

required

​

items

ModelEntity · object[]

required

Show child attributes

​

max_offset

integer | null

​

accessible_upper_bound

integer | null

​

window_limited

boolean

default:false

​

total_is_exact

boolean

default:true

​

has_more

boolean | null

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/model/list-models.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/model/list-models)

[Get User Package](https://docs.fish.audio/api-reference/endpoint/wallet/get-user-package)[Create Model](https://docs.fish.audio/api-reference/endpoint/model/create-model)
