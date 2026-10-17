---
url: https://docs.fish.audio/agents/deploy/overview/
title: Deploy Your Agent - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:46:41.917191+00:00
---

# Deploy Your Agent - Fish Audio

> Source: https://docs.fish.audio/agents/deploy/overview/

## On this page

  * Where users meet your agent
  * Who may start sessions
  * Still deciding?
  * How a browser session starts
  * Going further



Deploy

# Deploy Your Agent

Copy pageCopy page

Choose where users meet your agent and who may start sessions: widget, SDKs, or phone; public or authenticated

Copy pageCopy page

Your agent is one artifact with many front doors. Deploying it is two independent decisions:

  1. **Where users meet your agent** : a prebuilt widget, your own UI built on the SDKs, a phone number, or a custom client.
  2. **Who may start sessions** : anyone visiting your pages, or only clients your backend has vouched for.

Every surface runs the same agent with the same published configuration, and the browser surfaces work with either access mode.

Publishing gates every channel: sessions always run the agent’s **published** configuration, and creating a session against an agent that has never been published fails. [Publish](https://docs.fish.audio/agents/deploy/versions-publishing) before wiring up any channel.

## 

​

Where users meet your agent

In increasing order of integration effort:

## Widget

Drop a prebuilt call widget into your site: two lines of HTML, zero build step.

## Your own UI

Build a custom experience with the [Web SDK](https://docs.fish.audio/agents/deploy/web-sdk) or [React SDK](https://docs.fish.audio/agents/deploy/react-sdk): events, transcripts, audio controls.

## Phone

Bind a number and callers dial straight in.

## Custom client

On a stack the SDKs don’t cover, implement the [wire protocol](https://docs.fish.audio/agents/deploy/protocol) directly.

## 

​

Who may start sessions

The widget and the SDKs each work with **either** access mode; pick per agent. Phone numbers skip this decision entirely: inbound calls connect through [telephony](https://docs.fish.audio/agents/telephony/inbound-calls), not a browser session.

## Public agents

The client connects with just an `agentId`: no backend, gated by an origin allowlist and rate limits.

## Authenticated sessions

Your backend creates a short-lived session token with your API key: trusted attribution and full control.

| Public agent ID| Session token  
---|---|---  
Credential in browser| None| Short-lived session token  
Requires| Agent set to public + allowed origins| Your own backend endpoint  
Session parameters set by| The SDK (`overrides`, `dynamicVariables`, `language`, `toolEvents` options)| Your backend, in the creation request  
Best for| Demos, marketing pages, low-friction embeds| Production apps with signed-in users  
  
## 

​

Still deciding?

You are building| Start with  
---|---  
A call button on an existing site, no build step| [Widget](https://docs.fish.audio/agents/deploy/widget) with [public access](https://docs.fish.audio/agents/deploy/public-agents)  
A demo or marketing page without a backend| [Web SDK](https://docs.fish.audio/agents/deploy/web-sdk) on a [public agent](https://docs.fish.audio/agents/deploy/public-agents)  
Voice calls inside a web app with signed-in users| [Web SDK](https://docs.fish.audio/agents/deploy/web-sdk) with [authenticated sessions](https://docs.fish.audio/agents/deploy/authenticated-sessions)  
A React or Next.js frontend| [React SDK](https://docs.fish.audio/agents/deploy/react-sdk)  
A phone line callers dial in to| [Phone numbers](https://docs.fish.audio/agents/telephony/phone-numbers) and [transfers](https://docs.fish.audio/agents/telephony/transfers)  
Server-side session creation and history retrieval| [Authenticated sessions](https://docs.fish.audio/agents/deploy/authenticated-sessions) and [conversation history](https://docs.fish.audio/agents/monitor/conversation-history)  
A client on a stack the SDKs don’t cover| [Wire protocol](https://docs.fish.audio/agents/deploy/protocol)  
  
## 

​

How a browser session starts

For private agents, your backend creates the session. Your API key never ships to the browser. The browser SDK takes the resulting session token and handles audio and transport from there.

Your backend
    
    
    curl --request POST https://api.fish.audio/v1/agent/sessions \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{ "agent_id": "YOUR_AGENT_ID" }'
    # → 201 session token. Return it to your frontend as-is
    

Your frontend
    
    
    import { AgentSession } from "@fishaudio/agent-client";
    
    // sessionToken = the create-session response, passed through unchanged
    const session = await AgentSession.start({ sessionToken });
    

Agents marked [public](https://docs.fish.audio/agents/deploy/public-agents) skip the backend step entirely: the SDK connects with just an `agentId`, gated by an origin allowlist and rate limits.

For phone calls there is no client integration: assign a number, and inbound calls connect directly to your agent, which can [transfer callers](https://docs.fish.audio/agents/telephony/transfers) to another number mid-call. See [Phone numbers](https://docs.fish.audio/agents/telephony/phone-numbers).

## 

​

Going further

## Versions & publishing

The publish step every channel depends on.

## Authenticated sessions

The full session-creation reference: request fields, token lifetime, errors.

## Conversation history

List sessions and read full transcripts over REST.

## Wire protocol

The wire-level session contract, for building your own client.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/deploy/overview.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/deploy/overview)

[Tutorial: Simulate a Rescheduling Call](https://docs.fish.audio/agents/test/simulation-tutorial)[Versions & Publishing](https://docs.fish.audio/agents/deploy/versions-publishing)
