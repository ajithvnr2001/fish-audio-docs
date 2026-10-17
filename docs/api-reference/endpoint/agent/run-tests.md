---
url: https://docs.fish.audio/api-reference/endpoint/agent/run-tests/
title: Run Tests - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:14.390024+00:00
---

# Run Tests - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/run-tests/

Run Tests

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/agents/<agent-id>/tests/run \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{}'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run"
    
    payload = {
        "test_ids": ["<string>"],
        "repeat_count": 10
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
      body: JSON.stringify({test_ids: ['<string>'], repeat_count: 10})
    };
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'test_ids' => [
            '<string>'
        ],
        'repeat_count' => 10
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run"
    
    	payload := strings.NewReader("{\n  \"test_ids\": [\n    \"<string>\"\n  ],\n  \"repeat_count\": 10\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"test_ids\": [\n    \"<string>\"\n  ],\n  \"repeat_count\": 10\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"test_ids\": [\n    \"<string>\"\n  ],\n  \"repeat_count\": 10\n}"
    
    response = http.request(request)
    puts response.read_body

202

400

401

404

422

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

# Run Tests

Copy pageCopy page

Start a batch that runs the agent’s attached tests against its draft.

Copy pageCopy page

POST

/

v1

/

agent

/

agents

/

{agent_id}

/

tests

/

run

Try it

Run Tests

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/agents/<agent-id>/tests/run \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{}'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run"
    
    payload = {
        "test_ids": ["<string>"],
        "repeat_count": 10
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
      body: JSON.stringify({test_ids: ['<string>'], repeat_count: 10})
    };
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'test_ids' => [
            '<string>'
        ],
        'repeat_count' => 10
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run"
    
    	payload := strings.NewReader("{\n  \"test_ids\": [\n    \"<string>\"\n  ],\n  \"repeat_count\": 10\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"test_ids\": [\n    \"<string>\"\n  ],\n  \"repeat_count\": 10\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/tests/run")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"test_ids\": [\n    \"<string>\"\n  ],\n  \"repeat_count\": 10\n}"
    
    response = http.request(request)
    puts response.read_body

202

400

401

404

422

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

test_ids

string[]

Attached tests to run. Omit to run every test attached to the agent.

Minimum array length: `1`

​

repeat_count

integer

Run every selected test this many times in this batch, in place of each test's own repeat count.

Required range: `1 <= x <= 20`

#### Response

202

application/json

Request accepted, processing continues off-line

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

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/run-tests.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/run-tests)

[List Test Tools](https://docs.fish.audio/api-reference/endpoint/agent/list-test-tools)[List Test Batches](https://docs.fish.audio/api-reference/endpoint/agent/list-test-batches)
