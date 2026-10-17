---
url: https://docs.fish.audio/api-reference/endpoint/agent/update-agent/
title: Update Agent - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:16.097073+00:00
---

# Update Agent - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/update-agent/

Update Agent

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/v1/agent/agents/{agent_id} \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "name": "<string>",
      "description": "<string>",
      "public_enabled": true,
      "allowed_origins": [
        "<string>"
      ],
      "overrides_allowed": []
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}"
    
    payload = {
        "name": "<string>",
        "description": "<string>",
        "public_enabled": True,
        "allowed_origins": ["<string>"],
        "overrides_allowed": []
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
        name: '<string>',
        description: '<string>',
        public_enabled: true,
        allowed_origins: ['<string>'],
        overrides_allowed: []
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'name' => '<string>',
        'description' => '<string>',
        'public_enabled' => true,
        'allowed_origins' => [
            '<string>'
        ],
        'overrides_allowed' => [
            
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}"
    
    	payload := strings.NewReader("{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"public_enabled\": true,\n  \"allowed_origins\": [\n    \"<string>\"\n  ],\n  \"overrides_allowed\": []\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/v1/agent/agents/{agent_id}")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"public_enabled\": true,\n  \"allowed_origins\": [\n    \"<string>\"\n  ],\n  \"overrides_allowed\": []\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"public_enabled\": true,\n  \"allowed_origins\": [\n    \"<string>\"\n  ],\n  \"overrides_allowed\": []\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

404

422

503
    
    
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

Agents

# Update Agent

Copy pageCopy page

Update agent-level fields (name, description, status, public access and session-override policy).

Copy pageCopy page

PATCH

/

v1

/

agent

/

agents

/

{agent_id}

Try it

Update Agent

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/v1/agent/agents/{agent_id} \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "name": "<string>",
      "description": "<string>",
      "public_enabled": true,
      "allowed_origins": [
        "<string>"
      ],
      "overrides_allowed": []
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}"
    
    payload = {
        "name": "<string>",
        "description": "<string>",
        "public_enabled": True,
        "allowed_origins": ["<string>"],
        "overrides_allowed": []
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
        name: '<string>',
        description: '<string>',
        public_enabled: true,
        allowed_origins: ['<string>'],
        overrides_allowed: []
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'name' => '<string>',
        'description' => '<string>',
        'public_enabled' => true,
        'allowed_origins' => [
            '<string>'
        ],
        'overrides_allowed' => [
            
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}"
    
    	payload := strings.NewReader("{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"public_enabled\": true,\n  \"allowed_origins\": [\n    \"<string>\"\n  ],\n  \"overrides_allowed\": []\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/v1/agent/agents/{agent_id}")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"public_enabled\": true,\n  \"allowed_origins\": [\n    \"<string>\"\n  ],\n  \"overrides_allowed\": []\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"public_enabled\": true,\n  \"allowed_origins\": [\n    \"<string>\"\n  ],\n  \"overrides_allowed\": []\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

404

422

503
    
    
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

#### Body

application/json

​

name

string | null

Required string length: `1 - 120`

​

description

string | null

Maximum string length: `2000`

​

status

enum<string> | null

Available options: 

`active`, 

`archived`

​

public_enabled

boolean | null

Allow keyless session creation from the browser SDK, gated by allowed_origins.

​

allowed_origins

string[] | null

Maximum array length: `20`

​

overrides_allowed

enum<string>[] | null

Which session-creation overrides callers may use. An empty list rejects all overrides.

Maximum array length: `8`

Available options: 

`first_message`, 

`system_prompt`, 

`voice_id`, 

`language`, 

`asr.model`

#### Response

200

application/json

Request fulfilled, document follows

​

agent_id

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

status

enum<string>

required

Available options: 

`active`, 

`archived`

​

publication_state

enum<string>

required

`live` once at least one version is published; `draft` agents cannot take sessions yet.

Available options: 

`live`, 

`draft`

​

created_at

string<date-time>

required

​

updated_at

string<date-time>

required

​

description

string

default:""

​

public_enabled

boolean

default:false

​

allowed_origins

string[]

​

overrides_allowed

enum<string>[]

Available options: 

`first_message`, 

`system_prompt`, 

`voice_id`, 

`language`, 

`asr.model`

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/update-agent.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/update-agent)

[Get Agent](https://docs.fish.audio/api-reference/endpoint/agent/get-agent)[Delete Agent](https://docs.fish.audio/api-reference/endpoint/agent/delete-agent)
