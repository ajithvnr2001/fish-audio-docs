---
url: https://docs.fish.audio/agents/overview/
title: Agents Overview - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:46:44.124560+00:00
---

# Agents Overview - Fish Audio

> Source: https://docs.fish.audio/agents/overview/

## On this page

  * Three surfaces, one agent
  * From draft to production
  * Capabilities



Get Started

# Agents Overview

Copy pageCopy page

Build voice agents in the console, ship them with the REST API and SDKs, and put them on the phone

Copy pageCopy page

Fish Agents is a hosted platform for real-time voice agents. Define an agent’s prompt, voice, knowledge, and tools in the Builder console, publish it, and talk to it from your web app through the SDK, over a phone number, or anywhere the REST API reaches. Speech recognition, turn-taking, and speech synthesis are handled for you.

Agents is in public beta. Every Fish Audio account can use it: open [Agents](https://fish.audio/app/agents) in the console to get started. Features and APIs may still change before general availability.

## Quickstart

Create an agent and have your first conversation in minutes.

## Concepts

Agents, drafts, versions, sessions: the mental model.

## Integration overview

Pick the right surface for your app.

## 

​

Three surfaces, one agent

Surface| What it does| Start here  
---|---|---  
**Console**|  Design, test, and publish agents visually, with no code.| [Configuration](https://docs.fish.audio/agents/build/configuration)  
**REST API**|  Manage agents, sessions, tools, and knowledge programmatically under `/v1/agent/*`.| [API introduction](https://docs.fish.audio/api-reference/introduction)  
**Client SDKs**|  Run live voice conversations in the browser with `@fishaudio/agent-client` or `@fishaudio/agent-react`.| [Web SDK](https://docs.fish.audio/agents/deploy/web-sdk)  
  
All three operate on the same agents. The core console workflow (creating agents, editing configuration, publishing versions) is also available over the API with your standard Fish Audio API key:
    
    
    curl https://api.fish.audio/v1/agent/agents \
      --header "Authorization: Bearer $FISH_API_KEY"
    

## 

​

From draft to production

1

Configure

Write the system prompt, set the first message, and pick a [voice and speaking language](https://docs.fish.audio/agents/build/voice-language). Attach [knowledge sources](https://docs.fish.audio/agents/build/knowledge-base) and [tools](https://docs.fish.audio/agents/build/tools). Edits save to the agent’s draft automatically.

2

Test

Talk to the draft in a [preview call](https://docs.fish.audio/agents/test/preview-calls), or run scripted [agent tests](https://docs.fish.audio/agents/test/agent-tests) that judge each reply pass or fail.

3

Publish

[Publishing](https://docs.fish.audio/agents/deploy/versions-publishing) freezes the draft into an immutable, numbered version. Live sessions always run the published configuration, so you can keep editing safely.

4

Integrate

Drop the [web SDK](https://docs.fish.audio/agents/deploy/web-sdk) into your app, create sessions over [REST](https://docs.fish.audio/agents/deploy/overview), or [bind a phone number](https://docs.fish.audio/agents/telephony/phone-numbers) so the agent answers inbound calls.

5

Monitor

Review transcripts, tool calls, and recordings in [conversation history](https://docs.fish.audio/agents/monitor/conversation-history), let [post-call analysis](https://docs.fish.audio/agents/monitor/post-call-analysis) summarize and evaluate every call, and push results to your backend with [webhooks](https://docs.fish.audio/agents/monitor/webhooks).

## 

​

Capabilities

## Prompt & voice

System prompt, first message, and any voice from the Fish Audio Voice Library.

## Knowledge base

Upload documents the agent retrieves from during conversations. Update a source and every agent using it picks up the new content.

## Tools

Call your backend with [webhook tools](https://docs.fish.audio/agents/build/webhook-tools), run code in your app with [client tools](https://docs.fish.audio/agents/build/client-tools), and toggle built-in [system tools](https://docs.fish.audio/agents/build/system-tools).

## Dynamic variables

Personalize each session with values injected at call time.

## Versions & publishing

Draft safely, publish deliberately, and read back the full version history.

## Telephony

Answer [inbound calls](https://docs.fish.audio/agents/telephony/inbound-calls) on [phone numbers](https://docs.fish.audio/agents/telephony/phone-numbers) bound to your agents.

## Conversation history

Transcripts, tool timelines, and per-speaker recordings. You choose what each agent stores.

## Post-call analysis & webhooks

Automatic summaries, structured data extraction, and success criteria, delivered to your systems via [webhooks](https://docs.fish.audio/agents/monitor/webhooks).

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/overview.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/overview)

[Quickstart](https://docs.fish.audio/agents/quickstart)
