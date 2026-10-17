---
url: https://docs.fish.audio/features/manage-voices/
title: Manage Voices - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:38.900760+00:00
---

# Manage Voices - Fish Audio

> Source: https://docs.fish.audio/features/manage-voices/

## On this page

  * When to use it
  * List your voices
  * Get, update, and delete
  * Implementation details
    * Filtering and pagination
    * Visibility
  * Going further



Core Features

# Manage Voices

Copy pageCopy page

List, inspect, update, and delete your voice models

Copy pageCopy page

Every voice you [clone](https://docs.fish.audio/features/voice-cloning) becomes a model you own. List your library, look up a model’s details, rename or re-share it, and delete what you no longer need, all from the API directly, the Python library, or JavaScript.

## Use it in the web app

No code: manage voices in the browser.

## API reference

Every endpoint for voice models.

## Cookbooks

Search and reuse Library voices.

## 

​

When to use it

## Browse your library

List the voices you’ve created or saved.

## Find a voice id

Look up the `reference_id` to use in [Text to Speech](https://docs.fish.audio/features/text-to-speech).

## Update metadata

Rename, re-tag, or change a model’s visibility.

## Clean up

Delete models you no longer use.

## 

​

List your voices

Page through your library. The response carries the `total` count and the `items` for the current page.

Python

API (curl)

JavaScript
    
    
    from fishaudio import FishAudio
    
    client = FishAudio()  # reads FISH_API_KEY
    
    page = client.voices.list(self_only=True, page_size=20)
    
    print(f"{page.total} voices")
    for v in page.items:
        print(v.id, v.title, v.state, v.visibility)
    
    
    
    curl "https://api.fish.audio/model?self=true&page_size=20" \
      --header "Authorization: Bearer $FISH_API_KEY"
    
    # Response: { "total": 42, "items": [ ... ], "has_more": true }
    
    
    
    import { FishAudioClient } from "fish-audio";
    
    const client = new FishAudioClient({ apiKey: process.env.FISH_API_KEY });
    
    const page = await client.voices.search({ page_size: 20 });
    
    console.log(`${page.total} voices`);
    for (const v of page.items) {
      console.log(v._id ?? v.id, v.title, v.state, v.visibility);
    }
    

## 

​

Get, update, and delete

Use a voice **id** to inspect a single model, change its metadata, or remove it.

Python

API (curl)
    
    
    # Inspect one model
    voice = client.voices.get("YOUR_VOICE_ID")
    print(voice.title, voice.state)
    
    # Update metadata (only the fields you pass change)
    client.voices.update(
        "YOUR_VOICE_ID",
        title="Updated title",
        visibility="unlist",
    )
    
    # Delete
    client.voices.delete("YOUR_VOICE_ID")
    
    
    
    # Inspect one model
    curl https://api.fish.audio/model/YOUR_VOICE_ID \
      --header "Authorization: Bearer $FISH_API_KEY"
    
    # Update metadata
    curl --request PATCH https://api.fish.audio/model/YOUR_VOICE_ID \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{ "title": "Updated title", "visibility": "unlist" }'
    
    # Delete
    curl --request DELETE https://api.fish.audio/model/YOUR_VOICE_ID \
      --header "Authorization: Bearer $FISH_API_KEY"
    

## 

​

Implementation details

### 

​

Filtering and pagination

Narrow the list with `title`, `tags`, or `language`, and page with `page_size` and `page_number`. Omit `self_only` (API: `self`) to search the public [Voice Library](https://docs.fish.audio/overview/platform) instead of just your own models.

Python

API (curl)
    
    
    page = client.voices.list(
        self_only=True,
        title="narration",
        page_size=50,
        page_number=2,
    )
    
    
    
    curl "https://api.fish.audio/model?self=true&title=narration&page_size=50&page_number=2" \
      --header "Authorization: Bearer $FISH_API_KEY"
    

### 

​

Visibility

Switch a model between `private`, `unlist` (shareable link), and `public` (listed in the Voice Library) with `update`. Publishing a model lets anyone use it as a `reference_id`.

## 

​

Going further

## Clone a voice

Create a new model from audio samples.

## Speak with a voice

Use any voice id as `reference_id`.

## Voice Models API

Every endpoint for listing and managing models.

## Python reference

The full `voices` resource surface.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/features/manage-voices.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/features/manage-voices)

[Realtime Streaming](https://docs.fish.audio/features/realtime-streaming)[Platform (Web App)](https://docs.fish.audio/overview/platform)
