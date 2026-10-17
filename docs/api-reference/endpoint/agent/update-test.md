---
url: https://docs.fish.audio/api-reference/endpoint/agent/update-test/
title: Update Test - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:16.637376+00:00
---

# Update Test - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/update-test/

Update Test

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/v1/agent/tests/{test_id} \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "name": "<string>",
      "conversation": [
        {
          "text": "<string>"
        }
      ],
      "expectation": "<string>",
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
          "value": "<string>"
        }
      ],
      "verify_absence": true,
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
        "repeat_count": 1
      },
      "dynamic_variables": {}
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/tests/{test_id}"
    
    payload = {
        "name": "<string>",
        "conversation": [{ "text": "<string>" }],
        "expectation": "<string>",
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
        "verify_absence": True,
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
        "dynamic_variables": {}
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
        conversation: [{text: '<string>'}],
        expectation: '<string>',
        success_examples: ['<string>'],
        failure_examples: ['<string>'],
        referenced_tool: {id: '<string>', name: '<string>', type: 'webhook', description: ''},
        tool_parameters: [{name: '<string>', value: '<string>'}],
        verify_absence: true,
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
        dynamic_variables: {}
      })
    };
    
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
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'name' => '<string>',
        'conversation' => [
            [
                    'text' => '<string>'
            ]
        ],
        'expectation' => '<string>',
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
        'verify_absence' => true,
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
    
    	url := "https://api.fish.audio/v1/agent/tests/{test_id}"
    
    	payload := strings.NewReader("{\n  \"name\": \"<string>\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"<string>\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": true,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {}\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/v1/agent/tests/{test_id}")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"name\": \"<string>\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"<string>\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": true,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {}\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/tests/{test_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"name\": \"<string>\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"<string>\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": true,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {}\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

404

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

# Update Test

Copy pageCopy page

Patch test fields. Omitted fields keep their value.

Copy pageCopy page

PATCH

/

v1

/

agent

/

tests

/

{test_id}

Try it

Update Test

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/v1/agent/tests/{test_id} \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "name": "<string>",
      "conversation": [
        {
          "text": "<string>"
        }
      ],
      "expectation": "<string>",
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
          "value": "<string>"
        }
      ],
      "verify_absence": true,
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
        "repeat_count": 1
      },
      "dynamic_variables": {}
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/tests/{test_id}"
    
    payload = {
        "name": "<string>",
        "conversation": [{ "text": "<string>" }],
        "expectation": "<string>",
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
        "verify_absence": True,
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
        "dynamic_variables": {}
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
        conversation: [{text: '<string>'}],
        expectation: '<string>',
        success_examples: ['<string>'],
        failure_examples: ['<string>'],
        referenced_tool: {id: '<string>', name: '<string>', type: 'webhook', description: ''},
        tool_parameters: [{name: '<string>', value: '<string>'}],
        verify_absence: true,
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
        dynamic_variables: {}
      })
    };
    
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
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'name' => '<string>',
        'conversation' => [
            [
                    'text' => '<string>'
            ]
        ],
        'expectation' => '<string>',
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
        'verify_absence' => true,
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
    
    	url := "https://api.fish.audio/v1/agent/tests/{test_id}"
    
    	payload := strings.NewReader("{\n  \"name\": \"<string>\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"<string>\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": true,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {}\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/v1/agent/tests/{test_id}")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"name\": \"<string>\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"<string>\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": true,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {}\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/tests/{test_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"name\": \"<string>\",\n  \"conversation\": [\n    {\n      \"text\": \"<string>\"\n    }\n  ],\n  \"expectation\": \"<string>\",\n  \"success_examples\": [\n    \"<string>\"\n  ],\n  \"failure_examples\": [\n    \"<string>\"\n  ],\n  \"referenced_tool\": {\n    \"id\": \"<string>\",\n    \"name\": \"<string>\",\n    \"type\": \"webhook\",\n    \"description\": \"\"\n  },\n  \"tool_parameters\": [\n    {\n      \"name\": \"<string>\",\n      \"value\": \"<string>\"\n    }\n  ],\n  \"verify_absence\": true,\n  \"simulation\": {\n    \"scenario\": \"<string>\",\n    \"success_conditions\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"<string>\"\n      }\n    ],\n    \"max_turns\": 10,\n    \"assertions\": {\n      \"tool_calls\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"params\": {},\n          \"min_calls\": 1,\n          \"max_calls\": 50\n        }\n      ],\n      \"forbidden_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"tool_mocks\": {\n      \"strategy\": \"all\",\n      \"fallback\": \"error\",\n      \"tools\": [\n        {\n          \"tool\": {\n            \"id\": \"<string>\",\n            \"name\": \"<string>\",\n            \"type\": \"webhook\",\n            \"description\": \"\"\n          },\n          \"result\": \"<unknown>\",\n          \"status\": 349,\n          \"when\": {},\n          \"error\": false\n        }\n      ],\n      \"real_tools\": [\n        {\n          \"id\": \"<string>\",\n          \"name\": \"<string>\",\n          \"type\": \"webhook\",\n          \"description\": \"\"\n        }\n      ]\n    },\n    \"simulated_user_model\": \"<string>\",\n    \"repeat_count\": 1\n  },\n  \"dynamic_variables\": {}\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

404

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

#### Path Parameters

​

test_id

string

required

#### Body

application/json

​

name

string | null

Required string length: `1 - 200`

​

test_type

enum<string> | null

Available options: 

`next_reply`, 

`tool`, 

`simulation`

​

conversation

AgentTestMessagePayload · object[] | null

Show child attributes

​

expectation

string | null

Maximum string length: `400`

​

success_examples

string[] | null

​

failure_examples

string[] | null

​

referenced_tool

AgentTestReferencedTool · object | null

Tool the runner should (or should not) observe on the next turn. A webhook or client tool is referenced by its library id, an integration tool by "<provider_key>:<tool_name>" (for example "google_calendar:create_event").

Show child attributes

​

tool_parameters

AgentTestToolParameter · object[] | null

Show child attributes

​

verify_absence

boolean | null

​

simulation

AgentTestSimulationConfig · object | null

Show child attributes

​

dynamic_variables

Dynamic Variables · object | null

Show child attributes

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

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/update-test.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/update-test)

[Get Test](https://docs.fish.audio/api-reference/endpoint/agent/get-test)[Delete Test](https://docs.fish.audio/api-reference/endpoint/agent/delete-test)
