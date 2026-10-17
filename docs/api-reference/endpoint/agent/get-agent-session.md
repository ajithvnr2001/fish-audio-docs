---
url: https://docs.fish.audio/api-reference/endpoint/agent/get-agent-session/
title: Get Agent Session - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:06.996506+00:00
---

# Get Agent Session - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/get-agent-session/

Get Agent Session

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/sessions/{session_id} \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/sessions/{session_id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/sessions/{session_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/sessions/{session_id}",
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
    
    	url := "https://api.fish.audio/v1/agent/sessions/{session_id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/sessions/{session_id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/sessions/{session_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

401

404

502

503
    
    
    {
      "session_id": "<string>",
      "agent_id": "<string>",
      "agent_name": "<string>",
      "status": "pending",
      "source": "api_key",
      "created_at": "<string>",
      "name": "<string>",
      "end_user_id": "<string>",
      "end_reason": "user_hangup",
      "direction": "inbound",
      "dial_status": "answered",
      "answered_by": "human",
      "caller_number": "<string>",
      "dialed_number": "<string>",
      "sip_call_id": "<string>",
      "timezone": "<string>",
      "started_at": "<string>",
      "ended_at": "<string>",
      "duration_seconds": 123,
      "participant_identity": "<string>",
      "agent_participant_identity": "<string>",
      "agent_joined_at": "<string>",
      "metadata": {},
      "content_purged_at": "<string>",
      "keypad_menu": {
        "outcome": "selected",
        "variable": "<string>",
        "value": "<string>",
        "key": "<string>",
        "input": "dtmf",
        "attempts": 0,
        "completed_at": "2023-11-07T05:31:56Z"
      },
      "unattributed_llm_usage": [
        {
          "status": "complete",
          "billing_mode": "tokens",
          "message_generation_id": "<string>",
          "turn_id": 123,
          "call_count": 0,
          "usage_complete": false,
          "call_ids": [
            "<string>"
          ],
          "cost_usd": "<string>",
          "billable_cost_usd": "<string>",
          "known_cost_usd": "0",
          "tokens": [
            {
              "model": "<string>",
              "rate_version": "<string>",
              "category": "input",
              "tokens": 123,
              "rate_per_million": "<string>",
              "cost_usd": "<string>"
            }
          ]
        }
      ],
      "items": [
        {
          "role": "user",
          "content": "<string>",
          "id": "<string>",
          "runtime_message_id": "<string>",
          "message_generation_id": "<string>",
          "llm_usage": {
            "status": "complete",
            "billing_mode": "tokens",
            "message_generation_id": "<string>",
            "turn_id": 123,
            "call_count": 0,
            "usage_complete": false,
            "call_ids": [
              "<string>"
            ],
            "cost_usd": "<string>",
            "billable_cost_usd": "<string>",
            "known_cost_usd": "0",
            "tokens": [
              {
                "model": "<string>",
                "rate_version": "<string>",
                "category": "input",
                "tokens": 123,
                "rate_per_million": "<string>",
                "cost_usd": "<string>"
              }
            ]
          },
          "type": "message",
          "input_medium": "dtmf",
          "turn_id": 123,
          "created_at": "<string>"
        }
      ],
      "analysis": {
        "status": "queued",
        "summary": "<string>",
        "data": [
          {
            "name": "<string>",
            "type": "boolean",
            "value": true,
            "rationale": ""
          }
        ],
        "criteria_results": [
          {
            "name": "<string>",
            "result": "success",
            "rationale": ""
          }
        ]
      }
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

Sessions

# Get Agent Session

Copy pageCopy page

Fetch one session’s full detail: status, timing, and the conversation timeline (transcript turns interleaved with tool calls, in order).

Copy pageCopy page

GET

/

v1

/

agent

/

sessions

/

{session_id}

Try it

Get Agent Session

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/sessions/{session_id} \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/sessions/{session_id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/sessions/{session_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/sessions/{session_id}",
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
    
    	url := "https://api.fish.audio/v1/agent/sessions/{session_id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/sessions/{session_id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/sessions/{session_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

401

404

502

503
    
    
    {
      "session_id": "<string>",
      "agent_id": "<string>",
      "agent_name": "<string>",
      "status": "pending",
      "source": "api_key",
      "created_at": "<string>",
      "name": "<string>",
      "end_user_id": "<string>",
      "end_reason": "user_hangup",
      "direction": "inbound",
      "dial_status": "answered",
      "answered_by": "human",
      "caller_number": "<string>",
      "dialed_number": "<string>",
      "sip_call_id": "<string>",
      "timezone": "<string>",
      "started_at": "<string>",
      "ended_at": "<string>",
      "duration_seconds": 123,
      "participant_identity": "<string>",
      "agent_participant_identity": "<string>",
      "agent_joined_at": "<string>",
      "metadata": {},
      "content_purged_at": "<string>",
      "keypad_menu": {
        "outcome": "selected",
        "variable": "<string>",
        "value": "<string>",
        "key": "<string>",
        "input": "dtmf",
        "attempts": 0,
        "completed_at": "2023-11-07T05:31:56Z"
      },
      "unattributed_llm_usage": [
        {
          "status": "complete",
          "billing_mode": "tokens",
          "message_generation_id": "<string>",
          "turn_id": 123,
          "call_count": 0,
          "usage_complete": false,
          "call_ids": [
            "<string>"
          ],
          "cost_usd": "<string>",
          "billable_cost_usd": "<string>",
          "known_cost_usd": "0",
          "tokens": [
            {
              "model": "<string>",
              "rate_version": "<string>",
              "category": "input",
              "tokens": 123,
              "rate_per_million": "<string>",
              "cost_usd": "<string>"
            }
          ]
        }
      ],
      "items": [
        {
          "role": "user",
          "content": "<string>",
          "id": "<string>",
          "runtime_message_id": "<string>",
          "message_generation_id": "<string>",
          "llm_usage": {
            "status": "complete",
            "billing_mode": "tokens",
            "message_generation_id": "<string>",
            "turn_id": 123,
            "call_count": 0,
            "usage_complete": false,
            "call_ids": [
              "<string>"
            ],
            "cost_usd": "<string>",
            "billable_cost_usd": "<string>",
            "known_cost_usd": "0",
            "tokens": [
              {
                "model": "<string>",
                "rate_version": "<string>",
                "category": "input",
                "tokens": 123,
                "rate_per_million": "<string>",
                "cost_usd": "<string>"
              }
            ]
          },
          "type": "message",
          "input_medium": "dtmf",
          "turn_id": 123,
          "created_at": "<string>"
        }
      ],
      "analysis": {
        "status": "queued",
        "summary": "<string>",
        "data": [
          {
            "name": "<string>",
            "type": "boolean",
            "value": true,
            "rationale": ""
          }
        ],
        "criteria_results": [
          {
            "name": "<string>",
            "result": "success",
            "rationale": ""
          }
        ]
      }
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

session_id

string

required

#### Response

200

application/json

Request fulfilled, document follows

​

session_id

string

required

​

agent_id

string

required

​

agent_name

string

required

​

status

enum<string>

required

Available options: 

`pending`, 

`active`, 

`completed`, 

`failed`, 

`unknown`

​

source

enum<string>

required

Available options: 

`api_key`, 

`dashboard`, 

`public`, 

`phone`

​

created_at

string

required

​

name

string | null

​

end_user_id

string | null

​

end_reason

enum<string> | null

Available options: 

`user_hangup`, 

`agent_hangup`, 

`escalated`, 

`conversation_timeout`, 

`heartbeat_timeout`, 

`agent_join_timeout`, 

`internal_error`, 

`llm_endpoint_failure`, 

`room_join_timeout`, 

`cancelled`, 

`dial_failed`

​

direction

enum<string>

default:inbound

Available options: 

`inbound`, 

`outbound`

​

dial_status

enum<string> | null

Available options: 

`answered`, 

`busy`, 

`no_answer`, 

`failed`

​

answered_by

enum<string> | null

Available options: 

`human`, 

`voicemail`, 

`unknown`

​

caller_number

string | null

​

dialed_number

string | null

​

sip_call_id

string | null

​

timezone

string | null

​

started_at

string | null

​

ended_at

string | null

​

duration_seconds

integer | null

​

participant_identity

string | null

​

agent_participant_identity

string | null

​

agent_joined_at

string | null

​

metadata

Metadata · object

Show child attributes

​

content_purged_at

string | null

​

keypad_menu

AgentSessionKeypadMenu · object | null

How the keypad menu of an inbound phone call ended. `outcome` is `selected` when the caller chose an option, `no_input` or `no_match` when no attempt got a valid choice (the last one had no input, or input matching no option), and `skipped` when the menu could not run (a resumed conversation or no SIP caller). `value` is what the menu variable received: the chosen option's value, or the fallback value when the caller never made a valid choice.

Show child attributes

​

unattributed_llm_usage

LLMMessageUsage · object[]

Show child attributes

​

items

(AgentSessionMessageItem · object | AgentSessionToolCallItem · object | AgentSessionTransferItem · object | AgentSessionToolResultItem · object)[]

One transcript message; system messages never surface here.

  * AgentSessionMessageItem

  * AgentSessionToolCallItem

  * AgentSessionTransferItem

  * AgentSessionToolResultItem




Show child attributes

​

analysis

AgentSessionAnalysisResult · object | null

Public trim of the post-call analysis record: outcomes only, no run internals (model, tokens, config hash).

Show child attributes

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/get-agent-session.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/get-agent-session)

[List Agent Sessions](https://docs.fish.audio/api-reference/endpoint/agent/list-agent-sessions)[Get Agent Session Recording](https://docs.fish.audio/api-reference/endpoint/agent/get-agent-session-recording)
