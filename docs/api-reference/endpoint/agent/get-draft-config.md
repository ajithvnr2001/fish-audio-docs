---
url: https://docs.fish.audio/api-reference/endpoint/agent/get-draft-config/
title: Get Draft Config - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:08.595481+00:00
---

# Get Draft Config - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/get-draft-config/

Get Draft Config

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/agents/{agent_id}/config \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/config"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/config"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/agents/{agent_id}/config")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/config")
    
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

Agents

# Get Draft Config

Copy pageCopy page

Read the agent’s current draft configuration — the state the next publish will freeze.

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

config

Try it

Get Draft Config

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/agents/{agent_id}/config \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/config"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/config"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/agents/{agent_id}/config")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/config")
    
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

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/get-draft-config.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/get-draft-config)

[Delete Agent](https://docs.fish.audio/api-reference/endpoint/agent/delete-agent)[Update Draft Config](https://docs.fish.audio/api-reference/endpoint/agent/update-draft-config)
