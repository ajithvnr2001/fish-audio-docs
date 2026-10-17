---
url: https://docs.fish.audio/agents/concepts/
title: Core Concepts - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:46:42.431793+00:00
---

# Core Concepts - Fish Audio

> Source: https://docs.fish.audio/agents/concepts/

## On this page

  * Workspaces
  * Agents
  * Drafts and published versions
    * Live vs. Draft
    * Which configuration runs
    * Restore and clone
  * Sessions
  * Deleting resources
  * Where everything lives
  * Going further



Get Started

# Core Concepts

Copy pageCopy page

Workspaces, agents, versions, and sessions: the mental model behind Fish Agents

Copy pageCopy page

Four nouns cover the whole platform. A **workspace** holds everything your team builds. An **agent** is a voice assistant you configure. Publishing an agent’s draft creates an immutable **version**. And every conversation with an agent (from your app, a phone call, or the console) is a **session**.

## 

​

Workspaces

A workspace is the isolation boundary for everything you create. Agents, tools, knowledge sources, and tests all belong to a workspace, and nothing in it is visible from any other workspace. Tools, knowledge sources, and tests are **workspace-level resources** , not per-agent ones: create a webhook tool once and attach it to as many agents as you like. Access controls in the console decide which agents can use each shared resource. Your API key belongs to your team: requests under `/v1/agent/*` can read and write agent resources across all of your team’s workspaces, and each resource carries its `workspace_id`. Resources created through the API land in the key owner’s default workspace:

List your team's agents
    
    
    curl https://api.fish.audio/v1/agent/agents \
      --header "Authorization: Bearer $FISH_API_KEY"
    

Create keys under [API keys](https://fish.audio/app/api-keys/) in the console.

## 

​

Agents

An agent is a bundle of configuration: a system prompt that steers behavior, a first-message policy, a [voice and speaking language](https://docs.fish.audio/agents/build/voice-language), attached [tools](https://docs.fish.audio/agents/build/tools), and [knowledge sources](https://docs.fish.audio/agents/build/knowledge-base). You assemble it in the Builder (the console page you land on after creating an agent) or through the API at `/v1/agent/agents`. Creating an agent takes only a name. Everything else is configured afterward, so start minimal and iterate.

## 

​

Drafts and published versions

Every agent has exactly one **draft** and any number of immutable **published versions**.

1

Edit the draft

Everything you change in the Builder autosaves to the draft. Watch for the `Saving… / Saved` indicator.

2

Publish

**Publish** snapshots the draft into a numbered, immutable version and makes it the version that live traffic uses. The button is only enabled when the draft actually differs from the latest published version.

3

Keep iterating

Continue editing the draft without affecting live conversations. When you’re ready, publish again. The version number increments.

### 

​

Live vs. Draft

The agent list shows one of two states:

Badge| Meaning  
---|---  
**Live**|  The agent has been published at least once  
**Draft**|  The agent has never been published  
  
Editing the draft of a Live agent does not change its badge. The Builder shows an unpublished-changes indicator next to **Publish** instead.

### 

​

Which configuration runs

  * [Preview calls](https://docs.fish.audio/agents/test/preview-calls) in the Builder always run the **current draft** , so you can hear changes before anyone else does.
  * Sessions from the SDK, phone calls, and public agent links run the **latest published version**.



This split is the core workflow: iterate on the draft, verify with a preview call, then publish to roll the change out to real traffic.

### 

​

Restore and clone

Past versions stay in the agent’s history. Review them or restore one back into the draft from [Versions & publishing](https://docs.fish.audio/agents/deploy/versions-publishing). **Clone** creates a new agent from an existing one’s current draft: prompt, voice, and tool and knowledge attachments carry over (shared resources are referenced, not copied). The clone is named `{name} copy`, starts as Draft, and does not inherit the source’s publish history.

## 

​

Sessions

A session is one conversation between one user and one agent. Sessions start from four places:

## Your app

A client connects with the [Web](https://docs.fish.audio/agents/deploy/web-sdk) or [React](https://docs.fish.audio/agents/deploy/react-sdk) SDK.

## Preview call

You test the draft from the Builder.

## Phone call

A caller dials a connected [phone number](https://docs.fish.audio/agents/telephony/phone-numbers).

## Public agent

Anyone talks to an agent you’ve shared publicly.

Except [preview calls](https://docs.fish.audio/agents/test/preview-calls), which are ephemeral and never enter history, every session appears in [Conversation history](https://docs.fish.audio/agents/monitor/conversation-history) and `/v1/agent/sessions` (with its transcript, and its recording when the agent [records audio](https://docs.fish.audio/agents/monitor/conversation-history#what-gets-stored)) and can trigger [post-call analysis](https://docs.fish.audio/agents/monitor/post-call-analysis) when configured.

## 

​

Deleting resources

Deletion is immediate and, from the console, cannot be undone: a deleted agent disappears from lists, the Builder, and all API responses. The same applies to tools, knowledge sources, and tests.

Names are freed on deletion: you can immediately create a new agent (or tool) with the same name.

## 

​

Where everything lives

Concept| Console| API resource  
---|---|---  
Agent| **Agents** list → Builder| [`/v1/agent/agents`](https://docs.fish.audio/api-reference/endpoint/agent/list-agents)  
Draft & versions| Builder (autosave + **Publish**)| [`/v1/agent/agents`](https://docs.fish.audio/api-reference/endpoint/agent/get-draft-config)  
Session| [Preview calls](https://docs.fish.audio/agents/test/preview-calls), [Conversation history](https://docs.fish.audio/agents/monitor/conversation-history)| [`/v1/agent/sessions`](https://docs.fish.audio/api-reference/endpoint/agent/create-agent-session)  
Tool| Builder **Tools** page| [`/v1/agent/tools`](https://docs.fish.audio/api-reference/endpoint/agent/list-tools)  
Knowledge source| Builder **Knowledge base** page| [`/v1/agent/knowledge-sources`](https://docs.fish.audio/api-reference/endpoint/agent/list-knowledge-sources)  
Phone number| **Phone numbers** page| [`/v1/agent/phone-numbers`](https://docs.fish.audio/api-reference/endpoint/agent/list-phone-numbers)  
  
## 

​

Going further

## Quickstart

Create, configure, and talk to your first agent.

## Configuration

System prompt, first message, and conversation settings.

## Versions & publishing

Publish history, restore, and rollout details.

## Integrate

Put your agent in front of users with the SDKs.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/concepts.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/concepts)

[Quickstart](https://docs.fish.audio/agents/quickstart)[Pricing](https://docs.fish.audio/agents/pricing)
