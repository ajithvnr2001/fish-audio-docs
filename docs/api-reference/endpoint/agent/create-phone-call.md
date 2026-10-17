---
url: https://docs.fish.audio/api-reference/endpoint/agent/create-phone-call/
title: Create Phone Call - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:04.397796+00:00
---

# Create Phone Call - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/create-phone-call/

Create Phone Call

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/phone-calls \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --header 'Idempotency-Key: <unique-key>' \
      --data '{
        "agent_id": "<agent-id>",
        "phone_number_id": "<phone-number-id>",
        "to_number": "+14155550123"
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/phone-calls"
    
    payload = {
        "agent_id": "<string>",
        "phone_number_id": "<string>",
        "to_number": "<string>",
        "dynamic_variables": {},
        "overrides": {
            "first_message": "<string>",
            "first_message_prompt": "<string>",
            "system_prompt": "<string>",
            "voice_id": "<string>",
            "asr": {}
        },
        "metadata": {},
        "llm_extra_body": {},
        "sip_headers": {}
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
        agent_id: '<string>',
        phone_number_id: '<string>',
        to_number: '<string>',
        dynamic_variables: {},
        overrides: {
          first_message: '<string>',
          first_message_prompt: '<string>',
          system_prompt: '<string>',
          voice_id: '<string>',
          asr: {}
        },
        metadata: {},
        llm_extra_body: {},
        sip_headers: {}
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/phone-calls', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/phone-calls",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'agent_id' => '<string>',
        'phone_number_id' => '<string>',
        'to_number' => '<string>',
        'dynamic_variables' => [
            
        ],
        'overrides' => [
            'first_message' => '<string>',
            'first_message_prompt' => '<string>',
            'system_prompt' => '<string>',
            'voice_id' => '<string>',
            'asr' => [
                    
            ]
        ],
        'metadata' => [
            
        ],
        'llm_extra_body' => [
            
        ],
        'sip_headers' => [
            
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
    
    	url := "https://api.fish.audio/v1/agent/phone-calls"
    
    	payload := strings.NewReader("{\n  \"agent_id\": \"<string>\",\n  \"phone_number_id\": \"<string>\",\n  \"to_number\": \"<string>\",\n  \"dynamic_variables\": {},\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"sip_headers\": {}\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/phone-calls")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"agent_id\": \"<string>\",\n  \"phone_number_id\": \"<string>\",\n  \"to_number\": \"<string>\",\n  \"dynamic_variables\": {},\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"sip_headers\": {}\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/phone-calls")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"agent_id\": \"<string>\",\n  \"phone_number_id\": \"<string>\",\n  \"to_number\": \"<string>\",\n  \"dynamic_variables\": {},\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"sip_headers\": {}\n}"
    
    response = http.request(request)
    puts response.read_body

201

401

402

403

404

409

422

429

502

503
    
    
    {
      "session_id": "<string>",
      "status": "queued"
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

Phone Calls

# Create Phone Call

Copy pageCopy page

Place an outbound call from one of your phone numbers; the agent speaks when the callee answers.

Copy pageCopy page

POST

/

v1

/

agent

/

phone-calls

Try it

Create Phone Call

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/phone-calls \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --header 'Idempotency-Key: <unique-key>' \
      --data '{
        "agent_id": "<agent-id>",
        "phone_number_id": "<phone-number-id>",
        "to_number": "+14155550123"
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/phone-calls"
    
    payload = {
        "agent_id": "<string>",
        "phone_number_id": "<string>",
        "to_number": "<string>",
        "dynamic_variables": {},
        "overrides": {
            "first_message": "<string>",
            "first_message_prompt": "<string>",
            "system_prompt": "<string>",
            "voice_id": "<string>",
            "asr": {}
        },
        "metadata": {},
        "llm_extra_body": {},
        "sip_headers": {}
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
        agent_id: '<string>',
        phone_number_id: '<string>',
        to_number: '<string>',
        dynamic_variables: {},
        overrides: {
          first_message: '<string>',
          first_message_prompt: '<string>',
          system_prompt: '<string>',
          voice_id: '<string>',
          asr: {}
        },
        metadata: {},
        llm_extra_body: {},
        sip_headers: {}
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/phone-calls', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/phone-calls",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'agent_id' => '<string>',
        'phone_number_id' => '<string>',
        'to_number' => '<string>',
        'dynamic_variables' => [
            
        ],
        'overrides' => [
            'first_message' => '<string>',
            'first_message_prompt' => '<string>',
            'system_prompt' => '<string>',
            'voice_id' => '<string>',
            'asr' => [
                    
            ]
        ],
        'metadata' => [
            
        ],
        'llm_extra_body' => [
            
        ],
        'sip_headers' => [
            
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
    
    	url := "https://api.fish.audio/v1/agent/phone-calls"
    
    	payload := strings.NewReader("{\n  \"agent_id\": \"<string>\",\n  \"phone_number_id\": \"<string>\",\n  \"to_number\": \"<string>\",\n  \"dynamic_variables\": {},\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"sip_headers\": {}\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/phone-calls")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"agent_id\": \"<string>\",\n  \"phone_number_id\": \"<string>\",\n  \"to_number\": \"<string>\",\n  \"dynamic_variables\": {},\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"sip_headers\": {}\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/phone-calls")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"agent_id\": \"<string>\",\n  \"phone_number_id\": \"<string>\",\n  \"to_number\": \"<string>\",\n  \"dynamic_variables\": {},\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"sip_headers\": {}\n}"
    
    response = http.request(request)
    puts response.read_body

201

401

402

403

404

409

422

429

502

503
    
    
    {
      "session_id": "<string>",
      "status": "queued"
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

#### Headers

​

idempotency-key

string | null

Retry-safe replay key: the same key with the same body returns the call already placed instead of dialing again (24h window).

#### Body

application/json

POST phone-calls body, shared by the public and console routes.

to_number is deliberately not format-validated here: the contract orders the E.164 check after the agent/published checks, so it runs in the service with a machine-readable reason.

​

agent_id

string

required

​

phone_number_id

string

required

The team-owned number to dial from (twilio provider only).

​

to_number

string

required

Destination in E.164, e.g. +14155550123.

​

dynamic_variables

Dynamic Variables · object | null

Show child attributes

​

overrides

AgentSessionOverridesPayload · object | null

Wire twin of @fishaudio/agent-protocol `SessionOverrides` (session.ts).

Every field must be allow-listed in Agent.overrides_allowed; unauthorized fields fail session creation loudly rather than being silently dropped.

Show child attributes

​

metadata

Metadata · object | null

Show child attributes

​

llm_extra_body

Llm Extra Body · object | null

Show child attributes

​

sip_headers

Sip Headers · object | null

Custom SIP headers for this call's INVITE, imported SIP numbers only. Same rules as the number's termination_headers, and merged over them.

Show child attributes

#### Response

201

application/json

Document created, URL follows

​

session_id

string

required

​

status

string

default:queued

Allowed value: `"queued"`

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/create-phone-call.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/create-phone-call)

[Release Phone Number](https://docs.fish.audio/api-reference/endpoint/agent/release-phone-number)[Overview](https://docs.fish.audio/api-reference/sdk/python/overview)
