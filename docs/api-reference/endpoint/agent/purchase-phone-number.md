---
url: https://docs.fish.audio/api-reference/endpoint/agent/purchase-phone-number/
title: Purchase Phone Number - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:14.650009+00:00
---

# Purchase Phone Number - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/purchase-phone-number/

Purchase or Import Phone Number

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/phone-numbers \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "provider": "twilio",
      "phone_number": "<string>",
      "label": "",
      "agent_id": "<string>"
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/phone-numbers"
    
    payload = {
        "provider": "twilio",
        "phone_number": "<string>",
        "label": "",
        "agent_id": "<string>"
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
      body: JSON.stringify({provider: 'twilio', phone_number: '<string>', label: '', agent_id: '<string>'})
    };
    
    fetch('https://api.fish.audio/v1/agent/phone-numbers', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/phone-numbers",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'provider' => 'twilio',
        'phone_number' => '<string>',
        'label' => '',
        'agent_id' => '<string>'
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
    
    	url := "https://api.fish.audio/v1/agent/phone-numbers"
    
    	payload := strings.NewReader("{\n  \"provider\": \"twilio\",\n  \"phone_number\": \"<string>\",\n  \"label\": \"\",\n  \"agent_id\": \"<string>\"\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/phone-numbers")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"provider\": \"twilio\",\n  \"phone_number\": \"<string>\",\n  \"label\": \"\",\n  \"agent_id\": \"<string>\"\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/phone-numbers")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"provider\": \"twilio\",\n  \"phone_number\": \"<string>\",\n  \"label\": \"\",\n  \"agent_id\": \"<string>\"\n}"
    
    response = http.request(request)
    puts response.read_body

201

401

402

403

404

409

422

502

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

# Purchase Phone Number

Copy pageCopy page

Buy a number from the inventory.

Copy pageCopy page

POST

/

v1

/

agent

/

phone-numbers

Try it

Purchase or Import Phone Number

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/phone-numbers \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '
    {
      "provider": "twilio",
      "phone_number": "<string>",
      "label": "",
      "agent_id": "<string>"
    }
    '
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/phone-numbers"
    
    payload = {
        "provider": "twilio",
        "phone_number": "<string>",
        "label": "",
        "agent_id": "<string>"
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
      body: JSON.stringify({provider: 'twilio', phone_number: '<string>', label: '', agent_id: '<string>'})
    };
    
    fetch('https://api.fish.audio/v1/agent/phone-numbers', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/phone-numbers",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'provider' => 'twilio',
        'phone_number' => '<string>',
        'label' => '',
        'agent_id' => '<string>'
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
    
    	url := "https://api.fish.audio/v1/agent/phone-numbers"
    
    	payload := strings.NewReader("{\n  \"provider\": \"twilio\",\n  \"phone_number\": \"<string>\",\n  \"label\": \"\",\n  \"agent_id\": \"<string>\"\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/phone-numbers")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"provider\": \"twilio\",\n  \"phone_number\": \"<string>\",\n  \"label\": \"\",\n  \"agent_id\": \"<string>\"\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/phone-numbers")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"provider\": \"twilio\",\n  \"phone_number\": \"<string>\",\n  \"label\": \"\",\n  \"agent_id\": \"<string>\"\n}"
    
    response = http.request(request)
    puts response.read_body

201

401

402

403

404

409

422

502

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

  * PublicPhoneNumberPurchasePayload

  * PublicSipNumberImportPayload




​

provider

string

required

`twilio` buys from the managed inventory (supports call transfer); `sip` imports a number you already own at your carrier; see the `sip` request variant.

Allowed value: `"twilio"`

​

phone_number

string

required

E.164 number from `GET /v1/agent/available-phone-numbers`, e.g. +14155550123.

​

label

string

default:""

Maximum string length: `120`

​

agent_id

string | null

Bind an agent to answer inbound calls right away.

#### Response

201

application/json

Document created, URL follows

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

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/purchase-phone-number.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/purchase-phone-number)

[List Phone Numbers](https://docs.fish.audio/api-reference/endpoint/agent/list-phone-numbers)[Get Phone Number](https://docs.fish.audio/api-reference/endpoint/agent/get-phone-number)
