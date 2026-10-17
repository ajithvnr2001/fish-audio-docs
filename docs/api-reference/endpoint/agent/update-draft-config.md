---
url: https://docs.fish.audio/api-reference/endpoint/agent/update-draft-config/
title: Update Draft Config - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:15.694588+00:00
---

# Update Draft Config - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/update-draft-config/

Update Draft Config

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/v1/agent/agents/<agent-id>/config \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{
        "prompt": {
          "system_prompt": "You are the receptionist for Fish Dental."
        },
        "webhooks": {
          "post_call": [
            {
              "url": "https://example.com/hooks/fish",
              "secret": "<signing-secret>"
            }
          ]
        }
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/config"
    
    payload = {
        "prompt": {
            "system_prompt": "<string>",
            "first_message": "<string>",
            "first_message_prompt": "<string>"
        },
        "voice": {
            "voice_id": "<string>",
            "expressive": True,
            "speed": 1.25,
            "pronunciation_dictionary_ids": ["<string>"]
        },
        "asr": {
            "multilingual": True,
            "strict_language": True,
            "keyterms": ["<string>"]
        },
        "conversation": {
            "max_duration_seconds": 1830,
            "response_wait_ms": 1150,
            "response_max_wait_ms": 2000,
            "interruptible": True,
            "interruption_ignore_phrases": ["<string>"],
            "speculative_response": True,
            "reengage_enabled": True,
            "hangup_after_seconds": 1805,
            "hangup_farewell_enabled": True,
            "record_audio": True,
            "timezone": "<string>",
            "transfer_destinations": [
                {
                    "type": "phone",
                    "label": "",
                    "phone_number": "<string>",
                    "sip_uri": "<string>",
                    "description": "",
                    "mode": "cold",
                    "warm_connect": "confirm",
                    "warm_briefing_instructions": "",
                    "warm_ring_timeout_seconds": 30,
                    "warm_confirm_timeout_seconds": 60,
                    "warm_human_detection": False,
                    "on_failure": {
                        "action": "return_to_agent",
                        "message": ""
                    },
                    "announcement_mode": "generated",
                    "announcement_message": ""
                }
            ],
            "transfer_refuse_questions": True,
            "outbound": {
                "amd_enabled": True,
                "voicemail": {
                    "action": "hangup",
                    "message": ""
                }
            },
            "keypad_menu": {
                "enabled": False,
                "prompt": "",
                "options": [],
                "accept_speech": True,
                "variable": "menu_choice",
                "no_input_timeout_seconds": 5,
                "max_attempts": 2,
                "retry_message": "",
                "fallback_value": ""
            },
            "keypad_input": {
                "enabled": False,
                "terminator": "#",
                "inter_digit_timeout_seconds": 2
            }
        },
        "tools": {
            "enabled": True,
            "tool_ids": ["<string>"],
            "system_tools": {
                "hang_up_call": True,
                "hang_up_call_farewell_message": "<string>",
                "hang_up_call_refuse_questions": True
            }
        },
        "webhooks": {
            "conversation_init": {
                "url": "<string>",
                "secret": "<string>",
                "timeout_seconds": 5
            },
            "post_call": [
                {
                    "url": "<string>",
                    "secret": "<string>"
                }
            ]
        },
        "knowledge_base": {
            "enabled": True,
            "knowledge_source_ids": ["<string>"]
        },
        "analysis": {
            "summary": {
                "enabled": True,
                "prompt": "<string>",
                "language": "en"
            },
            "data_fields": [
                {
                    "name": "<string>",
                    "type": "text",
                    "description": "",
                    "enum_options": ["<string>"]
                }
            ],
            "criteria": [
                {
                    "name": "<string>",
                    "description": ""
                }
            ]
        },
        "guardrails": {
            "focus": True,
            "manipulation": True
        },
        "llm": { "custom": {
                "base_url": "<string>",
                "model": "<string>",
                "api_key": "<string>"
            } },
        "variables": { "defaults": {} }
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
        prompt: {
          system_prompt: '<string>',
          first_message: '<string>',
          first_message_prompt: '<string>'
        },
        voice: {
          voice_id: '<string>',
          expressive: true,
          speed: 1.25,
          pronunciation_dictionary_ids: ['<string>']
        },
        asr: {multilingual: true, strict_language: true, keyterms: ['<string>']},
        conversation: {
          max_duration_seconds: 1830,
          response_wait_ms: 1150,
          response_max_wait_ms: 2000,
          interruptible: true,
          interruption_ignore_phrases: ['<string>'],
          speculative_response: true,
          reengage_enabled: true,
          hangup_after_seconds: 1805,
          hangup_farewell_enabled: true,
          record_audio: true,
          timezone: '<string>',
          transfer_destinations: [
            {
              type: 'phone',
              label: '',
              phone_number: '<string>',
              sip_uri: '<string>',
              description: '',
              mode: 'cold',
              warm_connect: 'confirm',
              warm_briefing_instructions: '',
              warm_ring_timeout_seconds: 30,
              warm_confirm_timeout_seconds: 60,
              warm_human_detection: false,
              on_failure: {action: 'return_to_agent', message: ''},
              announcement_mode: 'generated',
              announcement_message: ''
            }
          ],
          transfer_refuse_questions: true,
          outbound: {amd_enabled: true, voicemail: {action: 'hangup', message: ''}},
          keypad_menu: {
            enabled: false,
            prompt: '',
            options: [],
            accept_speech: true,
            variable: 'menu_choice',
            no_input_timeout_seconds: 5,
            max_attempts: 2,
            retry_message: '',
            fallback_value: ''
          },
          keypad_input: {enabled: false, terminator: '#', inter_digit_timeout_seconds: 2}
        },
        tools: {
          enabled: true,
          tool_ids: ['<string>'],
          system_tools: {
            hang_up_call: true,
            hang_up_call_farewell_message: '<string>',
            hang_up_call_refuse_questions: true
          }
        },
        webhooks: {
          conversation_init: {url: '<string>', secret: '<string>', timeout_seconds: 5},
          post_call: [{url: '<string>', secret: '<string>'}]
        },
        knowledge_base: {enabled: true, knowledge_source_ids: ['<string>']},
        analysis: {
          summary: {enabled: true, prompt: '<string>', language: 'en'},
          data_fields: [{name: '<string>', type: 'text', description: '', enum_options: ['<string>']}],
          criteria: [{name: '<string>', description: ''}]
        },
        guardrails: {focus: true, manipulation: true},
        llm: {custom: {base_url: '<string>', model: '<string>', api_key: '<string>'}},
        variables: {defaults: {}}
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}/config', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}/config",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'prompt' => [
            'system_prompt' => '<string>',
            'first_message' => '<string>',
            'first_message_prompt' => '<string>'
        ],
        'voice' => [
            'voice_id' => '<string>',
            'expressive' => true,
            'speed' => 1.25,
            'pronunciation_dictionary_ids' => [
                    '<string>'
            ]
        ],
        'asr' => [
            'multilingual' => true,
            'strict_language' => true,
            'keyterms' => [
                    '<string>'
            ]
        ],
        'conversation' => [
            'max_duration_seconds' => 1830,
            'response_wait_ms' => 1150,
            'response_max_wait_ms' => 2000,
            'interruptible' => true,
            'interruption_ignore_phrases' => [
                    '<string>'
            ],
            'speculative_response' => true,
            'reengage_enabled' => true,
            'hangup_after_seconds' => 1805,
            'hangup_farewell_enabled' => true,
            'record_audio' => true,
            'timezone' => '<string>',
            'transfer_destinations' => [
                    [
                                    'type' => 'phone',
                                    'label' => '',
                                    'phone_number' => '<string>',
                                    'sip_uri' => '<string>',
                                    'description' => '',
                                    'mode' => 'cold',
                                    'warm_connect' => 'confirm',
                                    'warm_briefing_instructions' => '',
                                    'warm_ring_timeout_seconds' => 30,
                                    'warm_confirm_timeout_seconds' => 60,
                                    'warm_human_detection' => false,
                                    'on_failure' => [
                                                                    'action' => 'return_to_agent',
                                                                    'message' => ''
                                    ],
                                    'announcement_mode' => 'generated',
                                    'announcement_message' => ''
                    ]
            ],
            'transfer_refuse_questions' => true,
            'outbound' => [
                    'amd_enabled' => true,
                    'voicemail' => [
                                    'action' => 'hangup',
                                    'message' => ''
                    ]
            ],
            'keypad_menu' => [
                    'enabled' => false,
                    'prompt' => '',
                    'options' => [
                                    
                    ],
                    'accept_speech' => true,
                    'variable' => 'menu_choice',
                    'no_input_timeout_seconds' => 5,
                    'max_attempts' => 2,
                    'retry_message' => '',
                    'fallback_value' => ''
            ],
            'keypad_input' => [
                    'enabled' => false,
                    'terminator' => '#',
                    'inter_digit_timeout_seconds' => 2
            ]
        ],
        'tools' => [
            'enabled' => true,
            'tool_ids' => [
                    '<string>'
            ],
            'system_tools' => [
                    'hang_up_call' => true,
                    'hang_up_call_farewell_message' => '<string>',
                    'hang_up_call_refuse_questions' => true
            ]
        ],
        'webhooks' => [
            'conversation_init' => [
                    'url' => '<string>',
                    'secret' => '<string>',
                    'timeout_seconds' => 5
            ],
            'post_call' => [
                    [
                                    'url' => '<string>',
                                    'secret' => '<string>'
                    ]
            ]
        ],
        'knowledge_base' => [
            'enabled' => true,
            'knowledge_source_ids' => [
                    '<string>'
            ]
        ],
        'analysis' => [
            'summary' => [
                    'enabled' => true,
                    'prompt' => '<string>',
                    'language' => 'en'
            ],
            'data_fields' => [
                    [
                                    'name' => '<string>',
                                    'type' => 'text',
                                    'description' => '',
                                    'enum_options' => [
                                                                    '<string>'
                                    ]
                    ]
            ],
            'criteria' => [
                    [
                                    'name' => '<string>',
                                    'description' => ''
                    ]
            ]
        ],
        'guardrails' => [
            'focus' => true,
            'manipulation' => true
        ],
        'llm' => [
            'custom' => [
                    'base_url' => '<string>',
                    'model' => '<string>',
                    'api_key' => '<string>'
            ]
        ],
        'variables' => [
            'defaults' => [
                    
            ]
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/config"
    
    	payload := strings.NewReader("{\n  \"prompt\": {\n    \"system_prompt\": \"<string>\",\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\"\n  },\n  \"voice\": {\n    \"voice_id\": \"<string>\",\n    \"expressive\": true,\n    \"speed\": 1.25,\n    \"pronunciation_dictionary_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"asr\": {\n    \"multilingual\": true,\n    \"strict_language\": true,\n    \"keyterms\": [\n      \"<string>\"\n    ]\n  },\n  \"conversation\": {\n    \"max_duration_seconds\": 1830,\n    \"response_wait_ms\": 1150,\n    \"response_max_wait_ms\": 2000,\n    \"interruptible\": true,\n    \"interruption_ignore_phrases\": [\n      \"<string>\"\n    ],\n    \"speculative_response\": true,\n    \"reengage_enabled\": true,\n    \"hangup_after_seconds\": 1805,\n    \"hangup_farewell_enabled\": true,\n    \"record_audio\": true,\n    \"timezone\": \"<string>\",\n    \"transfer_destinations\": [\n      {\n        \"type\": \"phone\",\n        \"label\": \"\",\n        \"phone_number\": \"<string>\",\n        \"sip_uri\": \"<string>\",\n        \"description\": \"\",\n        \"mode\": \"cold\",\n        \"warm_connect\": \"confirm\",\n        \"warm_briefing_instructions\": \"\",\n        \"warm_ring_timeout_seconds\": 30,\n        \"warm_confirm_timeout_seconds\": 60,\n        \"warm_human_detection\": false,\n        \"on_failure\": {\n          \"action\": \"return_to_agent\",\n          \"message\": \"\"\n        },\n        \"announcement_mode\": \"generated\",\n        \"announcement_message\": \"\"\n      }\n    ],\n    \"transfer_refuse_questions\": true,\n    \"outbound\": {\n      \"amd_enabled\": true,\n      \"voicemail\": {\n        \"action\": \"hangup\",\n        \"message\": \"\"\n      }\n    },\n    \"keypad_menu\": {\n      \"enabled\": false,\n      \"prompt\": \"\",\n      \"options\": [],\n      \"accept_speech\": true,\n      \"variable\": \"menu_choice\",\n      \"no_input_timeout_seconds\": 5,\n      \"max_attempts\": 2,\n      \"retry_message\": \"\",\n      \"fallback_value\": \"\"\n    },\n    \"keypad_input\": {\n      \"enabled\": false,\n      \"terminator\": \"#\",\n      \"inter_digit_timeout_seconds\": 2\n    }\n  },\n  \"tools\": {\n    \"enabled\": true,\n    \"tool_ids\": [\n      \"<string>\"\n    ],\n    \"system_tools\": {\n      \"hang_up_call\": true,\n      \"hang_up_call_farewell_message\": \"<string>\",\n      \"hang_up_call_refuse_questions\": true\n    }\n  },\n  \"webhooks\": {\n    \"conversation_init\": {\n      \"url\": \"<string>\",\n      \"secret\": \"<string>\",\n      \"timeout_seconds\": 5\n    },\n    \"post_call\": [\n      {\n        \"url\": \"<string>\",\n        \"secret\": \"<string>\"\n      }\n    ]\n  },\n  \"knowledge_base\": {\n    \"enabled\": true,\n    \"knowledge_source_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"analysis\": {\n    \"summary\": {\n      \"enabled\": true,\n      \"prompt\": \"<string>\",\n      \"language\": \"en\"\n    },\n    \"data_fields\": [\n      {\n        \"name\": \"<string>\",\n        \"type\": \"text\",\n        \"description\": \"\",\n        \"enum_options\": [\n          \"<string>\"\n        ]\n      }\n    ],\n    \"criteria\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"\"\n      }\n    ]\n  },\n  \"guardrails\": {\n    \"focus\": true,\n    \"manipulation\": true\n  },\n  \"llm\": {\n    \"custom\": {\n      \"base_url\": \"<string>\",\n      \"model\": \"<string>\",\n      \"api_key\": \"<string>\"\n    }\n  },\n  \"variables\": {\n    \"defaults\": {}\n  }\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/v1/agent/agents/{agent_id}/config")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"prompt\": {\n    \"system_prompt\": \"<string>\",\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\"\n  },\n  \"voice\": {\n    \"voice_id\": \"<string>\",\n    \"expressive\": true,\n    \"speed\": 1.25,\n    \"pronunciation_dictionary_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"asr\": {\n    \"multilingual\": true,\n    \"strict_language\": true,\n    \"keyterms\": [\n      \"<string>\"\n    ]\n  },\n  \"conversation\": {\n    \"max_duration_seconds\": 1830,\n    \"response_wait_ms\": 1150,\n    \"response_max_wait_ms\": 2000,\n    \"interruptible\": true,\n    \"interruption_ignore_phrases\": [\n      \"<string>\"\n    ],\n    \"speculative_response\": true,\n    \"reengage_enabled\": true,\n    \"hangup_after_seconds\": 1805,\n    \"hangup_farewell_enabled\": true,\n    \"record_audio\": true,\n    \"timezone\": \"<string>\",\n    \"transfer_destinations\": [\n      {\n        \"type\": \"phone\",\n        \"label\": \"\",\n        \"phone_number\": \"<string>\",\n        \"sip_uri\": \"<string>\",\n        \"description\": \"\",\n        \"mode\": \"cold\",\n        \"warm_connect\": \"confirm\",\n        \"warm_briefing_instructions\": \"\",\n        \"warm_ring_timeout_seconds\": 30,\n        \"warm_confirm_timeout_seconds\": 60,\n        \"warm_human_detection\": false,\n        \"on_failure\": {\n          \"action\": \"return_to_agent\",\n          \"message\": \"\"\n        },\n        \"announcement_mode\": \"generated\",\n        \"announcement_message\": \"\"\n      }\n    ],\n    \"transfer_refuse_questions\": true,\n    \"outbound\": {\n      \"amd_enabled\": true,\n      \"voicemail\": {\n        \"action\": \"hangup\",\n        \"message\": \"\"\n      }\n    },\n    \"keypad_menu\": {\n      \"enabled\": false,\n      \"prompt\": \"\",\n      \"options\": [],\n      \"accept_speech\": true,\n      \"variable\": \"menu_choice\",\n      \"no_input_timeout_seconds\": 5,\n      \"max_attempts\": 2,\n      \"retry_message\": \"\",\n      \"fallback_value\": \"\"\n    },\n    \"keypad_input\": {\n      \"enabled\": false,\n      \"terminator\": \"#\",\n      \"inter_digit_timeout_seconds\": 2\n    }\n  },\n  \"tools\": {\n    \"enabled\": true,\n    \"tool_ids\": [\n      \"<string>\"\n    ],\n    \"system_tools\": {\n      \"hang_up_call\": true,\n      \"hang_up_call_farewell_message\": \"<string>\",\n      \"hang_up_call_refuse_questions\": true\n    }\n  },\n  \"webhooks\": {\n    \"conversation_init\": {\n      \"url\": \"<string>\",\n      \"secret\": \"<string>\",\n      \"timeout_seconds\": 5\n    },\n    \"post_call\": [\n      {\n        \"url\": \"<string>\",\n        \"secret\": \"<string>\"\n      }\n    ]\n  },\n  \"knowledge_base\": {\n    \"enabled\": true,\n    \"knowledge_source_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"analysis\": {\n    \"summary\": {\n      \"enabled\": true,\n      \"prompt\": \"<string>\",\n      \"language\": \"en\"\n    },\n    \"data_fields\": [\n      {\n        \"name\": \"<string>\",\n        \"type\": \"text\",\n        \"description\": \"\",\n        \"enum_options\": [\n          \"<string>\"\n        ]\n      }\n    ],\n    \"criteria\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"\"\n      }\n    ]\n  },\n  \"guardrails\": {\n    \"focus\": true,\n    \"manipulation\": true\n  },\n  \"llm\": {\n    \"custom\": {\n      \"base_url\": \"<string>\",\n      \"model\": \"<string>\",\n      \"api_key\": \"<string>\"\n    }\n  },\n  \"variables\": {\n    \"defaults\": {}\n  }\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/config")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"prompt\": {\n    \"system_prompt\": \"<string>\",\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\"\n  },\n  \"voice\": {\n    \"voice_id\": \"<string>\",\n    \"expressive\": true,\n    \"speed\": 1.25,\n    \"pronunciation_dictionary_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"asr\": {\n    \"multilingual\": true,\n    \"strict_language\": true,\n    \"keyterms\": [\n      \"<string>\"\n    ]\n  },\n  \"conversation\": {\n    \"max_duration_seconds\": 1830,\n    \"response_wait_ms\": 1150,\n    \"response_max_wait_ms\": 2000,\n    \"interruptible\": true,\n    \"interruption_ignore_phrases\": [\n      \"<string>\"\n    ],\n    \"speculative_response\": true,\n    \"reengage_enabled\": true,\n    \"hangup_after_seconds\": 1805,\n    \"hangup_farewell_enabled\": true,\n    \"record_audio\": true,\n    \"timezone\": \"<string>\",\n    \"transfer_destinations\": [\n      {\n        \"type\": \"phone\",\n        \"label\": \"\",\n        \"phone_number\": \"<string>\",\n        \"sip_uri\": \"<string>\",\n        \"description\": \"\",\n        \"mode\": \"cold\",\n        \"warm_connect\": \"confirm\",\n        \"warm_briefing_instructions\": \"\",\n        \"warm_ring_timeout_seconds\": 30,\n        \"warm_confirm_timeout_seconds\": 60,\n        \"warm_human_detection\": false,\n        \"on_failure\": {\n          \"action\": \"return_to_agent\",\n          \"message\": \"\"\n        },\n        \"announcement_mode\": \"generated\",\n        \"announcement_message\": \"\"\n      }\n    ],\n    \"transfer_refuse_questions\": true,\n    \"outbound\": {\n      \"amd_enabled\": true,\n      \"voicemail\": {\n        \"action\": \"hangup\",\n        \"message\": \"\"\n      }\n    },\n    \"keypad_menu\": {\n      \"enabled\": false,\n      \"prompt\": \"\",\n      \"options\": [],\n      \"accept_speech\": true,\n      \"variable\": \"menu_choice\",\n      \"no_input_timeout_seconds\": 5,\n      \"max_attempts\": 2,\n      \"retry_message\": \"\",\n      \"fallback_value\": \"\"\n    },\n    \"keypad_input\": {\n      \"enabled\": false,\n      \"terminator\": \"#\",\n      \"inter_digit_timeout_seconds\": 2\n    }\n  },\n  \"tools\": {\n    \"enabled\": true,\n    \"tool_ids\": [\n      \"<string>\"\n    ],\n    \"system_tools\": {\n      \"hang_up_call\": true,\n      \"hang_up_call_farewell_message\": \"<string>\",\n      \"hang_up_call_refuse_questions\": true\n    }\n  },\n  \"webhooks\": {\n    \"conversation_init\": {\n      \"url\": \"<string>\",\n      \"secret\": \"<string>\",\n      \"timeout_seconds\": 5\n    },\n    \"post_call\": [\n      {\n        \"url\": \"<string>\",\n        \"secret\": \"<string>\"\n      }\n    ]\n  },\n  \"knowledge_base\": {\n    \"enabled\": true,\n    \"knowledge_source_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"analysis\": {\n    \"summary\": {\n      \"enabled\": true,\n      \"prompt\": \"<string>\",\n      \"language\": \"en\"\n    },\n    \"data_fields\": [\n      {\n        \"name\": \"<string>\",\n        \"type\": \"text\",\n        \"description\": \"\",\n        \"enum_options\": [\n          \"<string>\"\n        ]\n      }\n    ],\n    \"criteria\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"\"\n      }\n    ]\n  },\n  \"guardrails\": {\n    \"focus\": true,\n    \"manipulation\": true\n  },\n  \"llm\": {\n    \"custom\": {\n      \"base_url\": \"<string>\",\n      \"model\": \"<string>\",\n      \"api_key\": \"<string>\"\n    }\n  },\n  \"variables\": {\n    \"defaults\": {}\n  }\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

