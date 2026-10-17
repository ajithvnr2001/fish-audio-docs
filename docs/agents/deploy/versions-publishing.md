---
url: https://docs.fish.audio/agents/deploy/versions-publishing/
title: Versions & Publishing - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:46:43.480374+00:00
---

# Versions & Publishing - Fish Audio

> Source: https://docs.fish.audio/agents/deploy/versions-publishing/

## On this page

  * Draft vs. published
  * Publish from the Builder
  * Publish via the API
  * Version history
  * Restore a previous version
  * Clone an agent
  * Going further



Deploy

# Versions & Publishing

Copy pageCopy page

Edit safely in a draft, then publish an immutable version that live sessions run

Copy pageCopy page

Every agent has one **draft** and a linear history of **published versions**. Edits in the Builder or via the API always land in the draft. Production sessions never see them until you publish. Publishing snapshots the draft into an immutable, numbered version.

## Edit the draft

Prompt, voice, and conversation settings, all autosaved.

## Test before publishing

Preview calls talk to the draft, not the live version.

## Automate via API

Manage drafts, publishing, and version history programmatically.

## 

​

Draft vs. published

| Draft| Published version  
---|---|---  
Mutability| Editable: Builder and `PATCH .../config` write here| Immutable snapshot  
Used by| [Preview calls](https://docs.fish.audio/agents/test/preview-calls) and [agent tests](https://docs.fish.audio/agents/test/agent-tests)| Production sessions: web, SDK, and phone  
History| One per agent, always current| `version_number` increments with each publish  
  
An agent that has never been published cannot take production sessions: session creation returns `409` until the first publish.

Phone number settings are not part of the agent, so they are not versioned. Which agent a number is bound to, its [transfer caller ID](https://docs.fish.audio/agents/telephony/transfers#caller-id-on-transfers), and an [imported number’s SIP configuration](https://docs.fish.audio/agents/telephony/byo-sip#update-the-configuration) live on the number. Changes to them apply from the next call without publishing, and publishing or rolling back the agent never changes them.

## 

​

Publish from the Builder

1

Edit: changes autosave

Every change is written to the draft automatically; the **Saving… / Draft saved** indicator in the top bar shows the current state.

2

Watch the unpublished-changes indicator

When the draft differs from the last published version, the **Publish** button becomes active with an unpublished-changes hint next to it. When there is nothing new to publish, the button is disabled. An agent that has never been published always counts as having changes.

3

Publish

Click **Publish**. Any pending edits are saved first, then the draft is snapshotted as the next version. A confirmation shows the new version number, and the agent shows as **Live** in your agents list.

New sessions use the newly published version from that point on. To hear a change before it goes live, run a [preview call](https://docs.fish.audio/agents/test/preview-calls). Previews always use the draft.

## 

​

Publish via the API

Configuration edits (`PATCH`) go to the draft; a separate `publish` call rolls them out. A `version_title` and `version_description` are optional and make the version history easier to audit:

Update the draft
    
    
    curl --request PATCH "https://api.fish.audio/v1/agent/agents/$AGENT_ID/config" \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{
        "prompt": { "system_prompt": "You are a concise support agent for Acme." }
      }'
    

Publish
    
    
    curl --request POST "https://api.fish.audio/v1/agent/agents/$AGENT_ID/publish" \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{ "version_title": "Tighten support tone" }'
    

The publish response includes the new `version_number`.

## 

​

Version history

List published versions, or fetch the complete configuration snapshot of any one of them, including the version currently serving production:

List versions
    
    
    curl "https://api.fish.audio/v1/agent/agents/$AGENT_ID/versions" \
      --header "Authorization: Bearer $FISH_API_KEY"
    

Get one version's snapshot
    
    
    curl "https://api.fish.audio/v1/agent/agents/$AGENT_ID/versions/3" \
      --header "Authorization: Bearer $FISH_API_KEY"
    

Each version record includes:

Field| Description  
---|---  
`version_number`| Auto-incrementing, unique per agent  
`version_title`| Optional label sent when publishing  
`version_description`| Optional description sent when publishing  
`config_hash`| Fingerprint of the configuration snapshot  
`published_at`| When the version was published  
  
Fetching a single version returns the full configuration as it was published. Because `GET .../config` always shows the draft, the snapshot endpoint is how you read back what is actually running in production.

Version snapshots never echo credential secrets. Write-only fields (such as webhook secrets and tool authorization headers) return a `has_secret: true` marker instead of the value, and the custom LLM [`api_key`](https://docs.fish.audio/agents/build/custom-llm) reads back as `null`, in every version including historical ones.

## 

​

Restore a previous version

Roll back by copying an old snapshot back into the draft: read the version you want, then `PATCH` its sections into the draft config.

1\. Read the old snapshot
    
    
    curl "https://api.fish.audio/v1/agent/agents/$AGENT_ID/versions/2" \
      --header "Authorization: Bearer $FISH_API_KEY"
    

2\. Patch it back into the draft
    
    
    curl --request PATCH "https://api.fish.audio/v1/agent/agents/$AGENT_ID/config" \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{ "prompt": { "system_prompt": "<system prompt from the snapshot>" } }'
    

Patching updates the draft. It does **not** publish. Review or [preview](https://docs.fish.audio/agents/test/preview-calls) the restored draft, then publish it as a new version; the rollback becomes part of the linear history, so the audit trail stays intact. Because snapshots never echo secrets (see above), credential fields keep their current draft values unless you set them again explicitly. Phone number settings, such as the transfer caller ID, stay as they are.

## 

​

Clone an agent

Cloning creates a new agent from an existing one’s **draft** configuration. In the console, open the agents list and choose **Clone** from the agent’s row menu. The clone starts with a copy of the source’s current draft. Published versions do not carry over: the new agent is unpublished until you publish it yourself. Use clones to template a base configuration across many agents, or to experiment without risking an agent that is already live.

## 

​

Going further

## Agent configuration

Everything that lives in the draft: prompt, voice, conversation settings.

## Preview calls

Talk to the draft before it ships.

## Agent tests

Run regression tests against the draft, then publish with confidence.

## Integration overview

Connect published agents to your product via SDK and API.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/deploy/versions-publishing.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/deploy/versions-publishing)

[Overview](https://docs.fish.audio/agents/deploy/overview)[Public Agents](https://docs.fish.audio/agents/deploy/public-agents)
