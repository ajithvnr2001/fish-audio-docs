---
url: https://docs.fish.audio/api-reference/endpoint/agent/update-tool/
title: Update Tool - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:17.433100+00:00
---

# Update Tool - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/update-tool/

Update Tool

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/v1/agent/tools/{tool_id} \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "name": "<string>",
      "description": "<string>",
      "arguments": [
        {
          "name": "<string>",
          "description": ""
        }
      ],
      "url": "<string>",
      "content_type": "<string>",
      "body_template": "<string>",
      "headers": [
        {
          "name": "<string>",
          "value": "<string>",
          "kind": "custom"
        }
      ],
      "timeout_seconds": 150,
      "mock_responses": [
        {
          "name": "",
          "status_code": 200,
          "content_type": "application/json",
          "body": ""
        }
      ],
      "expects_response": true
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/tools/{tool_id}"
    
    payload = {
        "name": "<string>",
        "description": "<string>",
        "arguments": [
            {
                "name": "<string>",
                "description": ""
            }
        ],
        "url": "<string>",
        "content_type": "<string>",
        "body_template": "<string>",
        "headers": [
            {
                "name": "<string>",
                "value": "<string>",
                "kind": "custom"
            }
        ],
        "timeout_seconds": 150,
        "mock_responses": [
            {
                "name": "",
                "status_code": 200,
                "content_type": "application/json",
                "body": ""
            }
        ],
        "expects_response": True
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
        arguments: [{name: '<string>', description: ''}],
        url: '<string>',
        content_type: '<string>',
        body_template: '<string>',
        headers: [{name: '<string>', value: '<string>', kind: 'custom'}],
        timeout_seconds: 150,
        mock_responses: [
          {
            name: '',
            status_code: 200,
            content_type: 'application/json',
            body: JSON.stringify('')
          }
        ],
        expects_response: true
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/tools/{tool_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/tools/{tool_id}",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'name' => '<string>',
        'description' => '<string>',
        'arguments' => [
            [
                    'name' => '<string>',
                    'description' => ''
            ]
        ],
        'url' => '<string>',
        'content_type' => '<string>',
        'body_template' => '<string>',
        'headers' => [
            [
                    'name' => '<string>',
                    'value' => '<string>',
                    'kind' => 'custom'
            ]
        ],
        'timeout_seconds' => 150,
        'mock_responses' => [
            [
                    'name' => '',
                    'status_code' => 200,
                    'content_type' => 'application/json',
                    'body' => ''
            ]
        ],
        'expects_response' => true
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
    
    	url := "https://api.fish.audio/v1/agent/tools/{tool_id}"
    
    	payload := strings.NewReader("{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"url\": \"<string>\",\n  \"content_type\": \"<string>\",\n  \"body_template\": \"<string>\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 150,\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/v1/agent/tools/{tool_id}")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"url\": \"<string>\",\n  \"content_type\": \"<string>\",\n  \"body_template\": \"<string>\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 150,\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/tools/{tool_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"url\": \"<string>\",\n  \"content_type\": \"<string>\",\n  \"body_template\": \"<string>\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 150,\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true\n}"
    
    response = http.request(request)
    puts response.read_body

200

400

401

404

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

# Update Tool

Copy pageCopy page

Patch tool fields; omitted fields keep their value (null is rejected — send an empty string to clear a text field).

Copy pageCopy page

PATCH

/

v1

/

agent

/

tools

/

{tool_id}

Try it

Update Tool

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/v1/agent/tools/{tool_id} \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "name": "<string>",
      "description": "<string>",
      "arguments": [
        {
          "name": "<string>",
          "description": ""
        }
      ],
      "url": "<string>",
      "content_type": "<string>",
      "body_template": "<string>",
      "headers": [
        {
          "name": "<string>",
          "value": "<string>",
          "kind": "custom"
        }
      ],
      "timeout_seconds": 150,
      "mock_responses": [
        {
          "name": "",
          "status_code": 200,
          "content_type": "application/json",
          "body": ""
        }
      ],
      "expects_response": true
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/tools/{tool_id}"
    
    payload = {
        "name": "<string>",
        "description": "<string>",
        "arguments": [
            {
                "name": "<string>",
                "description": ""
            }
        ],
        "url": "<string>",
        "content_type": "<string>",
        "body_template": "<string>",
        "headers": [
            {
                "name": "<string>",
                "value": "<string>",
                "kind": "custom"
            }
        ],
        "timeout_seconds": 150,
        "mock_responses": [
            {
                "name": "",
                "status_code": 200,
                "content_type": "application/json",
                "body": ""
            }
        ],
        "expects_response": True
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
        arguments: [{name: '<string>', description: ''}],
        url: '<string>',
        content_type: '<string>',
        body_template: '<string>',
        headers: [{name: '<string>', value: '<string>', kind: 'custom'}],
        timeout_seconds: 150,
        mock_responses: [
          {
            name: '',
            status_code: 200,
            content_type: 'application/json',
            body: JSON.stringify('')
          }
        ],
        expects_response: true
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/tools/{tool_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/tools/{tool_id}",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'name' => '<string>',
        'description' => '<string>',
        'arguments' => [
            [
                    'name' => '<string>',
                    'description' => ''
            ]
        ],
        'url' => '<string>',
        'content_type' => '<string>',
        'body_template' => '<string>',
        'headers' => [
            [
                    'name' => '<string>',
                    'value' => '<string>',
                    'kind' => 'custom'
            ]
        ],
        'timeout_seconds' => 150,
        'mock_responses' => [
            [
                    'name' => '',
                    'status_code' => 200,
                    'content_type' => 'application/json',
                    'body' => ''
            ]
        ],
        'expects_response' => true
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
    
    	url := "https://api.fish.audio/v1/agent/tools/{tool_id}"
    
    	payload := strings.NewReader("{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"url\": \"<string>\",\n  \"content_type\": \"<string>\",\n  \"body_template\": \"<string>\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 150,\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/v1/agent/tools/{tool_id}")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"url\": \"<string>\",\n  \"content_type\": \"<string>\",\n  \"body_template\": \"<string>\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 150,\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/tools/{tool_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"name\": \"<string>\",\n  \"description\": \"<string>\",\n  \"arguments\": [\n    {\n      \"name\": \"<string>\",\n      \"description\": \"\"\n    }\n  ],\n  \"url\": \"<string>\",\n  \"content_type\": \"<string>\",\n  \"body_template\": \"<string>\",\n  \"headers\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\",\n      \"kind\": \"custom\"\n    }\n  ],\n  \"timeout_seconds\": 150,\n  \"mock_responses\": [\n    {\n      \"name\": \"\",\n      \"status_code\": 200,\n      \"content_type\": \"application/json\",\n      \"body\": \"\"\n    }\n  ],\n  \"expects_response\": true\n}"
    
    response = http.request(request)
    puts response.read_body

200

400

401

404

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

tool_id

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

arguments

AgentWebhookArgumentPayload · object[] | null

Show child attributes

​

method

enum<string> | null

Available options: 

`GET`, 

`POST`, 

`PUT`, 

`PATCH`, 

`DELETE`

​

url

string | null

Required string length: `1 - 4000`

​

content_type

string | null

Maximum string length: `128`

​

body_template

string | null

Request body sent for non-GET calls. `{{argument}}`, `{{system.*}}` and custom session variable placeholders are filled in at call time; a missing value becomes empty. When the body's content type is JSON (the default `application/json`, any `+json` type, or a `Content-Type` header saying so), a placeholder inside a JSON string, such as `{"note": "{{note}}"}`, is JSON-escaped, so quotes, backslashes and newlines in the value keep the body valid JSON. A placeholder outside a string, such as `{"count": {{count}}}`, is inserted as is. Other content types are filled in as is.

Maximum string length: `100000`

​

headers

AgentWebhookHeaderPayload · object[] | null

Show child attributes

​

timeout_seconds

integer | null

Required range: `1 <= x <= 300`

​

error_handling

enum<string> | null

Available options: 

`passthrough`, 

`hide`

​

mock_responses

AgentWebhookMockResponsePayload · object[] | null

Show child attributes

​

expects_response

boolean | null

​

execution_mode

enum<string> | null

Available options: 

`blocking`, 

`fire_and_forget`, 

`background`

#### Response

200

application/json

Request fulfilled, document follows

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

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/update-tool.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/update-tool)

[Get Tool](https://docs.fish.audio/api-reference/endpoint/agent/get-tool)[Delete Tool](https://docs.fish.audio/api-reference/endpoint/agent/delete-tool)
