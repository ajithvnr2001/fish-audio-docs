---
url: https://docs.fish.audio/api-reference/endpoint/model/update-model/
title: Update Model - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:19.667618+00:00
---

# Update Model - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/model/update-model/

Update Model

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/model/{id} \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "title": "<string>",
      "description": "<string>",
      "cover_image": "<string>",
      "tags": [
        "<string>"
      ]
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/model/{id}"
    
    payload = {
        "title": "<string>",
        "description": "<string>",
        "cover_image": "<string>",
        "tags": ["<string>"]
    }
    headers = {
        "Authorization": "Bearer <token>",
        "Content-Type": "application/json"
    }
    
    response = requests.patch(url, json=payload, headers=headers)
    
    print(response.text)
    
    
    const options = {
      method: 'PATCH',
      headers: {Authorization: 'Bearer <token>', 'Content-Type': 'application/json'},
      body: JSON.stringify({
        title: '<string>',
        description: '<string>',
        cover_image: '<string>',
        tags: ['<string>']
      })
    };
    
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
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'title' => '<string>',
        'description' => '<string>',
        'cover_image' => '<string>',
        'tags' => [
            '<string>'
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
    
    	url := "https://api.fish.audio/model/{id}"
    
    	payload := strings.NewReader("{\n  \"title\": \"<string>\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"tags\": [\n    \"<string>\"\n  ]\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/model/{id}")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"title\": \"<string>\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"tags\": [\n    \"<string>\"\n  ]\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/model/{id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"title\": \"<string>\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"tags\": [\n    \"<string>\"\n  ]\n}"
    
    response = http.request(request)
    puts response.read_body

401

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

Voice Models

# Update Model

Copy pageCopy page

Update an existing model

Copy pageCopy page

PATCH

/

model

/

{id}

Try it

Update Model

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/model/{id} \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "title": "<string>",
      "description": "<string>",
      "cover_image": "<string>",
      "tags": [
        "<string>"
      ]
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/model/{id}"
    
    payload = {
        "title": "<string>",
        "description": "<string>",
        "cover_image": "<string>",
        "tags": ["<string>"]
    }
    headers = {
        "Authorization": "Bearer <token>",
        "Content-Type": "application/json"
    }
    
    response = requests.patch(url, json=payload, headers=headers)
    
    print(response.text)
    
    
    const options = {
      method: 'PATCH',
      headers: {Authorization: 'Bearer <token>', 'Content-Type': 'application/json'},
      body: JSON.stringify({
        title: '<string>',
        description: '<string>',
        cover_image: '<string>',
        tags: ['<string>']
      })
    };
    
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
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'title' => '<string>',
        'description' => '<string>',
        'cover_image' => '<string>',
        'tags' => [
            '<string>'
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
    
    	url := "https://api.fish.audio/model/{id}"
    
    	payload := strings.NewReader("{\n  \"title\": \"<string>\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"tags\": [\n    \"<string>\"\n  ]\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/model/{id}")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"title\": \"<string>\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"tags\": [\n    \"<string>\"\n  ]\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/model/{id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"title\": \"<string>\",\n  \"description\": \"<string>\",\n  \"cover_image\": \"<string>\",\n  \"tags\": [\n    \"<string>\"\n  ]\n}"
    
    response = http.request(request)
    puts response.read_body

401

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

#### Body

application/jsonapplication/x-www-form-urlencodedmultipart/form-dataapplication/msgpackapplication/jsonapplication/x-www-form-urlencodedmultipart/form-dataapplication/msgpack

​

title

string | null

​

description

string | null

​

cover_image

file | null

​

visibility

enum<string> | null

Available options: 

`public`, 

`unlist`, 

`private`

​

tags

string[]stringstring[]string

#### Response

200

Request fulfilled, document follows

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/model/update-model.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/model/update-model)

[Delete Model](https://docs.fish.audio/api-reference/endpoint/model/delete-model)[Text to Speech](https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech)
