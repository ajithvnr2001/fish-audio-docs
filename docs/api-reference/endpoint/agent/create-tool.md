---
url: https://docs.fish.audio/api-reference/endpoint/agent/create-tool/
title: Create Tool - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:05.722930+00:00
---

# Create Tool - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/create-tool/

Create Webhook Tool

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/tools \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{
        "name": "Book appointment",
        "description": "Creates an appointment in the scheduling system.",
        "method": "POST",
        "url": "https://api.example.com/appointments",
        "arguments": [
          {"name": "date", "description": "Appointment date, YYYY-MM-DD"}
        ],
        "body_template": "{\"date\": \"{{date}}\"}",
        "headers": [
          {"name": "Authorization", "value": "Bearer <api-token>", "kind": "authorization_bearer"}
        ]
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/tools"
    
    payload = {
        "name": "<string>",
        "description": "",
        "tool_type": "webhook",
        "arguments": [
            {
                "name": "<string>",
                "description": ""
            }
        ],
        "method": "POST",
        "url": "",
        "content_type": "application/json",
        "body_template": "",
        "headers": [
            {
                "name": "<string>",
                "value": "<string>",
                "kind": "custom"
            }
        ],
        "timeout_seconds": 30,
        "error_handling": "passthrough",
        "mock_responses": [
            {
                "name": "",
                "status_code": 200,
                "content_type": "application/json",
                "body": ""
            }
        ],
        "expects_response": True,
        "execution_mode": "blocking"
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
        name: '<string>',
        description: '',
        tool_type: 'webhook',
        arguments: [{name: '<string>', description: ''}],
        method: 'POST',
        url: '',
        content_type: 'application/json',
        body_template: '',
        headers: [{name: '<string>', value: '<string>', kind: 'custom'}],
        timeout_seconds: 30,
        error_handling: 'passthrough',
        mock_responses: [
          {
            name: '',
            status_code: 200,
            content_type: 'application/json',
            body: JSON.stringify('')
          }
        ],
        expects_response: true,
        execution_mode: 'blocking'
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/tools', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/tools",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'name' => '<string>',
        'description' => '',
        'tool_type' => 'webhook',
        'arguments' => [
            [
                    'name' => '<string>',
                    'description' => ''
            ]
        ],
        'method' => 'POST',
        'url' => '',
        'content_type' => 'application/json',
        'body_template' => '',
        'headers' => [
            [
                    'name' => '<string>',
                    'value' => '<string>',
                    'kind' => 'custom'
            ]
        ],
        'timeout_seconds' => 30,
        'error_handling' => 'passthrough',
        'mock_responses' => [
            [
                    'name' => '',
                    'status_code' => 200,
                    'content_type' => 'application/json',
                    'body' => ''
            ]
        ],
        'expects_response' => true,
        'execution_mode' => 'blocking'
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
    
    	url := "https://api.fish.audio/v1/agent/tools"
    
    	payload := strings.NewReader("{\n  \"name\": \"<string>\",\n  \"description\": \"\",\n  \"tool_type\": \"webhook\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"method\": \"POST\",\n  \"url\": \"\",\n  \"content_type\": \"application/json\",\n  \"body_template\": \"\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 30,\n  \"error_handling\": \"passthrough\",\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true,\n  \"execution_mode\": \"blocking\"\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/tools")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"name\": \"<string>\",\n  \"description\": \"\",\n  \"tool_type\": \"webhook\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"method\": \"POST\",\n  \"url\": \"\",\n  \"content_type\": \"application/json\",\n  \"body_template\": \"\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 30,\n  \"error_handling\": \"passthrough\",\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true,\n  \"execution_mode\": \"blocking\"\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/tools")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"name\": \"<string>\",\n  \"description\": \"\",\n  \"tool_type\": \"webhook\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"method\": \"POST\",\n  \"url\": \"\",\n  \"content_type\": \"application/json\",\n  \"body_template\": \"\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 30,\n  \"error_handling\": \"passthrough\",\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true,\n  \"execution_mode\": \"blocking\"\n}"
    
    response = http.request(request)
    puts response.read_body

201

401

422

503
    
    
    {
      "tool_id": "<string>",
      "workspace_id": "<string>",
      "name": "<string>",
      "tool_type": "webhook",
      "method": "GET",
      "url": "<string>",
      "created_at": "2023-11-07T05:31:56Z",
      "updated_at": "2023-11-07T05:31:56Z",
      "content_type": "<string>",
      "timeout_seconds": 123,
      "error_handling": "passthrough",
      "description": "",
      "used_by": 0,
      "arguments": [
        {
          "name": "<string>",
          "description": ""
        }
      ],
      "body_template": "",
      "headers": [
        {
          "name": "<string>",
          "kind": "custom",
          "value": "<string>",
          "has_secret": false
        }
      ],
      "mock_responses": [
        {
          "name": "",
          "status_code": 200,
          "content_type": "application/json",
          "body": ""
        }
      ],
      "expects_response": true,
      "execution_mode": "blocking"
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

Tools

# Create Tool

Copy pageCopy page

Create a workspace tool.

Copy pageCopy page

POST

/

v1

/

agent

/

tools

Try it

Create Webhook Tool

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/tools \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{
        "name": "Book appointment",
        "description": "Creates an appointment in the scheduling system.",
        "method": "POST",
        "url": "https://api.example.com/appointments",
        "arguments": [
          {"name": "date", "description": "Appointment date, YYYY-MM-DD"}
        ],
        "body_template": "{\"date\": \"{{date}}\"}",
        "headers": [
          {"name": "Authorization", "value": "Bearer <api-token>", "kind": "authorization_bearer"}
        ]
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/tools"
    
    payload = {
        "name": "<string>",
        "description": "",
        "tool_type": "webhook",
        "arguments": [
            {
                "name": "<string>",
                "description": ""
            }
        ],
        "method": "POST",
        "url": "",
        "content_type": "application/json",
        "body_template": "",
        "headers": [
            {
                "name": "<string>",
                "value": "<string>",
                "kind": "custom"
            }
        ],
        "timeout_seconds": 30,
        "error_handling": "passthrough",
        "mock_responses": [
            {
                "name": "",
                "status_code": 200,
                "content_type": "application/json",
                "body": ""
            }
        ],
        "expects_response": True,
        "execution_mode": "blocking"
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
        name: '<string>',
        description: '',
        tool_type: 'webhook',
        arguments: [{name: '<string>', description: ''}],
        method: 'POST',
        url: '',
        content_type: 'application/json',
        body_template: '',
        headers: [{name: '<string>', value: '<string>', kind: 'custom'}],
        timeout_seconds: 30,
        error_handling: 'passthrough',
        mock_responses: [
          {
            name: '',
            status_code: 200,
            content_type: 'application/json',
            body: JSON.stringify('')
          }
        ],
        expects_response: true,
        execution_mode: 'blocking'
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/tools', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/tools",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'name' => '<string>',
        'description' => '',
        'tool_type' => 'webhook',
        'arguments' => [
            [
                    'name' => '<string>',
                    'description' => ''
            ]
        ],
        'method' => 'POST',
        'url' => '',
        'content_type' => 'application/json',
        'body_template' => '',
        'headers' => [
            [
                    'name' => '<string>',
                    'value' => '<string>',
                    'kind' => 'custom'
            ]
        ],
        'timeout_seconds' => 30,
        'error_handling' => 'passthrough',
        'mock_responses' => [
            [
                    'name' => '',
                    'status_code' => 200,
                    'content_type' => 'application/json',
                    'body' => ''
            ]
        ],
        'expects_response' => true,
        'execution_mode' => 'blocking'
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
    
    	url := "https://api.fish.audio/v1/agent/tools"
    
    	payload := strings.NewReader("{\n  \"name\": \"<string>\",\n  \"description\": \"\",\n  \"tool_type\": \"webhook\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"method\": \"POST\",\n  \"url\": \"\",\n  \"content_type\": \"application/json\",\n  \"body_template\": \"\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 30,\n  \"error_handling\": \"passthrough\",\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true,\n  \"execution_mode\": \"blocking\"\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/tools")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"name\": \"<string>\",\n  \"description\": \"\",\n  \"tool_type\": \"webhook\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"method\": \"POST\",\n  \"url\": \"\",\n  \"content_type\": \"application/json\",\n  \"body_template\": \"\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 30,\n  \"error_handling\": \"passthrough\",\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true,\n  \"execution_mode\": \"blocking\"\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/tools")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"name\": \"<string>\",\n  \"description\": \"\",\n  \"tool_type\": \"webhook\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"method\": \"POST\",\n  \"url\": \"\",\n  \"content_type\": \"application/json\",\n  \"body_template\": \"\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 30,\n  \"error_handling\": \"passthrough\",\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true,\n  \"execution_mode\": \"blocking\"\n}"
    
    response = http.request(request)
    puts response.read_body

201

401

422

503
    
    
    {
      "tool_id": "<string>",
      "workspace_id": "<string>",
      "name": "<string>",
      "tool_type": "webhook",
      "method": "GET",
      "url": "<string>",
      "created_at": "2023-11-07T05:31:56Z",
      "updated_at": "2023-11-07T05:31:56Z",
      "content_type": "<string>",
      "timeout_seconds": 123,
      "error_handling": "passthrough",
      "description": "",
      "used_by": 0,
      "arguments": [
        {
          "name": "<string>",
          "description": ""
        }
      ],
      "body_template": "",
      "headers": [
        {
          "name": "<string>",
          "kind": "custom",
          "value": "<string>",
          "has_secret": false
        }
      ],
      "mock_responses": [
        {
          "name": "",
          "status_code": 200,
          "content_type": "application/json",
          "body": ""
        }
      ],
      "expects_response": true,
      "execution_mode": "blocking"
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

application/json

Console payload minus the folder concept (folders are console-only).

​

name

string

required

Required string length: `1 - 120`

​

description

string

default:""

Maximum string length: `2000`

​

tool_type

enum<string>

default:webhook

Available options: 

`webhook`, 

`client`

​

arguments

AgentWebhookArgumentPayload · object[]

Show child attributes

​

method

enum<string>

default:POST

Available options: 

`GET`, 

`POST`, 

`PUT`, 

`PATCH`, 

`DELETE`

​

url

string

default:""

Maximum string length: `4000`

​

content_type

string

default:application/json

Maximum string length: `128`

​

body_template

string

default:""

Request body sent for non-GET calls. `{{argument}}`, `{{system.*}}` and custom session variable placeholders are filled in at call time; a missing value becomes empty. When the body's content type is JSON (the default `application/json`, any `+json` type, or a `Content-Type` header saying so), a placeholder inside a JSON string, such as `{"note": "{{note}}"}`, is JSON-escaped, so quotes, backslashes and newlines in the value keep the body valid JSON. A placeholder outside a string, such as `{"count": {{count}}}`, is inserted as is. Other content types are filled in as is.

Maximum string length: `100000`

​

headers

AgentWebhookHeaderPayload · object[]

Show child attributes

​

timeout_seconds

integer

default:30

Required range: `1 <= x <= 300`

​

error_handling

enum<string>

default:passthrough

Available options: 

`passthrough`, 

`hide`

​

mock_responses

AgentWebhookMockResponsePayload · object[]

Show child attributes

​

expects_response

boolean

default:true

​

execution_mode

enum<string>

default:blocking

Available options: 

`blocking`, 

`fire_and_forget`, 

`background`

#### Response

201

application/json

Document created, URL follows

​

tool_id

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

tool_type

enum<string>

required

Available options: 

`webhook`, 

`client`

​

method

enum<string>

required

Available options: 

`GET`, 

`POST`, 

`PUT`, 

`PATCH`, 

`DELETE`

​

url

string

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

content_type

string

required

​

timeout_seconds

integer

required

​

error_handling

enum<string>

required

Available options: 

`passthrough`, 

`hide`

​

description

string

default:""

​

used_by

integer

default:0

How many agents reference this tool in their draft configuration.

​

arguments

AgentWebhookArgumentPayload · object[]

Show child attributes

​

body_template

string

default:""

​

headers

PublicToolHeader · object[]

Show child attributes

​

mock_responses

AgentWebhookMockResponsePayload · object[]

Show child attributes

​

expects_response

boolean

default:true

​

execution_mode

enum<string>

default:blocking

Available options: 

`blocking`, 

`fire_and_forget`, 

`background`

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/create-tool.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/create-tool)

[List Tools](https://docs.fish.audio/api-reference/endpoint/agent/list-tools)[Get Tool](https://docs.fish.audio/api-reference/endpoint/agent/get-tool)
