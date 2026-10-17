---
url: https://docs.fish.audio/api-reference/endpoint/wallet/get-user-package/
title: Get User Package - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:22.285490+00:00
---

# Get User Package - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/wallet/get-user-package/

Get User Package

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/wallet/{user_id}/package \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/wallet/{user_id}/package"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/wallet/{user_id}/package', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/wallet/{user_id}/package",
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
    
    	url := "https://api.fish.audio/wallet/{user_id}/package"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/wallet/{user_id}/package")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/wallet/{user_id}/package")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

401

503
    
    
    {
      "user_id": "<string>",
      "type": "<string>",
      "total": 123,
      "balance": 123,
      "created_at": "2023-11-07T05:31:56Z",
      "updated_at": "2023-11-07T05:31:56Z",
      "finished_at": "2023-11-07T05:31:56Z",
      "stripe_subscription_id": "<string>",
      "stripe_price_id": "<string>",
      "billing_period": "<string>",
      "current_period_end": "2023-11-07T05:31:56Z",
      "cancel_at_period_end": true,
      "cancel_at": "2023-11-07T05:31:56Z",
      "scheduled_change": {},
      "last_synced_at": "2023-11-07T05:31:56Z",
      "subscription_currency": "<string>",
      "subscription_status": "<string>",
      "extra_balance": 0,
      "has_used_trial": false
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

Wallet

# Get User Package

Copy pageCopy page

Get current user premium information

Copy pageCopy page

GET

/

wallet

/

{user_id}

/

package

Try it

Get User Package

cURL
    
    
    curl --request GET \
      --url https://api.fish.audio/wallet/{user_id}/package \
      --header 'Authorization: Bearer <token>'
    
    
    import requests
    
    url = "https://api.fish.audio/wallet/{user_id}/package"
    
    headers = {"Authorization": "Bearer <token>"}
    
    response = requests.get(url, headers=headers)
    
    print(response.text)
    
    
    const options = {method: 'GET', headers: {Authorization: 'Bearer <token>'}};
    
    fetch('https://api.fish.audio/wallet/{user_id}/package', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/wallet/{user_id}/package",
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
    
    	url := "https://api.fish.audio/wallet/{user_id}/package"
    
    	req, _ := http.NewRequest("GET", url, nil)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.get("https://api.fish.audio/wallet/{user_id}/package")
      .header("Authorization", "Bearer <token>")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/wallet/{user_id}/package")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Get.new(url)
    request["Authorization"] = 'Bearer <token>'
    
    response = http.request(request)
    puts response.read_body

200

401

503
    
    
    {
      "user_id": "<string>",
      "type": "<string>",
      "total": 123,
      "balance": 123,
      "created_at": "2023-11-07T05:31:56Z",
      "updated_at": "2023-11-07T05:31:56Z",
      "finished_at": "2023-11-07T05:31:56Z",
      "stripe_subscription_id": "<string>",
      "stripe_price_id": "<string>",
      "billing_period": "<string>",
      "current_period_end": "2023-11-07T05:31:56Z",
      "cancel_at_period_end": true,
      "cancel_at": "2023-11-07T05:31:56Z",
      "scheduled_change": {},
      "last_synced_at": "2023-11-07T05:31:56Z",
      "subscription_currency": "<string>",
      "subscription_status": "<string>",
      "extra_balance": 0,
      "has_used_trial": false
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

user_id

string

default:self

User ID or 'self'

#### Response

200

application/json

Request fulfilled, document follows

​

user_id

string

required

​

type

string

required

​

total

integer

required

​

balance

integer

required

​

created_at

string<date-time>

required

​

updated_at

string<date-time>

required

​

finished_at

string<date-time>

required

​

stripe_subscription_id

string | null

​

stripe_price_id

string | null

​

billing_period

string | null

​

current_period_end

string<date-time> | null

​

cancel_at_period_end

boolean | null

​

cancel_at

string<date-time> | null

​

scheduled_change

Scheduled Change · object | null

​

last_synced_at

string<date-time> | null

​

subscription_currency

string | null

​

subscription_status

string | null

​

extra_balance

integer | null

default:0

​

has_used_trial

boolean

default:false

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/wallet/get-user-package.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/wallet/get-user-package)

[Get API Credit](https://docs.fish.audio/api-reference/endpoint/wallet/get-api-credit)[List Models](https://docs.fish.audio/api-reference/endpoint/model/list-models)
