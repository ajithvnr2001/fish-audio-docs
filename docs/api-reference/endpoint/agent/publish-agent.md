---
url: https://docs.fish.audio/api-reference/endpoint/agent/publish-agent/
title: Publish Agent - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:13.719620+00:00
---

# Publish Agent - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/agent/publish-agent/

Publish

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/agents/<agent-id>/publish \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{
        "version_title": "Tighter greeting"
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/publish"
    
    payload = {
        "version_title": "<string>",
        "version_description": "<string>"
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
      body: JSON.stringify({version_title: '<string>', version_description: '<string>'})
    };
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}/publish', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}/publish",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'version_title' => '<string>',
        'version_description' => '<string>'
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/publish"
    
    	payload := strings.NewReader("{\n  \"version_title\": \"<string>\",\n  \"version_description\": \"<string>\"\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/agents/{agent_id}/publish")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"version_title\": \"<string>\",\n  \"version_description\": \"<string>\"\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/publish")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"version_title\": \"<string>\",\n  \"version_description\": \"<string>\"\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

404

409

422

503
    
    
    {
      "version_number": 123,
      "config_hash": "<string>",
      "published_at": "2023-11-07T05:31:56Z",
      "version_title": "<string>",
      "version_description": "<string>"
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

# Publish Agent

Copy pageCopy page

Freeze the current draft into an immutable version (version_number auto-increments) and make it the live configuration for new sessions.

Copy pageCopy page

POST

/

v1

/

agent

/

agents

/

{agent_id}

/

publish

Try it

Publish

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/agent/agents/<agent-id>/publish \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --data '{
        "version_title": "Tighter greeting"
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/agent/agents/{agent_id}/publish"
    
    payload = {
        "version_title": "<string>",
        "version_description": "<string>"
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
      body: JSON.stringify({version_title: '<string>', version_description: '<string>'})
    };
    
    fetch('https://api.fish.audio/v1/agent/agents/{agent_id}/publish', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/agent/agents/{agent_id}/publish",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'version_title' => '<string>',
        'version_description' => '<string>'
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
    
    	url := "https://api.fish.audio/v1/agent/agents/{agent_id}/publish"
    
    	payload := strings.NewReader("{\n  \"version_title\": \"<string>\",\n  \"version_description\": \"<string>\"\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/agent/agents/{agent_id}/publish")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"version_title\": \"<string>\",\n  \"version_description\": \"<string>\"\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/agent/agents/{agent_id}/publish")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"version_title\": \"<string>\",\n  \"version_description\": \"<string>\"\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

404

409

422

503
    
    
    {
      "version_number": 123,
      "config_hash": "<string>",
      "published_at": "2023-11-07T05:31:56Z",
      "version_title": "<string>",
      "version_description": "<string>"
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

version_title

string

Optional label shown in the version history.

Maximum string length: `120`

​

version_description

string

Optional longer note for audit and rollback context.

Maximum string length: `2000`

#### Response

200

application/json

Request fulfilled, document follows

​

version_number

integer

required

​

config_hash

string

required

​

published_at

string<date-time>

required

​

version_title

string | null

​

version_description

string | null

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/agent/publish-agent.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/agent/publish-agent)

[Update Draft Config](https://docs.fish.audio/api-reference/endpoint/agent/update-draft-config)[List Agent Versions](https://docs.fish.audio/api-reference/endpoint/agent/list-agent-versions)
