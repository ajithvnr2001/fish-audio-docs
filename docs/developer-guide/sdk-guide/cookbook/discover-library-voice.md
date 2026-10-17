---
url: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/discover-library-voice/
title: Discover and reuse a Voice Library voice - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:34.958099+00:00
---

# Discover and reuse a Voice Library voice - Fish Audio

> Source: https://docs.fish.audio/developer-guide/sdk-guide/cookbook/discover-library-voice/

## On this page

  * Prerequisites
  * Recipe
  * Related



Manage Voices

# Discover and reuse a Voice Library voice

Copy pageCopy page

Search the public Voice Library by title, pick a result, and synthesize speech with it as your reference_id

Copy pageCopy page

## 

​

Prerequisites

Create a Fish Audio account

Sign up for a free Fish Audio account to get started with our API.

  1. Go to [fish.audio/auth/signup](https://fish.audio/auth/signup)
  2. Fill in your details to create an account, complete steps to verify your account.
  3. Log in to your account and navigate to the [API section](https://fish.audio/app/api-keys)



Get your API key

Once you have an account, you’ll need an API key to authenticate your requests.

  1. Log in to your [Fish Audio Dashboard](https://fish.audio/app/api-keys/)
  2. Navigate to the API Keys section
  3. Click “Create New Key” and give it a descriptive name, set a expiration if desired
  4. Copy your key and store it securely



Keep your API key secret! Never commit it to version control or share it publicly.

## 

​

Recipe

Set `self_only=False` on [`voices.list()`](https://docs.fish.audio/api-reference/sdk/python/resources#list) to search the public [Voice Library](https://docs.fish.audio/features/manage-voices) instead of only your own models. The response carries `total` (matches across all pages) and `items` (this page). Pick a result’s `id` and pass it straight to [`tts.convert()`](https://docs.fish.audio/api-reference/sdk/python/resources#convert) as `reference_id`.

Python

JavaScript
    
    
    from fishaudio import FishAudio
    from fishaudio.utils import save
    
    client = FishAudio()  # reads FISH_API_KEY
    
    # Search the public library by title (not just your own voices)
    page = client.voices.list(title="narration", self_only=False, page_size=10)
    print(f"{page.total} public voices match")
    
    # Pick the first result; fall back to a known id if the search is empty
    reference_id = "<voice-id>"
    for voice in page.items:
        print(voice.id, voice.title, voice.languages)
        reference_id = reference_id if reference_id != "<voice-id>" else voice.id
    
    # Synthesize with the discovered voice as the reference
    audio = client.tts.convert(
        text="Speaking with a voice I found in the public library.",
        reference_id=reference_id,
    )
    save(audio, "out.mp3")
    
    
    
    import { FishAudioClient } from "fish-audio";
    import { writeFile } from "fs/promises";
    
    const client = new FishAudioClient({ apiKey: process.env.FISH_API_KEY });
    
    // Search the public Voice Library by title (not just your own voices)
    const page = await client.voices.search({ title: "narration", page_size: 10 });
    console.log(`${page.total} public voices match`);
    
    // Pick the first result; fall back to a known id if the search is empty
    let referenceId = "<voice-id>";
    for (const voice of page.items) {
      console.log(voice._id, voice.title, voice.languages);
      referenceId = referenceId !== "<voice-id>" ? referenceId : voice._id;
    }
    
    // Synthesize with the discovered voice as the reference
    const stream = await client.textToSpeech.convert(
      {
        text: "Speaking with a voice I found in the public library.",
        reference_id: referenceId,
        format: "mp3",
      },
      "s2-pro"
    );
    
    const chunks = [];
    for await (const chunk of stream) chunks.push(Buffer.from(chunk));
    await writeFile("out.mp3", Buffer.concat(chunks));
    

`total > len(page.items)` tells you there are more pages; bump `page_number` to walk them. Any public voice `id` works as `reference_id`; nothing is saved to your account. You can hit the same endpoint directly:
    
    
    curl "https://api.fish.audio/model?title=narration&page_size=10" \
      --header "Authorization: Bearer $FISH_API_KEY"
    
    # Response: { "total": 128, "items": [ { "_id": "...", "title": "...", ... } ] }
    

Title search is fuzzy and ranked by usage, so the top result is usually the most popular match. Add `language=["en"]` to narrow by spoken language, or raise `page_size` and page with `page_number` to scan deeper.

## 

​

Related

  * [Manage Voices](https://docs.fish.audio/features/manage-voices)
  * [Instant voice cloning](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/instant-voice-cloning)
  * [Python reference: voices](https://docs.fish.audio/api-reference/sdk/python/resources)



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/sdk-guide/cookbook/discover-library-voice.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/sdk-guide/cookbook/discover-library-voice)

[Build a voice agent loop: speech in, reply, speech out](https://docs.fish.audio/developer-guide/sdk-guide/cookbook/voice-agent-loop)[Voice Cloning Best Practices](https://docs.fish.audio/developer-guide/best-practices/voice-cloning)
