---
url: https://docs.fish.audio/api-reference/endpoint/agent/get-test-run/
title: Get Test Run - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:11.519851+00:00
---

# Get Test Run - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/get-test-run/

Get Test Run

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/test-runs/{run_id} \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/test-runs/{run_id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/test-runs/{run_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/test-runs/{run_id}",
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
    
    	url := "https://api.fish.audio/v1/agent/test-runs/{run_id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/test-runs/{run_id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/test-runs/{run_id}")
    
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
      "run_id": "<string>",
      "test_id": "<string>",
      "agent_id": "<string>",
      "test_type": "next_reply",
      "status": "queued",
      "created_at": "2023-11-07T05:31:56Z",
      "batch_id": "<string>",
      "repeat_index": 0,
      "needs_review": false,
      "error": "",
      "usage": {
        "agent_replies": 0,
        "cost_usd": "<string>"
      },
      "started_at": "2023-11-07T05:31:56Z",
      "finished_at": "2023-11-07T05:31:56Z",
      "agent_reply": "",
      "judge_reasoning": "",
      "config_hash": "",
      "latency_ms": 0,
      "simulation_result": {
        "transcript": [
          {
            "role": "user",
            "text": "",
            "turn_id": 123,
            "node_id": "<string>",
            "created_at": "<string>",
            "seq": 123
          }
        ],
        "tool_calls": [
          {
            "id": "",
            "tool_name": "",
            "tool_source": "",
            "input": {},
            "status": "",
            "output": "<string>",
            "error": "<string>",
            "mocked": false,
            "mock_source": "test",
            "node_id": "",
            "turn_id": 123,
            "created_at": "<string>",
            "seq": 123
          }
        ],
        "assertions": [
          {
            "kind": "tool_call",
            "target": "<string>",
            "passed": true,
            "tool_id": "<string>",
            "tool_type": "webhook",
            "detail": ""
          }
        ],
        "conditions": [
          {
            "name": "<string>",
            "result": "success",
            "rationale": ""
          }
        ],
        "summary": "",
        "passed": false
      },
      "channel": "web_voice",
      "turns_used": 0,
      "ended_by": "agent",
      "mock_gaps": [
        {
          "tool_name": "<string>",
          "source": "missing",
          "tool_id": "<string>",
          "tool_type": "webhook",
          "calls": 0
        }
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

Tests

# Get Test Run

Copy pageCopy page

Fetch one test run with its transcript, verdicts and tool calls.

Copy pageCopy page

GET

/

v1

/

agent

/

test-runs

/

{run_id}

Try it

Get Test Run

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/test-runs/{run_id} \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/test-runs/{run_id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/test-runs/{run_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/test-runs/{run_id}",
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
    
    	url := "https://api.fish.audio/v1/agent/test-runs/{run_id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/test-runs/{run_id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/test-runs/{run_id}")
    
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
      "run_id": "<string>",
      "test_id": "<string>",
      "agent_id": "<string>",
      "test_type": "next_reply",
      "status": "queued",
      "created_at": "2023-11-07T05:31:56Z",
      "batch_id": "<string>",
      "repeat_index": 0,
      "needs_review": false,
      "error": "",
      "usage": {
        "agent_replies": 0,
        "cost_usd": "<string>"
      },
      "started_at": "2023-11-07T05:31:56Z",
      "finished_at": "2023-11-07T05:31:56Z",
      "agent_reply": "",
      "judge_reasoning": "",
      "config_hash": "",
      "latency_ms": 0,
      "simulation_result": {
        "transcript": [
          {
            "role": "user",
            "text": "",
            "turn_id": 123,
            "node_id": "<string>",
            "created_at": "<string>",
            "seq": 123
          }
        ],
        "tool_calls": [
          {
            "id": "",
            "tool_name": "",
            "tool_source": "",
            "input": {},
            "status": "",
            "output": "<string>",
            "error": "<string>",
            "mocked": false,
            "mock_source": "test",
            "node_id": "",
            "turn_id": 123,
            "created_at": "<string>",
            "seq": 123
          }
        ],
        "assertions": [
          {
            "kind": "tool_call",
            "target": "<string>",
            "passed": true,
            "tool_id": "<string>",
            "tool_type": "webhook",
            "detail": ""
          }
        ],
        "conditions": [
          {
            "name": "<string>",
            "result": "success",
            "rationale": ""
          }
        ],
        "summary": "",
        "passed": false
      },
      "channel": "web_voice",
      "turns_used": 0,
      "ended_by": "agent",
      "mock_gaps": [
        {
          "tool_name": "<string>",
          "source": "missing",
          "tool_id": "<string>",
          "tool_type": "webhook",
          "calls": 0
        }
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

#### Authorizations

​

Authorization

string

header

required

Bearer authentication header of the form `Bearer <token>`, where `<token>` is your auth token.

#### Path Parameters

​

run_id

string

required

#### Response

200

application/json

Request fulfilled, document follows

​

run_id

string

required

​

test_id

string

required

​

agent_id

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

status

enum<string>

required

Available options: 

`queued`, 

`running`, 

`passed`, 

`failed`, 

`error`

​

created_at

string<date-time>

required

​

batch_id

string | null

​

repeat_index

integer

default:0

Which repeat of the test in its batch this run is.

​

needs_review

boolean

default:false

The judge could not decide, or a tool call had no mock answer.

​

error

string

default:""

​

usage

PublicAgentTestRunUsage · object

Show child attributes

​

started_at

string<date-time> | null

​

finished_at

string<date-time> | null

​

agent_reply

string

default:""

The reply a scripted test judged.

​

judge_reasoning

string

default:""

​

config_hash

string

default:""

The agent draft's config hash the run tested.

​

latency_ms

integer

default:0

​

simulation_result

AgentTestSimulationResult · object | null

The simulation run's result: what was said, what the agent called, the deterministic assertions and the judge's per-condition verdicts.

Show child attributes

​

channel

enum<string> | null

Available options: 

`web_voice`, 

`phone_inbound`, 

`phone_outbound`

​

turns_used

integer

default:0

​

ended_by

enum<string> | null

Available options: 

`agent`, 

`user`, 

`transfer`, 

`max_turns`, 

`timeout`, 

`error`

​

mock_gaps

AgentTestMockGap · object[]

Show child attributes

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/get-test-run.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/get-test-run)

[List Test Runs](https://docs.fish.audio/api-reference/endpoint/agent/list-test-runs)[List Knowledge Sources](https://docs.fish.audio/api-reference/endpoint/agent/list-knowledge-sources)
