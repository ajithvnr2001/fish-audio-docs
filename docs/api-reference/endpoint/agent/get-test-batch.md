---
url: https://docs.fish.audio/api-reference/endpoint/agent/get-test-batch/
title: Get Test Batch - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:09.417699+00:00
---

# Get Test Batch - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/get-test-batch/

Poll Test Batch

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/agents/<agent-id>/test-batches/<batch-id> \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}",
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}")
    
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
      "batch_id": "<string>",
      "agent_id": "<string>",
      "status": "running",
      "completed": true,
      "passed": 123,
      "failed": 123,
      "errors": 123,
      "runs": [
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
      ],
      "pass_rate": 123
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

# Get Test Batch

Copy pageCopy page

The runs of one batch with their pass, fail and error counts.

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

/

{batch_id}

Try it

Poll Test Batch

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/agents/<agent-id>/test-batches/<batch-id> \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}",
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/test-batches/{batch_id}")
    
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
      "batch_id": "<string>",
      "agent_id": "<string>",
      "status": "running",
      "completed": true,
      "passed": 123,
      "failed": 123,
      "errors": 123,
      "runs": [
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
      ],
      "pass_rate": 123
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

​

batch_id

string

required

#### Response

200

application/json

Request fulfilled, document follows

​

batch_id

string

required

​

agent_id

string

required

​

status

enum<string>

required

running until every run has finished.

Available options: 

`running`, 

`completed`

​

completed

boolean

required

​

passed

integer

required

​

failed

integer

required

​

errors

integer

required

​

runs

PublicAgentTestRun · object[]

required

Show child attributes

​

pass_rate

number | null

passed / (passed + failed), null until a run passed or failed. Error runs never judged the agent and are left out.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/get-test-batch.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/get-test-batch)

[List Test Batches](https://docs.fish.audio/api-reference/endpoint/agent/list-test-batches)[List Test Runs](https://docs.fish.audio/api-reference/endpoint/agent/list-test-runs)
