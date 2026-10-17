---
url: https://docs.fish.audio/api-reference/endpoint/openapi-v1/voice-design/
title: Voice Design - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:22.096643+00:00
---

# Voice Design - Fish Audio

> Source: https://docs.fish.audio/api-reference/endpoint/openapi-v1/voice-design/

Voice Design

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/voice-design \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --header 'model: voice-design-1' \
      --data '{
        "instruction": "Warm, confident studio narrator with a natural tone",
        "reference_text": "Welcome to Fish Audio.",
        "language": "en",
        "n": 2,
        "speed": 1,
        "num_step": 32,
        "guidance_scale": 2,
        "instruct_guidance_scale": 0,
        "seed": 42
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/voice-design"
    
    payload = {
        "guidance_scale": 2,
        "instruct_guidance_scale": 0,
        "instruction": "Warm, confident studio narrator with a natural tone",
        "language": "en",
        "n": 2,
        "num_step": 32,
        "reference_text": "Welcome to Fish Audio.",
        "seed": 42,
        "speed": 1
    }
    headers = {
        "model": "<model>",
        "Authorization": "Bearer <token>",
        "Content-Type": "application/json"
    }
    
    response = requests.post(url, json=payload, headers=headers)
    
    print(response.text)
    
    
    const options = {
      method: 'POST',
      headers: {
        model: '<model>',
        Authorization: 'Bearer <token>',
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        guidance_scale: 2,
        instruct_guidance_scale: 0,
        instruction: 'Warm, confident studio narrator with a natural tone',
        language: 'en',
        n: 2,
        num_step: 32,
        reference_text: 'Welcome to Fish Audio.',
        seed: 42,
        speed: 1
      })
    };
    
    fetch('https://api.fish.audio/v1/voice-design', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/voice-design",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'guidance_scale' => 2,
        'instruct_guidance_scale' => 0,
        'instruction' => 'Warm, confident studio narrator with a natural tone',
        'language' => 'en',
        'n' => 2,
        'num_step' => 32,
        'reference_text' => 'Welcome to Fish Audio.',
        'seed' => 42,
        'speed' => 1
      ]),
      CURLOPT_HTTPHEADER => [
        "Authorization: Bearer <token>",
        "Content-Type: application/json",
        "model: <model>"
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
    
    	url := "https://api.fish.audio/v1/voice-design"
    
    	payload := strings.NewReader("{\n  \"guidance_scale\": 2,\n  \"instruct_guidance_scale\": 0,\n  \"instruction\": \"Warm, confident studio narrator with a natural tone\",\n  \"language\": \"en\",\n  \"n\": 2,\n  \"num_step\": 32,\n  \"reference_text\": \"Welcome to Fish Audio.\",\n  \"seed\": 42,\n  \"speed\": 1\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("model", "<model>")
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/voice-design")
      .header("model", "<model>")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"guidance_scale\": 2,\n  \"instruct_guidance_scale\": 0,\n  \"instruction\": \"Warm, confident studio narrator with a natural tone\",\n  \"language\": \"en\",\n  \"n\": 2,\n  \"num_step\": 32,\n  \"reference_text\": \"Welcome to Fish Audio.\",\n  \"seed\": 42,\n  \"speed\": 1\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/voice-design")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["model"] = '<model>'
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"guidance_scale\": 2,\n  \"instruct_guidance_scale\": 0,\n  \"instruction\": \"Warm, confident studio narrator with a natural tone\",\n  \"language\": \"en\",\n  \"n\": 2,\n  \"num_step\": 32,\n  \"reference_text\": \"Welcome to Fish Audio.\",\n  \"seed\": 42,\n  \"speed\": 1\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

402

503
    
    
    {
      "candidates": [
        {
          "id": "<string>",
          "index": 1,
          "audio_base64": "<string>",
          "sample_rate": 123,
          "duration_ms": 1,
          "text": "<string>",
          "instruct": "<string>",
          "language": "<string>"
        }
      ]
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

Voice Design

# Voice Design

Copy pageCopy page

Generate candidate voices from a prompt

Copy pageCopy page

POST

/

v1

/

voice-design

Try it

Voice Design

cURL
    
    
    curl --request POST \
      --url https://api.fish.audio/v1/voice-design \
      --header 'Authorization: Bearer <token>' \
      --header 'Content-Type: application/json' \
      --header 'model: voice-design-1' \
      --data '{
        "instruction": "Warm, confident studio narrator with a natural tone",
        "reference_text": "Welcome to Fish Audio.",
        "language": "en",
        "n": 2,
        "speed": 1,
        "num_step": 32,
        "guidance_scale": 2,
        "instruct_guidance_scale": 0,
        "seed": 42
      }'
    
    
    import requests
    
    url = "https://api.fish.audio/v1/voice-design"
    
    payload = {
        "guidance_scale": 2,
        "instruct_guidance_scale": 0,
        "instruction": "Warm, confident studio narrator with a natural tone",
        "language": "en",
        "n": 2,
        "num_step": 32,
        "reference_text": "Welcome to Fish Audio.",
        "seed": 42,
        "speed": 1
    }
    headers = {
        "model": "<model>",
        "Authorization": "Bearer <token>",
        "Content-Type": "application/json"
    }
    
    response = requests.post(url, json=payload, headers=headers)
    
    print(response.text)
    
    
    const options = {
      method: 'POST',
      headers: {
        model: '<model>',
        Authorization: 'Bearer <token>',
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        guidance_scale: 2,
        instruct_guidance_scale: 0,
        instruction: 'Warm, confident studio narrator with a natural tone',
        language: 'en',
        n: 2,
        num_step: 32,
        reference_text: 'Welcome to Fish Audio.',
        seed: 42,
        speed: 1
      })
    };
    
    fetch('https://api.fish.audio/v1/voice-design', options)
      .then(res => res.json())
      .then(res => console.log(res))
      .catch(err => console.error(err));
    
    
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, [
      CURLOPT_URL => "https://api.fish.audio/v1/voice-design",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => json_encode([
        'guidance_scale' => 2,
        'instruct_guidance_scale' => 0,
        'instruction' => 'Warm, confident studio narrator with a natural tone',
        'language' => 'en',
        'n' => 2,
        'num_step' => 32,
        'reference_text' => 'Welcome to Fish Audio.',
        'seed' => 42,
        'speed' => 1
      ]),
      CURLOPT_HTTPHEADER => [
        "Authorization: Bearer <token>",
        "Content-Type: application/json",
        "model: <model>"
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
    
    	url := "https://api.fish.audio/v1/voice-design"
    
    	payload := strings.NewReader("{\n  \"guidance_scale\": 2,\n  \"instruct_guidance_scale\": 0,\n  \"instruction\": \"Warm, confident studio narrator with a natural tone\",\n  \"language\": \"en\",\n  \"n\": 2,\n  \"num_step\": 32,\n  \"reference_text\": \"Welcome to Fish Audio.\",\n  \"seed\": 42,\n  \"speed\": 1\n}")
    
    	req, _ := http.NewRequest("POST", url, payload)
    
    	req.Header.Add("model", "<model>")
    	req.Header.Add("Authorization", "Bearer <token>")
    	req.Header.Add("Content-Type", "application/json")
    
    	res, _ := http.DefaultClient.Do(req)
    
    	defer res.Body.Close()
    	body, _ := io.ReadAll(res.Body)
    
    	fmt.Println(string(body))
    
    }
    
    
    HttpResponse<String> response = Unirest.post("https://api.fish.audio/v1/voice-design")
      .header("model", "<model>")
      .header("Authorization", "Bearer <token>")
      .header("Content-Type", "application/json")
      .body("{\n  \"guidance_scale\": 2,\n  \"instruct_guidance_scale\": 0,\n  \"instruction\": \"Warm, confident studio narrator with a natural tone\",\n  \"language\": \"en\",\n  \"n\": 2,\n  \"num_step\": 32,\n  \"reference_text\": \"Welcome to Fish Audio.\",\n  \"seed\": 42,\n  \"speed\": 1\n}")
      .asString();
    
    
    require 'uri'
    require 'net/http'
    
    url = URI("https://api.fish.audio/v1/voice-design")
    
    http = Net::HTTP.new(url.host, url.port)
    http.use_ssl = true
    
    request = Net::HTTP::Post.new(url)
    request["model"] = '<model>'
    request["Authorization"] = 'Bearer <token>'
    request["Content-Type"] = 'application/json'
    request.body = "{\n  \"guidance_scale\": 2,\n  \"instruct_guidance_scale\": 0,\n  \"instruction\": \"Warm, confident studio narrator with a natural tone\",\n  \"language\": \"en\",\n  \"n\": 2,\n  \"num_step\": 32,\n  \"reference_text\": \"Welcome to Fish Audio.\",\n  \"seed\": 42,\n  \"speed\": 1\n}"
    
    response = http.request(request)
    puts response.read_body

200

401

402

503
    
    
    {
      "candidates": [
        {
          "id": "<string>",
          "index": 1,
          "audio_base64": "<string>",
          "sample_rate": 123,
          "duration_ms": 1,
          "text": "<string>",
          "instruct": "<string>",
          "language": "<string>"
        }
      ]
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

This endpoint only accepts `application/json`.You must include the `model: voice-design-1` header. Extra request fields are rejected.

A successful request returns generated voice candidates with `audio_base64` audio payloads. Decode the base64 value to write the candidate audio to a file.

## 

​

Example
    
    
    curl --request POST https://api.fish.audio/v1/voice-design \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --header "model: voice-design-1" \
      --data '{
        "instruction": "Warm, confident studio narrator with a natural tone",
        "reference_text": "Welcome to Fish Audio.",
        "language": "en",
        "n": 2,
        "speed": 1,
        "num_step": 32,
        "guidance_scale": 2,
        "instruct_guidance_scale": 0,
        "seed": 42
      }'
    

## 

​

Usage notes

  * `instruction` is required and must be 1 to 2000 characters.
  * `reference_text` is optional preview text and can be up to 150 characters.
  * `n` controls how many candidates are returned. The supported range is 1 to 4.
  * `seed` is optional and can help reproduce candidate generation.
  * The endpoint is stateless: it does not create batches, samples, voice models, or presigned URLs.
  * Billing happens once per successful generation request, not once per candidate.



#### Authorizations

​

Authorization

string

header

required

Bearer authentication header of the form `Bearer <token>`, where `<token>` is your auth token.

#### Headers

​

model

string

default:voice-design-1

required

Specify which voice-design model to use.

Allowed value: `"voice-design-1"`

#### Body

application/json

Request body for synchronous voice design generation. The endpoint returns generated voice candidates with base64-encoded audio.

​

instruction

string

required

Voice design prompt. Must contain 1 to 2000 characters.

Required string length: `1 - 2000`

​

reference_text

string | null

Optional text used as reference content for the generated voice.

Maximum string length: `150`

​

language

string | null

Optional BCP-47 language hint, such as `en`, `zh`, or `ja`.

​

n

integer

default:2

Number of voice candidates to generate.

Required range: `1 <= x <= 4`

​

speed

number

default:1

Speaking speed multiplier for candidate generation.

Required range: `x <= 3`

​

num_step

integer

default:32

Number of diffusion steps used by the voice-design model.

Required range: `1 <= x <= 128`

​

guidance_scale

number

default:2

Classifier-free guidance scale. Higher values follow the prompt more strongly.

Required range: `x >= 0`

​

instruct_guidance_scale

number

default:0

Instruction guidance scale for prompt conditioning.

Required range: `x >= 0`

​

seed

integer | null

Optional deterministic seed for candidate generation.

#### Response

200

application/json

Request fulfilled, document follows

​

candidates

VoiceDesignCandidate · object[]

required

Generated voice candidates.

Show child attributes

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/endpoint/openapi-v1/voice-design.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/endpoint/openapi-v1/voice-design)

[Speech to Text](https://docs.fish.audio/api-reference/endpoint/openapi-v1/speech-to-text)[Agents API Errors](https://docs.fish.audio/api-reference/agent-errors)
