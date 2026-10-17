---
url: https://docs.fish.audio/api-reference/endpoint/agent/update-phone-number/
title: Update Phone Number - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:17.225676+00:00
---

# Update Phone Number - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/update-phone-number/

Update Phone Number

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id} \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "label": "<string>",
      "agent_id": "<string>",
      "retry_caller_id_sync": false
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}"
    
    payload = {
        "label": "<string>",
        "agent_id": "<string>",
        "retry_caller_id_sync": False
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
      body: JSON.stringify({label: '<string>', agent_id: '<string>', retry_caller_id_sync: false})
    };
    
    fetch('https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'label' => '<string>',
        'agent_id' => '<string>',
        'retry_caller_id_sync' => false
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
    
    	url := "https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}"
    
    	payload := strings.NewReader("{\n  \"label\": \"<string>\",\n  \"agent_id\": \"<string>\",\n  \"retry_caller_id_sync\": false\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"label\": \"<string>\",\n  \"agent_id\": \"<string>\",\n  \"retry_caller_id_sync\": false\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"label\": \"<string>\",\n  \"agent_id\": \"<string>\",\n  \"retry_caller_id_sync\": false\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

404

409

422

503
    
    
    {
      "phone_number_id": "<string>",
      "workspace_id": "<string>",
      "phone_number": "<string>",
      "provider": "livekit",
      "agent_id": "<string>",
      "status": "provisioning",
      "created_at": "2023-11-07T05:31:56Z",
      "updated_at": "2023-11-07T05:31:56Z",
      "label": "",
      "transfer_caller_id": "agent_number",
      "cold_transfer_use_original_caller": true,
      "cold_transfer_use_original_caller_effective": true,
      "caller_id_sync_status": "carrier_managed",
      "caller_id_sync_error": "",
      "status_detail": "",
      "supports_outbound": false,
      "termination_uri": "<string>",
      "inbound_auth_username": "<string>",
      "inbound_allowed_addresses": [
        "<string>"
      ],
      "termination_transport": "<string>",
      "termination_auth_username": "<string>",
      "termination_headers": {}
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

Phone Numbers

# Update Phone Number

Copy pageCopy page

Change the label and/or repoint the number at another agent — the deployment-pipeline move (rebind from the staging agent to the production one).

Copy pageCopy page

PATCH

/

v1

/

agent

/

phone-numbers

/

{phone_number_id}

Try it

Update Phone Number

cURL
    
    
    curl --request PATCH \
      --url https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id} \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "label": "<string>",
      "agent_id": "<string>",
      "retry_caller_id_sync": false
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}"
    
    payload = {
        "label": "<string>",
        "agent_id": "<string>",
        "retry_caller_id_sync": False
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
      body: JSON.stringify({label: '<string>', agent_id: '<string>', retry_caller_id_sync: false})
    };
    
    fetch('https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "PATCH",
      CURLOPT_POSTFIELDS => json_encode([
        'label' => '<string>',
        'agent_id' => '<string>',
        'retry_caller_id_sync' => false
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
    
    	url := "https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}"
    
    	payload := strings.NewReader("{\n  \"label\": \"<string>\",\n  \"agent_id\": \"<string>\",\n  \"retry_caller_id_sync\": false\n}")
    
    	req, _ := http.NewRequest("PATCH", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.patch("https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"label\": \"<string>\",\n  \"agent_id\": \"<string>\",\n  \"retry_caller_id_sync\": false\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Patch.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"label\": \"<string>\",\n  \"agent_id\": \"<string>\",\n  \"retry_caller_id_sync\": false\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

404

409

422

503
    
    
    {
      "phone_number_id": "<string>",
      "workspace_id": "<string>",
      "phone_number": "<string>",
      "provider": "livekit",
      "agent_id": "<string>",
      "status": "provisioning",
      "created_at": "2023-11-07T05:31:56Z",
      "updated_at": "2023-11-07T05:31:56Z",
      "label": "",
      "transfer_caller_id": "agent_number",
      "cold_transfer_use_original_caller": true,
      "cold_transfer_use_original_caller_effective": true,
      "caller_id_sync_status": "carrier_managed",
      "caller_id_sync_error": "",
      "status_detail": "",
      "supports_outbound": false,
      "termination_uri": "<string>",
      "inbound_auth_username": "<string>",
      "inbound_allowed_addresses": [
        "<string>"
      ],
      "termination_transport": "<string>",
      "termination_auth_username": "<string>",
      "termination_headers": {}
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

phone_number_id

string

required

#### Body

application/json

​

label

string | null

Maximum string length: `120`

​

agent_id

string | null

Agent that answers this number's inbound calls. Explicit null unbinds; omit the field to keep the current binding.

​

transfer_caller_id

enum<string> | null

Managed `twilio` numbers only: the caller ID a transfer target sees, `agent_number` (this number) or `original_caller` (the caller's own number). Applies to cold and warm transfers. It is a number setting, not agent config: no publish is needed and agent rollbacks leave it alone. Warm transfers follow it from the next call, cold transfers once `caller_id_sync_status` is `synced`. The deprecated boolean `cold_transfer_use_original_caller` is still accepted in its place.

Available options: 

`agent_number`, 

`original_caller`

​

retry_caller_id_sync

boolean

default:false

Re-apply the current caller ID policy after a failed synchronization.

#### Response

200

application/json

Request fulfilled, document follows

​

phone_number_id

string

required

​

workspace_id

string

required

​

phone_number

string

required

E.164, e.g. +14155550123.

​

provider

enum<string>

required

Available options: 

`livekit`, 

`twilio`, 

`sip`

​

agent_id

string | null

required

Inbound calls route to this agent; unbound numbers ring busy.

​

status

enum<string>

required

Available options: 

`provisioning`, 

`active`, 

`error`, 

`released`

​

created_at

string<date-time>

required

​

updated_at

string<date-time>

required

​

label

string

default:""

​

transfer_caller_id

enum<string> | null

Managed `twilio` numbers: the caller ID a transfer target sees, on cold and warm transfers alike. `agent_number` shows this number, `original_caller` shows the caller's own number (a warm transfer falls back to this number when the caller withholds theirs). `null` for imported `sip` numbers, whose carrier decides.

Available options: 

`agent_number`, 

`original_caller`

​

cold_transfer_use_original_caller

boolean | null

deprecated

Deprecated, read `transfer_caller_id`. True when it is `original_caller`.

​

cold_transfer_use_original_caller_effective

boolean | null

deprecated

Deprecated, read `caller_id_sync_status`. Whether the carrier has confirmed the original caller policy for cold transfers, `null` while unknown.

​

caller_id_sync_status

enum<string>

default:carrier_managed

`synced` once the carrier confirmed the policy, `pending` while it is being applied, `error` when the last attempt failed (send `retry_caller_id_sync`), `carrier_managed` for imported `sip` numbers.

Available options: 

`synced`, 

`pending`, 

`error`, 

`carrier_managed`

​

caller_id_sync_error

string

default:""

Why the last synchronization failed; empty otherwise.

​

status_detail

string

default:""

What failed when status is `error`; empty otherwise.

​

supports_outbound

boolean

default:false

Whether the number can place calls (outbound and warm-transfer consult legs): managed `twilio` always, imported `sip` only when a termination was configured.

​

termination_uri

string | null

Imported `sip` numbers: the customer trunk's termination host.

​

inbound_auth_username

string | null

Imported `sip` numbers: the inbound digest username. Passwords are never echoed.

​

inbound_allowed_addresses

string[]

Imported `sip` numbers: allowed source IPs/CIDRs.

​

termination_transport

string | null

Imported `sip` numbers: termination transport.

​

termination_auth_username

string | null

Imported `sip` numbers: the termination digest username. Passwords are never echoed.

​

termination_headers

Termination Headers · object

Imported `sip` numbers: custom SIP headers added to every outbound INVITE through the termination.

Show child attributes

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/update-phone-number.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/update-phone-number)

[Get Phone Number](https://docs.fish.audio/api-reference/endpoint/agent/get-phone-number)[Release Phone Number](https://docs.fish.audio/api-reference/endpoint/agent/release-phone-number)
