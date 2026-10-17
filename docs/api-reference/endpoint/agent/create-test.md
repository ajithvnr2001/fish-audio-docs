---
url: https://docs.fish.audio/api-reference/endpoint/agent/create-test/
title: Create Test - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:05.150240+00:00
---

# Create Test - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/create-test/

Create Simulation Test

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/tests \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{
        "name": "Reschedules an appointment",
        "test_type": "simulation",
        "agent_ids": ["<agent-id>"],
        "simulation": {
          "scenario": "You are Jane. Move your Tuesday cleaning to Thursday afternoon.",
          "max_turns": 10,
          "success_conditions": [
            {"name": "rescheduled", "description": "The agent confirms the new Thursday slot."}
          ],
          "tool_mocks": {
            "strategy": "all",
            "tools": [
              {
                "tool": {"id": "<tool-id>", "name": "Book appointment", "type": "webhook"},
                "result": {"status": "confirmed"}
              }
            ]
          }
        }
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/tests"
    
    payload = {
        "name": "<string>",
        "test_type": "next_reply",
        "conversation": [{ "text": "<string>" }],
        "expectation": "",
        "success_examples": ["<string>"],
        "failure_examples": ["<string>"],
        "referenced_tool": {
            "id": "<string>",
            "name": "<string>",
            "type": "webhook",
            "description": ""
        },
        "tool_parameters": [
            {
                "name": "<string>",
                "value": "<string>"
            }
        ],
        "verify_absence": False,
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
                ]
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
                        "error": False
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
            "repeat_count": 1
        },
        "dynamic_variables": {},
        "agent_ids": ["<string>"]
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
        test_type: 'next_reply',
        conversation: [{text: '<string>'}],
        expectation: '',
        success_examples: ['<string>'],
        failure_examples: ['<string>'],
        referenced_tool: {id: '<string>', name: '<string>', type: 'webhook', description: ''},
        tool_parameters: [{name: '<string>', value: '<string>'}],
        verify_absence: false,
        simulation: {
          scenario: '<string>',
          success_conditions: [{name: '<string>', description: '<string>'}],
          max_turns: 10,
          assertions: {
            tool_calls: [
              {
                tool: {id: '<string>', name: '<string>', type: 'webhook', description: ''},
                params: {},
                min_calls: 1,
                max_calls: 50
              }
            ],
            forbidden_tools: [{id: '<string>', name: '<string>', type: 'webhook', description: ''}]
          },
          tool_mocks: {
            strategy: 'all',
            fallback: 'error',
            tools: [
              {
                tool: {id: '<string>', name: '<string>', type: 'webhook', description: ''},
                result: '<unknown>',
                status: 349,
                when: {},
                error: false
              }
            ],
            real_tools: [{id: '<string>', name: '<string>', type: 'webhook', description: ''}]
          },
          simulated_user_model: '<string>',
          repeat_count: 1
        },
        dynamic_variables: {},
        agent_ids: ['<string>']
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/tests', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/tests",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'name' => '<string>',
        'test_type' => 'next_reply',
        'conversation' => [
            [
                    'text' => '<string>'
            ]
        ],
        'expectation' => '',
        'success_examples' => [
            '<string>'
        ],
        'failure_examples' => [
            '<string>'
        ],
        'referenced_tool' => [
            'id' => '<string>',
            'name' => '<string>',
            'type' => 'webhook',
            'description' => ''
        ],
        'tool_parameters' => [
            [
                    'name' => '<string>',
                    'value' => '<string>'
            ]
        ],
        'verify_absence' => false,
        'simulation' => [
            'scenario' => '<string>',
            'success_conditions' => [
                    [
                                    'name' => '<string>',
                                    'description' => '<string>'
                    ]
            ],
            'max_turns' => 10,
            'assertions' => [
                    'tool_calls' => [
                                    [
                                                                    'tool' => [
                                                                                                                                    'id' => '<string>',
                                                                                                                                    'name' => '<string>',
                                                                                                                                    'type' => 'webhook',
                                                                                                                                    'description' => ''
                                                                    ],
                                                                    'params' => [
                                                                                                                                    
                                                                    ],
                                                                    'min_calls' => 1,
                                                                    'max_calls' => 50
                                    ]
                    ],
                    'forbidden_tools' => [
                                    [
                                                                    'id' => '<string>',
                                                                    'name' => '<string>',
                                                                    'type' => 'webhook',
                                                                    'description' => ''
                                    ]
                    ]
            ],
            'tool_mocks' => [
                    'strategy' => 'all',
                    'fallback' => 'error',
                    'tools' => [
                                    [
                                                                    'tool' => [
                                                                                                                                    'id' => '<string>',
                                                                                                                                    'name' => '<string>',
                                                                                                                                    'type' => 'webhook',
                                                                                                                                    'description' => ''
                                                                    ],
                                                                    'result' => '<unknown>',
                                                                    'status' => 349,
                                                                    'when' => [
                                                                                                                                    
                                                                    ],
                                                                    'error' => false
                                    ]
                    ],
                    'real_tools' => [
                                    [
                                                                    'id' => '<string>',
                                                                    'name' => '<string>',
                                                                    'type' => 'webhook',
                                                                    'description' => ''
                                    ]
                    ]
            ],
            'simulated_user_model' => '<string>',
            'repeat_count' => 1
        ],
        'dynamic_variables' => [
            
        ],
        'agent_ids' => [
            '<string>'
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
    
    	url := "https://api.fish.audio/v1/agent/tests"
    
    	payload := strings.NewReader("{\n  \"name\": \"<string>\",\n  \"test_type\": \"next_reply\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": false,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {},\n  \"agent_ids\": [\n    \"<string>\"\n  ]\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/tests")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"name\": \"<string>\",\n  \"test_type\": \"next_reply\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": false,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {},\n  \"agent_ids\": [\n    \"<string>\"\n  ]\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/tests")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"name\": \"<string>\",\n  \"test_type\": \"next_reply\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": false,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {},\n  \"agent_ids\": [\n    \"<string>\"\n  ]\n}"
    
    response = http.request(request)
    puts response.read_body