403

404

409

422

503
    
    
    {
      "agent_id": "<string>",
      "config_hash": "<string>",
      "prompt": {
        "system_prompt": "",
        "first_message_mode": "prompt",
        "first_message": "Hi! Thanks for calling — how can I help you today?",
        "first_message_prompt": "Greet the caller and ask what you can help with."
      },
      "voice": {
        "voice_id": "b347db033a6549378b48d00acb0d06cd",
        "speaking_language": "en",
        "expressive": false,
        "speed": 1,
        "tts_model": "s2.1-pro",
        "pronunciation_dictionary_ids": [
          "<string>"
        ]
      },
      "asr": {
        "model": "deepgram:nova-3",
        "multilingual": false,
        "strict_language": false,
        "keyterms": [
          "<string>"
        ]
      },
      "conversation": {
        "max_duration_seconds": 1800,
        "response_wait_ms": 550,
        "eagerness": "balanced",
        "response_max_wait_ms": 123,
        "interruptible": true,
        "interruption_sensitivity": "balanced",
        "interruption_ignore_phrases": [],
        "speculative_response": true,
        "reengage_enabled": false,
        "hangup_after_seconds": 60,
        "hangup_farewell_enabled": false,
        "record_audio": true,
        "timezone": "",
        "transfer_destinations": [],
        "transfer_refuse_questions": true,
        "outbound": {
          "amd_enabled": true,
          "voicemail": {
            "action": "hangup",
            "message": ""
          }
        },
        "keypad_menu": {
          "enabled": false,
          "prompt": "",
          "options": [],
          "accept_speech": true,
          "variable": "menu_choice",
          "no_input_timeout_seconds": 5,
          "max_attempts": 2,
          "retry_message": "",
          "fallback_value": ""
        },
        "keypad_input": {
          "enabled": false,
          "terminator": "#",
          "inter_digit_timeout_seconds": 2
        }
      },
      "tools": {
        "enabled": true,
        "tool_ids": [
          "<string>"
        ],
        "system_tools": {
          "hang_up_call": false,
          "hang_up_call_farewell_mode": "generated",
          "hang_up_call_farewell_message": "",
          "hang_up_call_refuse_questions": false
        }
      },
      "webhooks": {
        "conversation_init": {
          "url": "<string>",
          "has_secret": false,
          "timeout_seconds": 5
        },
        "post_call": [
          {
            "url": "<string>",
            "has_secret": false
          }
        ]
      },
      "knowledge_base": {
        "enabled": false,
        "knowledge_source_ids": [
          "<string>"
        ]
      },
      "analysis": {
        "summary": {
          "enabled": true,
          "prompt": "<string>",
          "language": "en"
        },
        "data_fields": [
          {
            "name": "<string>",
            "type": "text",
            "description": "",
            "enum_options": [
              "<string>"
            ]
          }
        ],
        "criteria": [
          {
            "name": "<string>",
            "description": ""
          }
        ]
      },
      "guardrails": {
        "focus": false,
        "manipulation": false
      },
      "llm": {
        "model": "google/gemini-3.6-flash",
        "custom": {
          "base_url": "<string>",
          "model": "<string>",
          "api_key": null
        }
      },
      "updated_at": "2023-11-07T05:31:56Z",
      "variables": {
        "defaults": {},
        "on_missing": "keep"
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

# Update Draft Config

Copy pageCopy page

Patch the draft configuration section by section; omitted sections keep their value.

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

/

config

Try it

Update Draft Config

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/v1/agent/agents/<agent-id>/config \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{
        "prompt": {
          "system_prompt": "You are the receptionist for Fish Dental."
        },
        "webhooks": {
          "post_call": [
            {
              "url": "https://example.com/hooks/fish",
              "secret": "<signing-secret>"
            }
          ]
        }
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/config"
    
    payload = {
        "prompt": {
            "system_prompt": "<string>",
            "first_message": "<string>",
            "first_message_prompt": "<string>"
        },
        "voice": {
            "voice_id": "<string>",
            "expressive": True,
            "speed": 1.25,
            "pronunciation_dictionary_ids": ["<string>"]
        },
        "asr": {
            "multilingual": True,
            "strict_language": True,
            "keyterms": ["<string>"]
        },
        "conversation": {
            "max_duration_seconds": 1830,
            "response_wait_ms": 1150,
            "response_max_wait_ms": 2000,
            "interruptible": True,
            "interruption_ignore_phrases": ["<string>"],
            "speculative_response": True,
            "reengage_enabled": True,
            "hangup_after_seconds": 1805,
            "hangup_farewell_enabled": True,
            "record_audio": True,
            "timezone": "<string>",
            "transfer_destinations": [
                {
                    "type": "phone",
                    "label": "",
                    "phone_number": "<string>",
                    "sip_uri": "<string>",
                    "description": "",
                    "mode": "cold",
                    "warm_connect": "confirm",
                    "warm_briefing_instructions": "",
                    "warm_ring_timeout_seconds": 30,
                    "warm_confirm_timeout_seconds": 60,
                    "warm_human_detection": False,
                    "on_failure": {
                        "action": "return_to_agent",
                        "message": ""
                    },
                    "announcement_mode": "generated",
                    "announcement_message": ""
                }
            ],
            "transfer_refuse_questions": True,
            "outbound": {
                "amd_enabled": True,
                "voicemail": {
                    "action": "hangup",
                    "message": ""
                }
            },
            "keypad_menu": {
                "enabled": False,
                "prompt": "",
                "options": [],
                "accept_speech": True,
                "variable": "menu_choice",
                "no_input_timeout_seconds": 5,
                "max_attempts": 2,
                "retry_message": "",
                "fallback_value": ""
            },
            "keypad_input": {
                "enabled": False,
                "terminator": "#",
                "inter_digit_timeout_seconds": 2
            }
        },
        "tools": {
            "enabled": True,
            "tool_ids": ["<string>"],
            "system_tools": {
                "hang_up_call": True,
                "hang_up_call_farewell_message": "<string>",
                "hang_up_call_refuse_questions": True
            }
        },
        "webhooks": {
            "conversation_init": {
                "url": "<string>",
                "secret": "<string>",
                "timeout_seconds": 5
            },
            "post_call": [
                {
                    "url": "<string>",
                    "secret": "<string>"
                }
            ]
        },
        "knowledge_base": {
            "enabled": True,
            "knowledge_source_ids": ["<string>"]
        },
        "analysis": {
            "summary": {
                "enabled": True,
                "prompt": "<string>",
                "language": "en"
            },
            "data_fields": [
                {
                    "name": "<string>",
                    "type": "text",
                    "description": "",
                    "enum_options": ["<string>"]
                }
            ],
            "criteria": [
                {
                    "name": "<string>",
                    "description": ""
                }
            ]
        },
        "guardrails": {
            "focus": True,
            "manipulation": True
        },
        "llm": { "custom": {
                "base_url": "<string>",
                "model": "<string>",
                "api_key": "<string>"
            } },
        "variables": { "defaults": {} }
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
        prompt: {
          system_prompt: '<string>',
          first_message: '<string>',
          first_message_prompt: '<string>'
        },
        voice: {
          voice_id: '<string>',
          expressive: true,
          speed: 1.25,
          pronunciation_dictionary_ids: ['<string>']
        },
        asr: {multilingual: true, strict_language: true, keyterms: ['<string>']},
        conversation: {
          max_duration_seconds: 1830,
          response_wait_ms: 1150,
          response_max_wait_ms: 2000,
          interruptible: true,
          interruption_ignore_phrases: ['<string>'],
          speculative_response: true,
          reengage_enabled: true,
          hangup_after_seconds: 1805,
          hangup_farewell_enabled: true,
          record_audio: true,
          timezone: '<string>',
          transfer_destinations: [
            {
              type: 'phone',
              label: '',
              phone_number: '<string>',
              sip_uri: '<string>',
              description: '',
              mode: 'cold',
              warm_connect: 'confirm',
              warm_briefing_instructions: '',
              warm_ring_timeout_seconds: 30,
              warm_confirm_timeout_seconds: 60,
              warm_human_detection: false,
              on_failure: {action: 'return_to_agent', message: ''},
              announcement_mode: 'generated',
              announcement_message: ''
            }
          ],
          transfer_refuse_questions: true,
          outbound: {amd_enabled: true, voicemail: {action: 'hangup', message: ''}},
          keypad_menu: {
            enabled: false,
            prompt: '',
            options: [],
            accept_speech: true,
            variable: 'menu_choice',
            no_input_timeout_seconds: 5,
            max_attempts: 2,
            retry_message: '',
            fallback_value: ''
          },
          keypad_input: {enabled: false, terminator: '#', inter_digit_timeout_seconds: 2}
        },
        tools: {
          enabled: true,
          tool_ids: ['<string>'],
          system_tools: {
            hang_up_call: true,
            hang_up_call_farewell_message: '<string>',
            hang_up_call_refuse_questions: true
          }
        },
        webhooks: {
          conversation_init: {url: '<string>', secret: '<string>', timeout_seconds: 5},
          post_call: [{url: '<string>', secret: '<string>'}]
        },
        knowledge_base: {enabled: true, knowledge_source_ids: ['<string>']},
        analysis: {
          summary: {enabled: true, prompt: '<string>', language: 'en'},
          data_fields: [{name: '<string>', type: 'text', description: '', enum_options: ['<string>']}],
          criteria: [{name: '<string>', description: ''}]
        },
        guardrails: {focus: true, manipulation: true},
        llm: {custom: {base_url: '<string>', model: '<string>', api_key: '<string>'}},
        variables: {defaults: {}}
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}/config', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}/config",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'prompt' => [
            'system_prompt' => '<string>',
            'first_message' => '<string>',
            'first_message_prompt' => '<string>'
        ],
        'voice' => [
            'voice_id' => '<string>',
            'expressive' => true,
            'speed' => 1.25,
            'pronunciation_dictionary_ids' => [
                    '<string>'
            ]
        ],
        'asr' => [
            'multilingual' => true,
            'strict_language' => true,
            'keyterms' => [
                    '<string>'
            ]
        ],
        'conversation' => [
            'max_duration_seconds' => 1830,
            'response_wait_ms' => 1150,
            'response_max_wait_ms' => 2000,
            'interruptible' => true,
            'interruption_ignore_phrases' => [
                    '<string>'
            ],
            'speculative_response' => true,
            'reengage_enabled' => true,
            'hangup_after_seconds' => 1805,
            'hangup_farewell_enabled' => true,
            'record_audio' => true,
            'timezone' => '<string>',
            'transfer_destinations' => [
                    [
                                    'type' => 'phone',
                                    'label' => '',
                                    'phone_number' => '<string>',
                                    'sip_uri' => '<string>',
                                    'description' => '',
                                    'mode' => 'cold',
                                    'warm_connect' => 'confirm',
                                    'warm_briefing_instructions' => '',
                                    'warm_ring_timeout_seconds' => 30,
                                    'warm_confirm_timeout_seconds' => 60,
                                    'warm_human_detection' => false,
                                    'on_failure' => [
                                                                    'action' => 'return_to_agent',
                                                                    'message' => ''
                                    ],
                                    'announcement_mode' => 'generated',
                                    'announcement_message' => ''
                    ]
            ],
            'transfer_refuse_questions' => true,
            'outbound' => [
                    'amd_enabled' => true,
                    'voicemail' => [
                                    'action' => 'hangup',
                                    'message' => ''
                    ]
            ],
            'keypad_menu' => [
                    'enabled' => false,
                    'prompt' => '',
                    'options' => [
                                    
                    ],
                    'accept_speech' => true,
                    'variable' => 'menu_choice',
                    'no_input_timeout_seconds' => 5,
                    'max_attempts' => 2,
                    'retry_message' => '',
                    'fallback_value' => ''
            ],
            'keypad_input' => [
                    'enabled' => false,
                    'terminator' => '#',
                    'inter_digit_timeout_seconds' => 2
            ]
        ],
        'tools' => [
            'enabled' => true,
            'tool_ids' => [
                    '<string>'
            ],
            'system_tools' => [
                    'hang_up_call' => true,
                    'hang_up_call_farewell_message' => '<string>',
                    'hang_up_call_refuse_questions' => true
            ]
        ],
        'webhooks' => [
            'conversation_init' => [
                    'url' => '<string>',
                    'secret' => '<string>',
                    'timeout_seconds' => 5
            ],
            'post_call' => [
                    [
                                    'url' => '<string>',
                                    'secret' => '<string>'
                    ]
            ]
        ],
        'knowledge_base' => [
            'enabled' => true,
            'knowledge_source_ids' => [
                    '<string>'
            ]
        ],
        'analysis' => [
            'summary' => [
                    'enabled' => true,
                    'prompt' => '<string>',
                    'language' => 'en'
            ],
            'data_fields' => [
                    [
                                    'name' => '<string>',
                                    'type' => 'text',
                                    'description' => '',
                                    'enum_options' => [
                                                                    '<string>'
                                    ]
                    ]
            ],
            'criteria' => [
                    [
                                    'name' => '<string>',
                                    'description' => ''
                    ]
            ]
        ],
        'guardrails' => [
            'focus' => true,
            'manipulation' => true
        ],
        'llm' => [
            'custom' => [
                    'base_url' => '<string>',
                    'model' => '<string>',
                    'api_key' => '<string>'
            ]
        ],
        'variables' => [
            'defaults' => [
                    
            ]
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/config"
    
    	payload := strings.NewReader("{\n  \"prompt\": {\n    \"system_prompt\": \"<string>\",\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\"\n  },\n  \"voice\": {\n    \"voice_id\": \"<string>\",\n    \"expressive\": true,\n    \"speed\": 1.25,\n    \"pronunciation_dictionary_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"asr\": {\n    \"multilingual\": true,\n    \"strict_language\": true,\n    \"keyterms\": [\n      \"<string>\"\n    ]\n  },\n  \"conversation\": {\n    \"max_duration_seconds\": 1830,\n    \"response_wait_ms\": 1150,\n    \"response_max_wait_ms\": 2000,\n    \"interruptible\": true,\n    \"interruption_ignore_phrases\": [\n      \"<string>\"\n    ],\n    \"speculative_response\": true,\n    \"reengage_enabled\": true,\n    \"hangup_after_seconds\": 1805,\n    \"hangup_farewell_enabled\": true,\n    \"record_audio\": true,\n    \"timezone\": \"<string>\",\n    \"transfer_destinations\": [\n      {\n        \"type\": \"phone\",\n        \"label\": \"\",\n        \"phone_number\": \"<string>\",\n        \"sip_uri\": \"<string>\",\n        \"description\": \"\",\n        \"mode\": \"cold\",\n        \"warm_connect\": \"confirm\",\n        \"warm_briefing_instructions\": \"\",\n        \"warm_ring_timeout_seconds\": 30,\n        \"warm_confirm_timeout_seconds\": 60,\n        \"warm_human_detection\": false,\n        \"on_failure\": {\n          \"action\": \"return_to_agent\",\n          \"message\": \"\"\n        },\n        \"announcement_mode\": \"generated\",\n        \"announcement_message\": \"\"\n      }\n    ],\n    \"transfer_refuse_questions\": true,\n    \"outbound\": {\n      \"amd_enabled\": true,\n      \"voicemail\": {\n        \"action\": \"hangup\",\n        \"message\": \"\"\n      }\n    },\n    \"keypad_menu\": {\n      \"enabled\": false,\n      \"prompt\": \"\",\n      \"options\": [],\n      \"accept_speech\": true,\n      \"variable\": \"menu_choice\",\n      \"no_input_timeout_seconds\": 5,\n      \"max_attempts\": 2,\n      \"retry_message\": \"\",\n      \"fallback_value\": \"\"\n    },\n    \"keypad_input\": {\n      \"enabled\": false,\n      \"terminator\": \"#\",\n      \"inter_digit_timeout_seconds\": 2\n    }\n  },\n  \"tools\": {\n    \"enabled\": true,\n    \"tool_ids\": [\n      \"<string>\"\n    ],\n    \"system_tools\": {\n      \"hang_up_call\": true,\n      \"hang_up_call_farewell_message\": \"<string>\",\n      \"hang_up_call_refuse_questions\": true\n    }\n  },\n  \"webhooks\": {\n    \"conversation_init\": {\n      \"url\": \"<string>\",\n      \"secret\": \"<string>\",\n      \"timeout_seconds\": 5\n    },\n    \"post_call\": [\n      {\n        \"url\": \"<string>\",\n        \"secret\": \"<string>\"\n      }\n    ]\n  },\n  \"knowledge_base\": {\n    \"enabled\": true,\n    \"knowledge_source_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"analysis\": {\n    \"summary\": {\n      \"enabled\": true,\n      \"prompt\": \"<string>\",\n      \"language\": \"en\"\n    },\n    \"data_fields\": [\n      {\n        \"name\": \"<string>\",\n        \"type\": \"text\",\n        \"description\": \"\",\n        \"enum_options\": [\n          \"<string>\"\n        ]\n      }\n    ],\n    \"criteria\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"\"\n      }\n    ]\n  },\n  \"guardrails\": {\n    \"focus\": true,\n    \"manipulation\": true\n  },\n  \"llm\": {\n    \"custom\": {\n      \"base_url\": \"<string>\",\n      \"model\": \"<string>\",\n      \"api_key\": \"<string>\"\n    }\n  },\n  \"variables\": {\n    \"defaults\": {}\n  }\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/v1/agent/agents/{agent_id}/config")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"prompt\": {\n    \"system_prompt\": \"<string>\",\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\"\n  },\n  \"voice\": {\n    \"voice_id\": \"<string>\",\n    \"expressive\": true,\n    \"speed\": 1.25,\n    \"pronunciation_dictionary_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"asr\": {\n    \"multilingual\": true,\n    \"strict_language\": true,\n    \"keyterms\": [\n      \"<string>\"\n    ]\n  },\n  \"conversation\": {\n    \"max_duration_seconds\": 1830,\n    \"response_wait_ms\": 1150,\n    \"response_max_wait_ms\": 2000,\n    \"interruptible\": true,\n    \"interruption_ignore_phrases\": [\n      \"<string>\"\n    ],\n    \"speculative_response\": true,\n    \"reengage_enabled\": true,\n    \"hangup_after_seconds\": 1805,\n    \"hangup_farewell_enabled\": true,\n    \"record_audio\": true,\n    \"timezone\": \"<string>\",\n    \"transfer_destinations\": [\n      {\n        \"type\": \"phone\",\n        \"label\": \"\",\n        \"phone_number\": \"<string>\",\n        \"sip_uri\": \"<string>\",\n        \"description\": \"\",\n        \"mode\": \"cold\",\n        \"warm_connect\": \"confirm\",\n        \"warm_briefing_instructions\": \"\",\n        \"warm_ring_timeout_seconds\": 30,\n        \"warm_confirm_timeout_seconds\": 60,\n        \"warm_human_detection\": false,\n        \"on_failure\": {\n          \"action\": \"return_to_agent\",\n          \"message\": \"\"\n        },\n        \"announcement_mode\": \"generated\",\n        \"announcement_message\": \"\"\n      }\n    ],\n    \"transfer_refuse_questions\": true,\n    \"outbound\": {\n      \"amd_enabled\": true,\n      \"voicemail\": {\n        \"action\": \"hangup\",\n        \"message\": \"\"\n      }\n    },\n    \"keypad_menu\": {\n      \"enabled\": false,\n      \"prompt\": \"\",\n      \"options\": [],\n      \"accept_speech\": true,\n      \"variable\": \"menu_choice\",\n      \"no_input_timeout_seconds\": 5,\n      \"max_attempts\": 2,\n      \"retry_message\": \"\",\n      \"fallback_value\": \"\"\n    },\n    \"keypad_input\": {\n      \"enabled\": false,\n      \"terminator\": \"#\",\n      \"inter_digit_timeout_seconds\": 2\n    }\n  },\n  \"tools\": {\n    \"enabled\": true,\n    \"tool_ids\": [\n      \"<string>\"\n    ],\n    \"system_tools\": {\n      \"hang_up_call\": true,\n      \"hang_up_call_farewell_message\": \"<string>\",\n      \"hang_up_call_refuse_questions\": true\n    }\n  },\n  \"webhooks\": {\n    \"conversation_init\": {\n      \"url\": \"<string>\",\n      \"secret\": \"<string>\",\n      \"timeout_seconds\": 5\n    },\n    \"post_call\": [\n      {\n        \"url\": \"<string>\",\n        \"secret\": \"<string>\"\n      }\n    ]\n  },\n  \"knowledge_base\": {\n    \"enabled\": true,\n    \"knowledge_source_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"analysis\": {\n    \"summary\": {\n      \"enabled\": true,\n      \"prompt\": \"<string>\",\n      \"language\": \"en\"\n    },\n    \"data_fields\": [\n      {\n        \"name\": \"<string>\",\n        \"type\": \"text\",\n        \"description\": \"\",\n        \"enum_options\": [\n          \"<string>\"\n        ]\n      }\n    ],\n    \"criteria\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"\"\n      }\n    ]\n  },\n  \"guardrails\": {\n    \"focus\": true,\n    \"manipulation\": true\n  },\n  \"llm\": {\n    \"custom\": {\n      \"base_url\": \"<string>\",\n      \"model\": \"<string>\",\n      \"api_key\": \"<string>\"\n    }\n  },\n  \"variables\": {\n    \"defaults\": {}\n  }\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/config")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"prompt\": {\n    \"system_prompt\": \"<string>\",\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\"\n  },\n  \"voice\": {\n    \"voice_id\": \"<string>\",\n    \"expressive\": true,\n    \"speed\": 1.25,\n    \"pronunciation_dictionary_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"asr\": {\n    \"multilingual\": true,\n    \"strict_language\": true,\n    \"keyterms\": [\n      \"<string>\"\n    ]\n  },\n  \"conversation\": {\n    \"max_duration_seconds\": 1830,\n    \"response_wait_ms\": 1150,\n    \"response_max_wait_ms\": 2000,\n    \"interruptible\": true,\n    \"interruption_ignore_phrases\": [\n      \"<string>\"\n    ],\n    \"speculative_response\": true,\n    \"reengage_enabled\": true,\n    \"hangup_after_seconds\": 1805,\n    \"hangup_farewell_enabled\": true,\n    \"record_audio\": true,\n    \"timezone\": \"<string>\",\n    \"transfer_destinations\": [\n      {\n        \"type\": \"phone\",\n        \"label\": \"\",\n        \"phone_number\": \"<string>\",\n        \"sip_uri\": \"<string>\",\n        \"description\": \"\",\n        \"mode\": \"cold\",\n        \"warm_connect\": \"confirm\",\n        \"warm_briefing_instructions\": \"\",\n        \"warm_ring_timeout_seconds\": 30,\n        \"warm_confirm_timeout_seconds\": 60,\n        \"warm_human_detection\": false,\n        \"on_failure\": {\n          \"action\": \"return_to_agent\",\n          \"message\": \"\"\n        },\n        \"announcement_mode\": \"generated\",\n        \"announcement_message\": \"\"\n      }\n    ],\n    \"transfer_refuse_questions\": true,\n    \"outbound\": {\n      \"amd_enabled\": true,\n      \"voicemail\": {\n        \"action\": \"hangup\",\n        \"message\": \"\"\n      }\n    },\n    \"keypad_menu\": {\n      \"enabled\": false,\n      \"prompt\": \"\",\n      \"options\": [],\n      \"accept_speech\": true,\n      \"variable\": \"menu_choice\",\n      \"no_input_timeout_seconds\": 5,\n      \"max_attempts\": 2,\n      \"retry_message\": \"\",\n      \"fallback_value\": \"\"\n    },\n    \"keypad_input\": {\n      \"enabled\": false,\n      \"terminator\": \"#\",\n      \"inter_digit_timeout_seconds\": 2\n    }\n  },\n  \"tools\": {\n    \"enabled\": true,\n    \"tool_ids\": [\n      \"<string>\"\n    ],\n    \"system_tools\": {\n      \"hang_up_call\": true,\n      \"hang_up_call_farewell_message\": \"<string>\",\n      \"hang_up_call_refuse_questions\": true\n    }\n  },\n  \"webhooks\": {\n    \"conversation_init\": {\n      \"url\": \"<string>\",\n      \"secret\": \"<string>\",\n      \"timeout_seconds\": 5\n    },\n    \"post_call\": [\n      {\n        \"url\": \"<string>\",\n        \"secret\": \"<string>\"\n      }\n    ]\n  },\n  \"knowledge_base\": {\n    \"enabled\": true,\n    \"knowledge_source_ids\": [\n      \"<string>\"\n    ]\n  },\n  \"analysis\": {\n    \"summary\": {\n      \"enabled\": true,\n      \"prompt\": \"<string>\",\n      \"language\": \"en\"\n    },\n    \"data_fields\": [\n      {\n        \"name\": \"<string>\",\n        \"type\": \"text\",\n        \"description\": \"\",\n        \"enum_options\": [\n          \"<string>\"\n        ]\n      }\n    ],\n    \"criteria\": [\n      {\n        \"name\": \"<string>\",\n        \"description\": \"\"\n      }\n    ]\n  },\n  \"guardrails\": {\n    \"focus\": true,\n    \"manipulation\": true\n  },\n  \"llm\": {\n    \"custom\": {\n      \"base_url\": \"<string>\",\n      \"model\": \"<string>\",\n      \"api_key\": \"<string>\"\n    }\n  },\n  \"variables\": {\n    \"defaults\": {}\n  }\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

403

404

409

422

503
    
    
    {
      "agent_id": "<string>",
      "config_hash": "<string>",
      "prompt": {
        "system_prompt": "",
        "first_message_mode": "prompt",
        "first_message": "Hi! Thanks for calling — how can I help you today?",
        "first_message_prompt": "Greet the caller and ask what you can help with."
      },
      "voice": {
        "voice_id": "b347db033a6549378b48d00acb0d06cd",
        "speaking_language": "en",
        "expressive": false,
        "speed": 1,
        "tts_model": "s2.1-pro",
        "pronunciation_dictionary_ids": [
          "<string>"
        ]
      },
      "asr": {
        "model": "deepgram:nova-3",
        "multilingual": false,
        "strict_language": false,
        "keyterms": [
          "<string>"
        ]
      },
      "conversation": {
        "max_duration_seconds": 1800,
        "response_wait_ms": 550,
        "eagerness": "balanced",
        "response_max_wait_ms": 123,
        "interruptible": true,
        "interruption_sensitivity": "balanced",
        "interruption_ignore_phrases": [],
        "speculative_response": true,
        "reengage_enabled": false,
        "hangup_after_seconds": 60,
        "hangup_farewell_enabled": false,
        "record_audio": true,
        "timezone": "",
        "transfer_destinations": [],
        "transfer_refuse_questions": true,
        "outbound": {
          "amd_enabled": true,
          "voicemail": {
            "action": "hangup",
            "message": ""
          }
        },
        "keypad_menu": {
          "enabled": false,
          "prompt": "",
          "options": [],
          "accept_speech": true,
          "variable": "menu_choice",
          "no_input_timeout_seconds": 5,
          "max_attempts": 2,
          "retry_message": "",
          "fallback_value": ""
        },
        "keypad_input": {
          "enabled": false,
          "terminator": "#",
          "inter_digit_timeout_seconds": 2
        }
      },
      "tools": {
        "enabled": true,
        "tool_ids": [
          "<string>"
        ],
        "system_tools": {
          "hang_up_call": false,
          "hang_up_call_farewell_mode": "generated",
          "hang_up_call_farewell_message": "",
          "hang_up_call_refuse_questions": false
        }
      },
      "webhooks": {
        "conversation_init": {
          "url": "<string>",
          "has_secret": false,
          "timeout_seconds": 5
        },
        "post_call": [
          {
            "url": "<string>",
            "has_secret": false
          }
        ]
      },
      "knowledge_base": {
        "enabled": false,
        "knowledge_source_ids": [
          "<string>"
        ]
      },
      "analysis": {
        "summary": {
          "enabled": true,
          "prompt": "<string>",
          "language": "en"
        },
        "data_fields": [
          {
            "name": "<string>",
            "type": "text",
            "description": "",
            "enum_options": [
              "<string>"
            ]
          }
        ],
        "criteria": [
          {
            "name": "<string>",
            "description": ""
          }
        ]
      },
      "guardrails": {
        "focus": false,
        "manipulation": false
      },
      "llm": {
        "model": "google/gemini-3.6-flash",
        "custom": {
          "base_url": "<string>",
          "model": "<string>",
          "api_key": null
        }
      },
      "updated_at": "2023-11-07T05:31:56Z",
      "variables": {
        "defaults": {},
        "on_missing": "keep"
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

prompt

PublicAgentPromptPatch · object | null

Show child attributes

​

voice

PublicAgentVoicePatch · object | null

Show child attributes

​

asr

PublicAgentAsrPatch · object | null

Show child attributes

​

conversation

PublicAgentConversationPatch · object | null

Show child attributes

​

tools

PublicAgentToolsPatch · object | null

Show child attributes

​

webhooks

PublicAgentWebhooksPatch · object | null

Show child attributes

​

knowledge_base

PublicAgentKnowledgeBasePatch · object | null

Show child attributes

​

analysis

PublicAgentAnalysisPatch · object | null

Show child attributes

​

guardrails

PublicAgentGuardrailsPatch · object | null

Show child attributes

​

llm

PublicAgentLLMPatch · object | null

Show child attributes

​

variables

PublicAgentVariablesPatch · object | null

Default values for the {{placeholders}} in the configured text, used when the session supplies none (the map replaces as a whole), and on_missing for a placeholder with neither: keep leaves it as written (default), empty renders it as empty text, reject refuses the session.

Show child attributes

#### Response

200

application/json

Request fulfilled, document follows

​

agent_id

string

required

​

config_hash

string

required

Content hash of the draft; equal to a version's config_hash when the draft has no unpublished changes.

​

prompt

AgentPromptConfig · object

required

Show child attributes

​

voice

AgentVoiceConfigView · object

required

Read shape of the voice section. The ASR fields that moved to the asr section stay mirrored here, deprecated, so clients written before the split keep reading them.

Show child attributes

​

asr

PublicAgentAsrConfig · object

required

The asr section as the public API reads it: without the console-only noise cancellation and speaker label switches.

Show child attributes

​

conversation

AgentConversationConfig · object

required

Show child attributes

​

tools

PublicAgentToolsConfig · object

required

Show child attributes

​

webhooks

PublicAgentWebhooksConfig · object

required

Show child attributes

​

knowledge_base

PublicAgentKnowledgeBaseConfig · object

required

Show child attributes

​

analysis

AgentAnalysisConfig · object

required

Show child attributes

​

guardrails

AgentGuardrailsConfig · object

required

Show child attributes

​

llm

AgentLLMConfigRedacted · object

required

Show child attributes

​

updated_at

string<date-time>

required

​

variables

AgentVariablesConfig · object

Defaults for `{{name}}` placeholders and what a placeholder without a value does.

Show child attributes

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/update-draft-config.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/update-draft-config)

[Get Draft Config](https://docs.fish.audio/api-reference/endpoint/agent/get-draft-config)[Publish Agent](https://docs.fish.audio/api-reference/endpoint/agent/publish-agent)
