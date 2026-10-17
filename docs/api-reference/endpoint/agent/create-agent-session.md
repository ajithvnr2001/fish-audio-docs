---
url: https://docs.fish.audio/api-reference/endpoint/agent/create-agent-session/
title: Create Agent Session - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:04.766075+00:00
---

# Create Agent Session - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/create-agent-session/

Create Session

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/sessions \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{
        "agent_id": "<agent-id>"
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/sessions"
    
    payload = {
        "agent_id": "<string>",
        "name": "<string>",
        "timezone": "<string>",
        "client_timezone": "<string>",
        "world_context": True,
        "overrides": {
            "first_message": "<string>",
            "first_message_prompt": "<string>",
            "system_prompt": "<string>",
            "voice_id": "<string>",
            "asr": {}
        },
        "dynamic_variables": {},
        "end_user_id": "<string>",
        "metadata": {},
        "llm_extra_body": {},
        "tool_events": True,
        "record_audio": True
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
        name: '<string>',
        timezone: '<string>',
        client_timezone: '<string>',
        world_context: true,
        overrides: {
          first_message: '<string>',
          first_message_prompt: '<string>',
          system_prompt: '<string>',
          voice_id: '<string>',
          asr: {}
        },
        dynamic_variables: {},
        end_user_id: '<string>',
        metadata: {},
        llm_extra_body: {},
        tool_events: true,
        record_audio: true
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/sessions', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/sessions",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'agent_id' => '<string>',
        'name' => '<string>',
        'timezone' => '<string>',
        'client_timezone' => '<string>',
        'world_context' => true,
        'overrides' => [
            'first_message' => '<string>',
            'first_message_prompt' => '<string>',
            'system_prompt' => '<string>',
            'voice_id' => '<string>',
            'asr' => [
                    
            ]
        ],
        'dynamic_variables' => [
            
        ],
        'end_user_id' => '<string>',
        'metadata' => [
            
        ],
        'llm_extra_body' => [
            
        ],
        'tool_events' => true,
        'record_audio' => true
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
    
    	url := "https://api.fish.audio/v1/agent/sessions"
    
    	payload := strings.NewReader("{\n  \"agent_id\": \"<string>\",\n  \"name\": \"<string>\",\n  \"timezone\": \"<string>\",\n  \"client_timezone\": \"<string>\",\n  \"world_context\": true,\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"dynamic_variables\": {},\n  \"end_user_id\": \"<string>\",\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"tool_events\": true,\n  \"record_audio\": true\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/sessions")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"agent_id\": \"<string>\",\n  \"name\": \"<string>\",\n  \"timezone\": \"<string>\",\n  \"client_timezone\": \"<string>\",\n  \"world_context\": true,\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"dynamic_variables\": {},\n  \"end_user_id\": \"<string>\",\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"tool_events\": true,\n  \"record_audio\": true\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/sessions")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"agent_id\": \"<string>\",\n  \"name\": \"<string>\",\n  \"timezone\": \"<string>\",\n  \"client_timezone\": \"<string>\",\n  \"world_context\": true,\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"dynamic_variables\": {},\n  \"end_user_id\": \"<string>\",\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"tool_events\": true,\n  \"record_audio\": true\n}"
    
    response = http.request(request)
    puts response.read_body

201

400

401

402

403

404

409

429

502

503
    
    
    {
      "session_id": "<string>",
      "expires_at": "<string>",
      "max_duration_seconds": 123,
      "transport": "livekit",
      "livekit_url": "<string>",
      "token": "<string>"
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

Sessions

# Create Agent Session

Copy pageCopy page

Start a conversation session with an agent and receive a join token for the session transport (currently LiveKit WebRTC).

Copy pageCopy page

POST

/

v1

/

agent

/

sessions

Try it

Create Session

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/sessions \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{
        "agent_id": "<agent-id>"
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/sessions"
    
    payload = {
        "agent_id": "<string>",
        "name": "<string>",
        "timezone": "<string>",
        "client_timezone": "<string>",
        "world_context": True,
        "overrides": {
            "first_message": "<string>",
            "first_message_prompt": "<string>",
            "system_prompt": "<string>",
            "voice_id": "<string>",
            "asr": {}
        },
        "dynamic_variables": {},
        "end_user_id": "<string>",
        "metadata": {},
        "llm_extra_body": {},
        "tool_events": True,
        "record_audio": True
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
        name: '<string>',
        timezone: '<string>',
        client_timezone: '<string>',
        world_context: true,
        overrides: {
          first_message: '<string>',
          first_message_prompt: '<string>',
          system_prompt: '<string>',
          voice_id: '<string>',
          asr: {}
        },
        dynamic_variables: {},
        end_user_id: '<string>',
        metadata: {},
        llm_extra_body: {},
        tool_events: true,
        record_audio: true
      })
    };
    
    fetch('https://api.fish.audio/v1/agent/sessions', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/sessions",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'agent_id' => '<string>',
        'name' => '<string>',
        'timezone' => '<string>',
        'client_timezone' => '<string>',
        'world_context' => true,
        'overrides' => [
            'first_message' => '<string>',
            'first_message_prompt' => '<string>',
            'system_prompt' => '<string>',
            'voice_id' => '<string>',
            'asr' => [
                    
            ]
        ],
        'dynamic_variables' => [
            
        ],
        'end_user_id' => '<string>',
        'metadata' => [
            
        ],
        'llm_extra_body' => [
            
        ],
        'tool_events' => true,
        'record_audio' => true
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
    
    	url := "https://api.fish.audio/v1/agent/sessions"
    
    	payload := strings.NewReader("{\n  \"agent_id\": \"<string>\",\n  \"name\": \"<string>\",\n  \"timezone\": \"<string>\",\n  \"client_timezone\": \"<string>\",\n  \"world_context\": true,\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"dynamic_variables\": {},\n  \"end_user_id\": \"<string>\",\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"tool_events\": true,\n  \"record_audio\": true\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/sessions")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"agent_id\": \"<string>\",\n  \"name\": \"<string>\",\n  \"timezone\": \"<string>\",\n  \"client_timezone\": \"<string>\",\n  \"world_context\": true,\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"dynamic_variables\": {},\n  \"end_user_id\": \"<string>\",\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"tool_events\": true,\n  \"record_audio\": true\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/sessions")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"agent_id\": \"<string>\",\n  \"name\": \"<string>\",\n  \"timezone\": \"<string>\",\n  \"client_timezone\": \"<string>\",\n  \"world_context\": true,\n  \"overrides\": {\n    \"first_message\": \"<string>\",\n    \"first_message_prompt\": \"<string>\",\n    \"system_prompt\": \"<string>\",\n    \"voice_id\": \"<string>\",\n    \"asr\": {}\n  },\n  \"dynamic_variables\": {},\n  \"end_user_id\": \"<string>\",\n  \"metadata\": {},\n  \"llm_extra_body\": {},\n  \"tool_events\": true,\n  \"record_audio\": true\n}"
    
    response = http.request(request)
    puts response.read_body

201

400

401

402

403

404

409

429

502

503
    
    
    {
      "session_id": "<string>",
      "expires_at": "<string>",
      "max_duration_seconds": 123,
      "transport": "livekit",
      "livekit_url": "<string>",
      "token": "<string>"
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

origin

string | null

#### Body

application/json

​

agent_id

string

required

​

name

string | null

Maximum string length: `128`

​

timezone

string | null

IANA timezone (like `Asia/Tokyo`) for the agent's sense of local date and time in this session. Overrides the agent's configured timezone, which defaults to UTC. Invalid names are rejected with 422.

Maximum string length: `64`

​

client_timezone

string | null

The end user's device timezone as an IANA name (like `Asia/Tokyo`), used as a fallback hint: it applies only when neither `timezone` nor the agent's configured timezone is set, and invalid values are ignored rather than rejected. The Web SDK fills it automatically from the browser for public agents. When your backend creates the session, forward the value from your client.

Maximum string length: `64`

​

world_context

boolean

default:true

​

overrides

AgentSessionOverridesPayload · object | null

Wire twin of @fishaudio/agent-protocol `SessionOverrides` (session.ts).

Every field must be allow-listed in Agent.overrides_allowed; unauthorized fields fail session creation loudly rather than being silently dropped.

Show child attributes

​

dynamic_variables

Dynamic Variables · object | null

Show child attributes

​

end_user_id

string | null

Your identifier for the end user, stored verbatim. Returned on session reads and webhooks, and filterable with `GET /v1/agent/sessions?end_user_id=`.

Maximum string length: `256`

​

metadata

Metadata · object | null

Show child attributes

​

llm_extra_body

Llm Extra Body · object | null

Show child attributes

​

tool_events

boolean

default:true

​

record_audio

boolean | null

#### Response

201

application/json

Document created, URL follows

Wire twin of @fishaudio/agent-protocol `SessionToken` (session.ts); keep in sync.

​

session_id

string

required

​

expires_at

string

required

​

max_duration_seconds

integer

required

​

transport

string

required

Allowed value: `"livekit"`

​

livekit_url

string

required

​

token

string

required

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/create-agent-session.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/create-agent-session)

[Get Widget Config](https://docs.fish.audio/api-reference/endpoint/agent/get-widget-config)[List Agent Sessions](https://docs.fish.audio/api-reference/endpoint/agent/list-agent-sessions)