201

400

401

422

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
    
    
    {
      "status": 123,
      "message": "<string>",
      "reason": "<string>"
    }

Tests

# Create Test

Copy pageCopy page

Create a Single Turn, Tool or Simulation test, optionally attached to agents.

Copy pageCopy page

POST

/

v1

/

agent

/

tests

Try it

Create Simulation Test

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/tests \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{
        "name": "Reschedules an appointment",
        "test_type": "simulation",
        "agent_ids": ["<agent-id>"],
        "simulation": {
          "scenario": "You are Jane. Move your Tuesday cleaning to Thursday afternoon.",
          "max_turns": 10,
          "success_conditions": [
            {"name": "rescheduled", "description": "The agent confirms the new Thursday slot."}
          ],
          "tool_mocks": {
            "strategy": "all",
            "tools": [
              {
                "tool": {"id": "<tool-id>", "name": "Book appointment", "type": "webhook"},
                "result": {"status": "confirmed"}
              }
            ]
          }
        }
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/tests"
    
    payload = {
        "name": "<string>",
        "test_type": "next_reply",
        "conversation": [{ "text": "<string>" }],
        "expectation": "",
        "success_examples": ["<string>"],
        "failure_examples": ["<string>"],
        "referenced_tool": {
            "id": "<string>",
            "name": "<string>",
            "type": "webhook",
            "description": ""
        },
        "tool_parameters": [
            {
                "name": "<string>",
                "value": "<string>"
            }
        ],
        "verify_absence": False,
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
                ]
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
                        "error": False
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
            "repeat_count": 1
        },
        "dynamic_variables": {},
        "agent_ids": ["<string>"]
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
        test_type: 'next_reply',
        conversation: [{text: '<string>'}],
        expectation: '',
        success_examples: ['<string>'],
        failure_examples: ['<string>'],
        referenced_tool: {id: '<string>', name: '<string>', type: 'webhook', description: ''},
        tool_parameters: [{name: '<string>', value: '<string>'}],
        verify_absence: false,
        simulation: {
          scenario: '<string>',
          success_conditions: [{name: '<string>', description: '<string>'}],
          max_turns: 10,
          assertions: {
            tool_calls: [
              {
                tool: {id: '<string>', name: '<string>', type: 'webhook', description: ''},
                params: {},
                min_calls: 1,
                max_calls: 50
              }
            ],
            forbidden_tools: [{id: '<string>', name: '<string>', type: 'webhook', description: ''}]
          },
          tool_mocks: {
            strategy: 'all',
            fallback: 'error',
            tools: [
              {
                tool: {id: '<string>', name: '<string>', type: 'webhook', description: ''},
                result: '<unknown>',
                status: 349,
                when: {},
                error: false
              }
            ],
            real_tools: [{id: '<string>', name: '<string>', type: 'webhook', description: ''}]
          },
          simulated_user_model: '<string>',
          repeat_count: 1
        },
        dynamic_variables: {},
        agent_ids: ['<string>']
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/tests', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/tests",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'name' => '<string>',
        'test_type' => 'next_reply',
        'conversation' => [
            [
                    'text' => '<string>'
            ]
        ],
        'expectation' => '',
        'success_examples' => [
            '<string>'
        ],
        'failure_examples' => [
            '<string>'
        ],
        'referenced_tool' => [
            'id' => '<string>',
            'name' => '<string>',
            'type' => 'webhook',
            'description' => ''
        ],
        'tool_parameters' => [
            [
                    'name' => '<string>',
                    'value' => '<string>'
            ]
        ],
        'verify_absence' => false,
        'simulation' => [
            'scenario' => '<string>',
            'success_conditions' => [
                    [
                                    'name' => '<string>',
                                    'description' => '<string>'
                    ]
            ],
            'max_turns' => 10,
            'assertions' => [
                    'tool_calls' => [
                                    [
                                                                    'tool' => [
                                                                                                                                    'id' => '<string>',
                                                                                                                                    'name' => '<string>',
                                                                                                                                    'type' => 'webhook',
                                                                                                                                    'description' => ''
                                                                    ],
                                                                    'params' => [
                                                                                                                                    
                                                                    ],
                                                                    'min_calls' => 1,
                                                                    'max_calls' => 50
                                    ]
                    ],
                    'forbidden_tools' => [
                                    [
                                                                    'id' => '<string>',
                                                                    'name' => '<string>',
                                                                    'type' => 'webhook',
                                                                    'description' => ''
                                    ]
                    ]
            ],
            'tool_mocks' => [
                    'strategy' => 'all',
                    'fallback' => 'error',
                    'tools' => [
                                    [
                                                                    'tool' => [
                                                                                                                                    'id' => '<string>',
                                                                                                                                    'name' => '<string>',
                                                                                                                                    'type' => 'webhook',
                                                                                                                                    'description' => ''
                                                                    ],
                                                                    'result' => '<unknown>',
                                                                    'status' => 349,
                                                                    'when' => [
                                                                                                                                    
                                                                    ],
                                                                    'error' => false
                                    ]
                    ],
                    'real_tools' => [
                                    [
                                                                    'id' => '<string>',
                                                                    'name' => '<string>',
                                                                    'type' => 'webhook',
                                                                    'description' => ''
                                    ]
                    ]
            ],
            'simulated_user_model' => '<string>',
            'repeat_count' => 1
        ],
        'dynamic_variables' => [
            
        ],
        'agent_ids' => [
            '<string>'
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
    
    	url := "https://api.fish.audio/v1/agent/tests"
    
    	payload := strings.NewReader("{\n  \"name\": \"<string>\",\n  \"test_type\": \"next_reply\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": false,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {},\n  \"agent_ids\": [\n    \"<string>\"\n  ]\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/tests")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"name\": \"<string>\",\n  \"test_type\": \"next_reply\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": false,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {},\n  \"agent_ids\": [\n    \"<string>\"\n  ]\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/tests")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"name\": \"<string>\",\n  \"test_type\": \"next_reply\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": false,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {},\n  \"agent_ids\": [\n    \"<string>\"\n  ]\n}"
    
    response = http.request(request)
    puts response.read_body

201

400

401

422

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

​

name

string

required

Required string length: `1 - 200`

​

test_type

enum<string>

default:next_reply

Available options: 

`next_reply`, 

`tool`, 

`simulation`

​

conversation

AgentTestMessagePayload · object[]

Show child attributes

​

expectation

string

default:""

Maximum string length: `400`

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

​

agent_ids

string[]

Agents to attach the test to. They must all be in one workspace, and the test is created there. Without agents the test goes into the API key owner's default workspace.

Maximum array length: `100`

#### Response

201

application/json

Document created, URL follows

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

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/create-test.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/create-test)

[List Tests](https://docs.fish.audio/api-reference/endpoint/agent/list-tests)[Get Test](https://docs.fish.audio/api-reference/endpoint/agent/get-test)
