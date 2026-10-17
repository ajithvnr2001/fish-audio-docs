---
url: https://docs.fish.audio/api-reference/endpoint/agent/get-phone-number/
title: Get Phone Number - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:09.223807+00:00
---

# Get Phone Number - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/get-phone-number/

Get Phone Number

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id} \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
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
    
    	url := "https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}")
    
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

Phone Numbers

# Get Phone Number

Copy pageCopy page

Fetch one phone number, including its current agent binding and provisioning status.

Copy pageCopy page

GET

/

v1

/

agent

/

phone-numbers

/

{phone_number_id}

Try it

Get Phone Number

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id} \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
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
    
    	url := "https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/phone-numbers/{phone_number_id}")
    
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

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/get-phone-number.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/get-phone-number)

[Purchase Phone Number](https://docs.fish.audio/api-reference/endpoint/agent/purchase-phone-number)[Update Phone Number](https://docs.fish.audio/api-reference/endpoint/agent/update-phone-number)
