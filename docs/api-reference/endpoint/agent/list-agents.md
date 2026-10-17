---
url: https://docs.fish.audio/api-reference/endpoint/agent/list-agents/
title: List Agents - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:12.004014+00:00
---

# List Agents - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/list-agents/

List Agents

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/agents \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/agents', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents",
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
    
    	url := "https://api.fish.audio/v1/agent/agents"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/agents")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents")
    
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
      "agents": [
        {
          "agent_id": "<string>",
          "workspace_id": "<string>",
          "name": "<string>",
          "status": "active",
          "publication_state": "live",
          "created_at": "2023-11-07T05:31:56Z",
          "updated_at": "2023-11-07T05:31:56Z",
          "description": "",
          "public_enabled": false,
          "allowed_origins": [
            "<string>"
          ],
          "overrides_allowed": [
            "first_message"
          ]
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

Agents

# List Agents

Copy pageCopy page

List your team’s agents, newest first.

Copy pageCopy page

GET

/

v1

/

agent

/

agents

Try it

List Agents

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/agents \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/agents', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents",
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
    
    	url := "https://api.fish.audio/v1/agent/agents"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/agents")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents")
    
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
      "agents": [
        {
          "agent_id": "<string>",
          "workspace_id": "<string>",
          "name": "<string>",
          "status": "active",
          "publication_state": "live",
          "created_at": "2023-11-07T05:31:56Z",
          "updated_at": "2023-11-07T05:31:56Z",
          "description": "",
          "public_enabled": false,
          "allowed_origins": [
            "<string>"
          ],
          "overrides_allowed": [
            "first_message"
          ]
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

Case-insensitive match on name and description.

​

include_archived

boolean

default:false

​

publication_state

enum<string>

default:all

`live` = has a published version; `draft` = never published.

Available options: 

`all`, 

`live`, 

`draft`

​

cursor

string | null

​

page

integer | null

1-based page number (offset pagination). Returns total; mutually exclusive with cursor.

Required range: `x >= 1`

​

include_total

boolean

default:false

Also count the filtered set on the cursor path.

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

agents

PublicAgentEntity · object[]

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

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/list-agents.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/list-agents)

[Agents API Errors](https://docs.fish.audio/api-reference/agent-errors)[Create Agent](https://docs.fish.audio/api-reference/endpoint/agent/create-agent)
