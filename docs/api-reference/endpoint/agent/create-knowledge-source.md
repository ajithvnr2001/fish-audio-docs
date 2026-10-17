---
url: https://docs.fish.audio/api-reference/endpoint/agent/create-knowledge-source/
title: Create Knowledge Source - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:03.866170+00:00
---

# Create Knowledge Source - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/create-knowledge-source/

Create Knowledge Source

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/knowledge-sources \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: multipart/form-data' \
      --form source=@example-file \
      --form 'name=<string>' \
      --form description=
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/knowledge-sources"
    
    files = { "source": ("example-file", open("example-file", "rb")) }
    payload = {
        "name": "<string>",
        "description": ""
    }
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.post(url, data=payload, files=files, headers=headers)
    
    print(response.text)
    
    
    const form = new FormData();
    form.append('source', '<string>');
    form.append('name', '<string>');
    form.append('description', '');
    
    const options = {method: 'POST', headers: {Authorization: 'Bearer <token>'}};
    
    options.body = form;
    
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
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => "-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"source\"; filename=\"example-file\"\r\nContent-Type: application/octet-stream\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"description\"\r\n\r\n\r\n-----011000010111000001101001--",
      CURLOPT_HTTPHEADER => [
        "Authorization: Bearer <token>",
        "Content-Type: multipart/form-data"
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
    
    	url := "https://api.fish.audio/v1/agent/knowledge-sources"
    
    	payload := strings.NewReader("-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"source\"; filename=\"example-file\"\r\nContent-Type: application/octet-stream\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"description\"\r\n\r\n\r\n-----011000010111000001101001--")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/knowledge-sources")
      .header("Authorization", "Bearer <token>")
      .body("-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"source\"; filename=\"example-file\"\r\nContent-Type: application/octet-stream\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"description\"\r\n\r\n\r\n-----011000010111000001101001--")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/knowledge-sources")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request.body = "-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"source\"; filename=\"example-file\"\r\nContent-Type: application/octet-stream\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"description\"\r\n\r\n\r\n-----011000010111000001101001--"
    
    response = http.request(request)
    puts response.read_body

201

400

401

403

422

503
    
    
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
      "content": "<string>",
      "description": ""
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

# Create Knowledge Source

Copy pageCopy page

Upload a plain-text or Markdown file (UTF-8, up to 1 MB) as a knowledge source.

Copy pageCopy page

POST

/

v1

/

agent

/

knowledge-sources

Try it

Create Knowledge Source

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/knowledge-sources \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: multipart/form-data' \
      --form source=@example-file \
      --form 'name=<string>' \
      --form description=
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/knowledge-sources"
    
    files = { "source": ("example-file", open("example-file", "rb")) }
    payload = {
        "name": "<string>",
        "description": ""
    }
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.post(url, data=payload, files=files, headers=headers)
    
    print(response.text)
    
    
    const form = new FormData();
    form.append('source', '<string>');
    form.append('name', '<string>');
    form.append('description', '');
    
    const options = {method: 'POST', headers: {Authorization: 'Bearer <token>'}};
    
    options.body = form;
    
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
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => "-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"source\"; filename=\"example-file\"\r\nContent-Type: application/octet-stream\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"description\"\r\n\r\n\r\n-----011000010111000001101001--",
      CURLOPT_HTTPHEADER => [
        "Authorization: Bearer <token>",
        "Content-Type: multipart/form-data"
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
    
    	url := "https://api.fish.audio/v1/agent/knowledge-sources"
    
    	payload := strings.NewReader("-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"source\"; filename=\"example-file\"\r\nContent-Type: application/octet-stream\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"description\"\r\n\r\n\r\n-----011000010111000001101001--")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/knowledge-sources")
      .header("Authorization", "Bearer <token>")
      .body("-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"source\"; filename=\"example-file\"\r\nContent-Type: application/octet-stream\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"description\"\r\n\r\n\r\n-----011000010111000001101001--")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/knowledge-sources")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request.body = "-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"source\"; filename=\"example-file\"\r\nContent-Type: application/octet-stream\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\n<string>\r\n-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"description\"\r\n\r\n\r\n-----011000010111000001101001--"
    
    response = http.request(request)
    puts response.read_body

201

400

401

403

422

503
    
    
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
      "content": "<string>",
      "description": ""
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

#### Body

multipart/form-data

​

source

file

required

​

name

string | null

​

description

string

default:""

#### Response

201

application/json

Document created, URL follows

​

knowledge_source_id

string

required

​

workspace_id

string

required

​

name

string

required

​

file_name

string

required

​

size_bytes

integer

required

​

chunk_count

integer

required

​

revision_number

integer

required

Increments every time the content is replaced. Drafts always use the newest revision; published versions pin the revision current at publish time.

​

created_at

string<date-time>

required

​

updated_at

string<date-time>

required

​

content

string

required

The full current text content.

​

description

string

default:""

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/create-knowledge-source.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/create-knowledge-source)

[List Knowledge Sources](https://docs.fish.audio/api-reference/endpoint/agent/list-knowledge-sources)[Get Knowledge Source](https://docs.fish.audio/api-reference/endpoint/agent/get-knowledge-source)
