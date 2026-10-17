---
url: https://docs.fish.audio/api-reference/endpoint/agent/get-test/
title: Get Test - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:09.772620+00:00
---

# Get Test - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/get-test/

Get Test

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/tests/{test_id} \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/tests/{test_id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/tests/{test_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/tests/{test_id}",
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
    
    	url := "https://api.fish.audio/v1/agent/tests/{test_id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/tests/{test_id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/tests/{test_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

401

404

503
    
    
    {
      "test_id": "<string>",
      "workspace_id": "<string>",
      "name": "<string>",
      "test_type": "next_reply",
      "created_at": "2023-11-07T05:31:56Z",
      "updated_at": "2023-11-07T05:31:56Z",
      "agent_ids": [
        "<string>"
      ],
      "conversation": [
        {
          "role": "agent",
          "text": "<string>"
        }
      ],
      "expectation": "",
      "success_examples": [
        "<string>"
      ],
      "failure_examples": [
        "<string>"
      ],
      "referenced_tool": {
        "id": "<string>",
        "name": "<string>",
        "type": "webhook",
        "description": ""
      },
      "tool_parameters": [
        {
          "name": "<string>",
          "value": "<string>",
          "type": "string"
        }
      ],
      "verify_absence": false,
      "simulation": {
        "scenario": "<string>",
        "success_conditions": [
          {
            "name": "<string>",
            "description": "<string>"
          }
        ],
        "max_turns": 10,
        "assertions": {
          "tool_calls": [
            {
              "tool": {
                "id": "<string>",
                "name": "<string>",
                "type": "webhook",
                "description": ""
              },
              "params": {},
              "min_calls": 1,
              "max_calls": 50
            }
          ],
          "forbidden_tools": [
            {
              "id": "<string>",
              "name": "<string>",
              "type": "webhook",
              "description": ""
            }
          ],
          "ended_by": "agent"
        },
        "tool_mocks": {
          "strategy": "all",
          "fallback": "error",
          "tools": [
            {
              "tool": {
                "id": "<string>",
                "name": "<string>",
                "type": "webhook",
                "description": ""
              },
              "result": "<unknown>",
              "status": 349,
              "when": {},
              "error": false
            }
          ],
          "real_tools": [
            {
              "id": "<string>",
              "name": "<string>",
              "type": "webhook",
              "description": ""
            }
          ]
        },
        "simulated_user_model": "<string>",
        "repeat_count": 1,
        "channel": "web_voice"
      },
      "dynamic_variables": {}
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

# Get Test

Copy pageCopy page

Fetch one test’s full definition, which is also the export format.

Copy pageCopy page

GET

/

v1

/

agent

/

tests

/

{test_id}

Try it

Get Test

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/tests/{test_id} \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/tests/{test_id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/tests/{test_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/tests/{test_id}",
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
    
    	url := "https://api.fish.audio/v1/agent/tests/{test_id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/tests/{test_id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/tests/{test_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

401

404

503
    
    
    {
      "test_id": "<string>",
      "workspace_id": "<string>",
      "name": "<string>",
      "test_type": "next_reply",
      "created_at": "2023-11-07T05:31:56Z",
      "updated_at": "2023-11-07T05:31:56Z",
      "agent_ids": [
        "<string>"
      ],
      "conversation": [
        {
          "role": "agent",
          "text": "<string>"
        }
      ],
      "expectation": "",
      "success_examples": [
        "<string>"
      ],
      "failure_examples": [
        "<string>"
      ],
      "referenced_tool": {
        "id": "<string>",
        "name": "<string>",
        "type": "webhook",
        "description": ""
      },
      "tool_parameters": [
        {
          "name": "<string>",
          "value": "<string>",
          "type": "string"
        }
      ],
      "verify_absence": false,
      "simulation": {
        "scenario": "<string>",
        "success_conditions": [
          {
            "name": "<string>",
            "description": "<string>"
          }
        ],
        "max_turns": 10,
        "assertions": {
          "tool_calls": [
            {
              "tool": {
                "id": "<string>",
                "name": "<string>",
                "type": "webhook",
                "description": ""
              },
              "params": {},
              "min_calls": 1,
              "max_calls": 50
            }
          ],
          "forbidden_tools": [
            {
              "id": "<string>",
              "name": "<string>",
              "type": "webhook",
              "description": ""
            }
          ],
          "ended_by": "agent"
        },
        "tool_mocks": {
          "strategy": "all",
          "fallback": "error",
          "tools": [
            {
              "tool": {
                "id": "<string>",
                "name": "<string>",
                "type": "webhook",
                "description": ""
              },
              "result": "<unknown>",
              "status": 349,
              "when": {},
              "error": false
            }
          ],
          "real_tools": [
            {
              "id": "<string>",
              "name": "<string>",
              "type": "webhook",
              "description": ""
            }
          ]
        },
        "simulated_user_model": "<string>",
        "repeat_count": 1,
        "channel": "web_voice"
      },
      "dynamic_variables": {}
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

test_id

string

required

#### Response

200

application/json

Request fulfilled, document follows

​

test_id

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

test_type

enum<string>

required

Available options: 

`next_reply`, 

`tool`, 

`simulation`

​

created_at

string<date-time>

required

​

updated_at

string<date-time>

required

​

agent_ids

string[]

Agents this test is attached to.

​

conversation

PublicAgentTestMessage · object[]

Show child attributes

​

expectation

string

default:""

​

success_examples

string[]

​

failure_examples

string[]

​

referenced_tool

AgentTestReferencedTool · object | null

Tool the runner should (or should not) observe on the next turn. A webhook or client tool is referenced by its library id, an integration tool by "<provider_key>:<tool_name>" (for example "google_calendar:create_event").

Show child attributes

​

tool_parameters

AgentTestToolParameter · object[]

Show child attributes

​

verify_absence

boolean

default:false

​

simulation

AgentTestSimulationConfig · object | null

Show child attributes

​

dynamic_variables

Dynamic Variables · object

Show child attributes

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/get-test.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/get-test)

[Create Test](https://docs.fish.audio/api-reference/endpoint/agent/create-test)[Update Test](https://docs.fish.audio/api-reference/endpoint/agent/update-test)
