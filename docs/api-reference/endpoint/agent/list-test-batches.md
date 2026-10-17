---
url: https://docs.fish.audio/api-reference/endpoint/agent/list-test-batches/
title: List Test Batches - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:13.357433+00:00
---

# List Test Batches - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/list-test-batches/

List Test Batches

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches",
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

400

401

404

503
    
    
    {
      "batches": [
        {
          "batch_id": "<string>",
          "agent_id": "<string>",
          "status": "running",
          "completed": true,
          "passed": 123,
          "failed": 123,
          "errors": 123,
          "run_count": 123,
          "trigger_source": "console",
          "created_at": "2023-11-07T05:31:56Z",
          "pass_rate": 123,
          "finished_at": "2023-11-07T05:31:56Z"
        }
      ],
      "has_more": true,
      "next_cursor": "<string>"
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

Tests

# List Test Batches

Copy pageCopy page

The agent’s test batches, newest first, with their counts.

Copy pageCopy page

GET

/

v1

/

agent

/

agents

/

{agent_id}

/

test-batches

Try it

List Test Batches

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches",
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

400

401

404

503
    
    
    {
      "batches": [
        {
          "batch_id": "<string>",
          "agent_id": "<string>",
          "status": "running",
          "completed": true,
          "passed": 123,
          "failed": 123,
          "errors": 123,
          "run_count": 123,
          "trigger_source": "console",
          "created_at": "2023-11-07T05:31:56Z",
          "pass_rate": 123,
          "finished_at": "2023-11-07T05:31:56Z"
        }
      ],
      "has_more": true,
      "next_cursor": "<string>"
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

#### Path Parameters

​

agent_id

string

required

#### Query Parameters

​

cursor

string | null

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

batches

PublicAgentTestBatchSummary · object[]

required

Show child attributes

​

has_more

boolean

required

​

next_cursor

string | null

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/list-test-batches.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/list-test-batches)

[Run Tests](https://docs.fish.audio/api-reference/endpoint/agent/run-tests)[Get Test Batch](https://docs.fish.audio/api-reference/endpoint/agent/get-test-batch)
