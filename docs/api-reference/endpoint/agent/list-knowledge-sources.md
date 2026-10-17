---
url: https://docs.fish.audio/api-reference/endpoint/agent/list-knowledge-sources/
title: List Knowledge Sources - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:14.959792+00:00
---

# List Knowledge Sources - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/list-knowledge-sources/

List Knowledge Sources

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/knowledge-sources \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/knowledge-sources"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/knowledge-sources', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/knowledge-sources",
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
    
    	url := "https://api.fish.audio/v1/agent/knowledge-sources"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/knowledge-sources")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/knowledge-sources")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

400

401

503
    
    
    {
      "knowledge_sources": [
        {
          "knowledge_source_id": "<string>",
          "workspace_id": "<string>",
          "name": "<string>",
          "file_name": "<string>",
          "size_bytes": 123,
          "chunk_count": 123,
          "revision_number": 123,
          "created_at": "2023-11-07T05:31:56Z",
          "updated_at": "2023-11-07T05:31:56Z",
          "description": ""
        }
      ],
      "has_more": true,
      "next_cursor": "<string>",
      "total": 123
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
    
    
    {
      "status": 123,
      "message": "<string>",
      "reason": "<string>"
    }

Knowledge Sources

# List Knowledge Sources

Copy pageCopy page

List your team’s knowledge sources, newest first.

Copy pageCopy page

GET

/

v1

/

agent

/

knowledge-sources

Try it

List Knowledge Sources

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/knowledge-sources \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/knowledge-sources"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/knowledge-sources', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/knowledge-sources",
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
    
    	url := "https://api.fish.audio/v1/agent/knowledge-sources"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/knowledge-sources")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/knowledge-sources")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

400

401

503
    
    
    {
      "knowledge_sources": [
        {
          "knowledge_source_id": "<string>",
          "workspace_id": "<string>",
          "name": "<string>",
          "file_name": "<string>",
          "size_bytes": 123,
          "chunk_count": 123,
          "revision_number": 123,
          "created_at": "2023-11-07T05:31:56Z",
          "updated_at": "2023-11-07T05:31:56Z",
          "description": ""
        }
      ],
      "has_more": true,
      "next_cursor": "<string>",
      "total": 123
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

#### Query Parameters

​

search

string | null

Case-insensitive match on name and file name.

​

cursor

string | null

​

page

integer | null

1-based page number; mutually exclusive with cursor.

Required range: `x >= 1`

​

include_total

boolean

default:false

​

page_size

integer

default:30

Required range: `1 <= x <= 100`

#### Response

200

application/json

Request fulfilled, document follows

​

knowledge_sources

PublicKnowledgeSourceSummary · object[]

required

Show child attributes

​

has_more

boolean

required

​

next_cursor

string | null

​

total

integer | null

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/list-knowledge-sources.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/list-knowledge-sources)

[Get Test Run](https://docs.fish.audio/api-reference/endpoint/agent/get-test-run)[Create Knowledge Source](https://docs.fish.audio/api-reference/endpoint/agent/create-knowledge-source)
