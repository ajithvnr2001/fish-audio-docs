---
url: https://docs.fish.audio/api-reference/endpoint/agent/list-agent-sessions/
title: List Agent Sessions - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:10.262995+00:00
---

# List Agent Sessions - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/list-agent-sessions/

List Agent Sessions

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/sessions \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/sessions"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
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
    
    	url := "https://api.fish.audio/v1/agent/sessions"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/sessions")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/sessions")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

400

401

503
    
    
    {
      "sessions": [
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
          }
        }
      ],
      "has_more": true,
      "next_cursor": "<string>",
      "total": 123
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

# List Agent Sessions

Copy pageCopy page

List your team’s sessions, newest first.

Copy pageCopy page

GET

/

v1

/

agent

/

sessions

Try it

List Agent Sessions

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/sessions \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/sessions"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
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
    
    	url := "https://api.fish.audio/v1/agent/sessions"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/sessions")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/sessions")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

400

401

503
    
    
    {
      "sessions": [
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
          }
        }
      ],
      "has_more": true,
      "next_cursor": "<string>",
      "total": 123
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

#### Query Parameters

​

agent_id

string | null

​

status

string | null

Comma-separated status filter (pending/active/completed/failed/unknown). Default: every status.

​

end_reason

string | null

Comma-separated end reason filter (user_hangup/agent_hangup/escalated/conversation_timeout/heartbeat_timeout/agent_join_timeout/internal_error/llm_endpoint_failure/room_join_timeout/cancelled/dial_failed).

​

direction

string | null

Filter by call direction (inbound/outbound). Sessions predating the field count as inbound.

​

caller_number

string | null

Exact-match caller E.164 (phone sessions only).

​

sip_call_id

string | null

Exact-match SIP Call-ID of the call's INVITE, for looking up the session behind a carrier CDR entry (phone sessions only).

​

end_user_id

string | null

Exact-match end_user_id set at session creation.

​

created_after

string | null

​

created_before

string | null

​

cursor

string | null

​

page

integer | null

1-based page number (offset pagination). Returns total; mutually exclusive with cursor, which deep scans must use.

Required range: `x >= 1`

​

include_total

boolean

default:false

Also count the filtered set on the cursor path.

​

page_size

integer

default:30

Required range: `1 <= x <= 100`

#### Response

200

application/json

Request fulfilled, document follows

​

sessions

AgentSessionSummary · object[]

required

Show child attributes

​

has_more

boolean

required

​

next_cursor

string | null

​

total

integer | null

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/list-agent-sessions.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/list-agent-sessions)

[Create Agent Session](https://docs.fish.audio/api-reference/endpoint/agent/create-agent-session)[Get Agent Session](https://docs.fish.audio/api-reference/endpoint/agent/get-agent-session)
