---
url: https://docs.fish.audio/agents/deploy/public-agents/
title: Public Agents - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:46:41.775945+00:00
---

# Public Agents - Fish Audio

> Source: https://docs.fish.audio/agents/deploy/public-agents/

## On this page

  * Enable public access
  * Start a session from the browser
  * Origin matching
  * Rate limiting
  * Treat public input as untrusted
  * Errors
  * When to use session tokens instead
  * Going further



Deploy

# Public Agents

Copy pageCopy page

Let visitors talk to your agent directly from the browser, no backend required

Copy pageCopy page

A public agent accepts sessions straight from the browser: the SDK calls the session endpoint with just an `agent_id`, no API key and no server of your own. The platform gates access with three controls: an agent-level public switch (off by default), a required origin allowlist, and rate limiting. Use this mode for demos, marketing pages, and support bubbles where standing up a backend isn’t worth it. For production apps with their own users, [authenticated sessions](https://docs.fish.audio/agents/deploy/authenticated-sessions) are usually the better fit. See when to use session tokens instead.

## 

​

Enable public access

1

Publish the agent

Public sessions always run the agent’s **published** configuration. An unpublished agent rejects session creation. See [Versions & publishing](https://docs.fish.audio/agents/deploy/versions-publishing).

2

Turn on the public switch

On the agent’s **Deploy** page in the console, turn on **Public access**. It is **off by default**. Until you enable it, sessions require authentication.

3

Add allowed origins

On the same page, list every web origin that may start sessions under **Allowed origins** (`allowed_origins` in the API). The allowlist is **required** : a request whose `Origin` doesn’t match any entry is rejected with `403`.

## 

​

Start a session from the browser

Pass `agentId` to the SDK and it creates the session directly with the Fish Audio API, then connects the audio.

JavaScript

API (curl)
    
    
    import { AgentSession } from "@fishaudio/agent-client";
    
    const session = await AgentSession.start({
      agentId: "YOUR_AGENT_ID",
    });
    
    session.on("agentResponse", ({ text }) => console.log("Agent:", text));
    
    
    
    # No Authorization header. The Origin header is checked instead.
    # Browsers send Origin automatically; curl must set it explicitly.
    curl --request POST https://api.fish.audio/v1/agent/sessions \
      --header "Content-Type: application/json" \
      --header "Origin: https://app.example.com" \
      --data '{ "agent_id": "YOUR_AGENT_ID" }'
    

The response is the same session token an authenticated request returns. The SDK consumes it internally. Everything else (events, methods, client tools) works exactly as in the [Web SDK](https://docs.fish.audio/agents/deploy/web-sdk).

## 

​

Origin matching

An entry matches only on **exact scheme + host + port**. The host is case-insensitive, and a trailing slash on an entry is tolerated.

Allowlist entry| Browser origin| Allowed  
---|---|---  
`https://app.example.com`| `https://app.example.com`| Yes  
`https://app.example.com`| `https://APP.example.com`| Yes (host is case-insensitive)  
`https://app.example.com`| `http://app.example.com`| No (scheme differs)  
`https://app.example.com`| `https://app.example.com:8443`| No (port differs)  
`http://localhost:5173`| `http://127.0.0.1:5173`| No (different hosts)  
  
`localhost` and `127.0.0.1` are **different origins**. If you develop against both, list both:
    
    
    http://localhost:5173
    http://127.0.0.1:5173
    

## 

​

Rate limiting

Public session creation is rate limited on two dimensions at once: per **client IP** and per **agent**. Either limit being exceeded rejects the request. Sessions started on a public agent are billed to the workspace that owns the agent, at the standard [conversation rate](https://docs.fish.audio/agents/pricing).

If legitimate traffic outgrows these limits, or you need per-user quotas, move to [authenticated sessions](https://docs.fish.audio/agents/deploy/authenticated-sessions): your backend becomes the gate, and the platform-side public limits no longer apply.

## 

​

Treat public input as untrusted

On the public path, the entire session request originates in the visitor’s browser. The platform enforces its own guardrails (public sessions accept only the `language` and `voice_id` [overrides](https://docs.fish.audio/agents/deploy/authenticated-sessions#overrides), rejecting everything else with `400`), but anything that passes through verbatim is attacker-controllable:

  * **`metadata`** is stored and returned exactly as sent, never interpreted by the platform. When you read it back in [conversation history](https://docs.fish.audio/agents/monitor/conversation-history) or [webhooks](https://docs.fish.audio/agents/monitor/webhooks), treat it as untrusted data, never as proof of who the visitor is.
  * **`dynamic_variables`** are chosen by the page that starts the session. Don’t inject anything through them that the visitor shouldn’t control. See [Dynamic variables](https://docs.fish.audio/agents/build/dynamic-variables).

For trusted attribution (a verified `end_user_id`, server-set metadata), create sessions from your backend instead.

## 

​

Errors

Public-mode failures surface as `FishAgentError` codes on `AgentSession.start()`:

Code| Meaning  
---|---  
`agent_not_public`| The agent’s public switch is off.  
`origin_forbidden`| The page’s origin is not in `allowed_origins` (HTTP `403`).  
`session_request_failed`| Other creation failures, for example the agent has no published version.  
  
## 

​

When to use session tokens instead

Public mode trades control for zero setup. Prefer the `sessionToken` flow (your backend calls the session endpoint with an API key and hands the token to the browser) when any of these apply:

  * The agent should stay **private** rather than callable by anyone who loads your page.
  * You need **trusted attribution** : an `end_user_id` and `metadata` set by your server, not the browser.
  * You want server-side control of `overrides`, `dynamic_variables`, or `tool_events` instead of accepting the browser’s values.
  * You already authenticate users and want **your own quotas** per account, not IP-based platform limits.

The SDK call changes by one field: pass `{ sessionToken }` instead of `{ agentId }`. See [Authenticated sessions](https://docs.fish.audio/agents/deploy/authenticated-sessions) for the full flow.

## 

​

Going further

## Authenticated sessions

The session token flow in full: request fields, lifetime, errors.

## Web SDK

Events, methods, and client tools, identical in both modes.

## React SDK

Hooks and components for React apps.

## Conversation history

Review what public visitors said to your agent.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/deploy/public-agents.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/deploy/public-agents)

[Versions & Publishing](https://docs.fish.audio/agents/deploy/versions-publishing)[Authenticated Sessions](https://docs.fish.audio/agents/deploy/authenticated-sessions)
