---
url: https://docs.fish.audio/agents/build/time-timezone/
title: Time & Timezone - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:46:41.001109+00:00
---

# Time & Timezone - Fish Audio

> Source: https://docs.fish.audio/agents/build/time-timezone/

## On this page

  * What the agent knows
  * Which timezone a session uses
  * Turn it off
  * Going further



Build

# Time & Timezone

Copy pageCopy page

Your agent knows the current date and time by default: how the timezone is chosen and how to opt out

Copy pageCopy page

Agents are time-aware out of the box: every session knows today’s date and the current time in the session’s timezone. You don’t reference a variable or add anything to your prompt: “tomorrow morning” and “next Tuesday” ground correctly from the first turn, on every channel (voice, text, and phone).

The default timezone is **UTC**. Change it for the agent in its [configuration](https://docs.fish.audio/agents/build/configuration#timezone), and override it for a single session with `timezone` in the creation request. See Which timezone a session uses.

## 

​

What the agent knows

Fish Audio injects two pieces of world context server-side:

When| What| Example  
---|---|---  
At session start| Today’s date and the session timezone| `Today is Thursday, July 23, 2026. Session timezone: Asia/Tokyo (UTC+9).`  
Before every reply| The current time, minute precision| `Current date and time: Thursday, July 23, 2026 at 13:00 (Asia/Tokyo).`  
  
The time is refreshed on every turn, so it stays accurate through long conversations and past midnight.

Injection happens outside your configuration, so it never counts toward the system prompt’s character limit.

Both facts also exist as [system variables](https://docs.fish.audio/agents/build/dynamic-variables#system-variables) for the cases where you want to template them yourself, for example into a webhook tool’s URL: `{{system.today}}` is the date at session creation as ISO `YYYY-MM-DD`, and `{{system.timezone}}` is the resolved IANA name (`UTC` when nothing resolves). There is no `{{system.now}}`: variables render once, when the session is created, so a templated clock would freeze at the opening. The per-turn time above is the one to rely on.

## 

​

Which timezone a session uses

The timezone is resolved once, when the session is created, taking the first that applies:

  1. **`timezone`** in the creation request: your explicit per-session choice, as an IANA name like `Asia/Tokyo`. An invalid name rejects the request with `422`.
  2. **The agent’s configured timezone** : set on the agent in the Builder (**Configuration → Timezone**) or via the [agent config API](https://docs.fish.audio/agents/build/configuration). Pin one when your agent serves a single region regardless of who calls.
  3. **`client_timezone`** : a hint with the end user’s browser timezone, sent automatically by the [Web SDK](https://docs.fish.audio/agents/deploy/web-sdk) in public-agent mode. Used only when neither of the above is set; an invalid hint is ignored rather than failing the session.
  4. **The caller’s phone number** : inbound calls infer the timezone from the caller’s country when that country has a single timezone.
  5. **UTC** otherwise.

In the browser, this means zero configuration: the SDK detects the visitor’s real timezone and the agent talks about “today” in the user’s local terms, not yours. With [authenticated sessions](https://docs.fish.audio/agents/deploy/authenticated-sessions), the SDK’s automatic hint doesn’t apply. Your backend creates the session, so set `timezone` (or forward the browser’s value as `client_timezone`) in the creation request:

API (curl)
    
    
    curl --request POST https://api.fish.audio/v1/agent/sessions \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{
        "agent_id": "YOUR_AGENT_ID",
        "timezone": "Asia/Tokyo"
      }'
    

Phone-number inference is country-level only. Countries that span several timezones (the US, Canada, Australia, Russia, Brazil) are skipped. Set the agent’s timezone for those. Calls that resolve nothing run in UTC.

## 

​

Turn it off

Time awareness is on by default. To withhold both the date and the per-turn time from a session (for example a role-play agent set on a fictional date, or a test that must be reproducible), set `world_context: false` when creating the session:

API (curl)

JavaScript SDK
    
    
    curl --request POST https://api.fish.audio/v1/agent/sessions \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{
        "agent_id": "YOUR_AGENT_ID",
        "world_context": false
      }'
    
    
    
    import { AgentSession } from "@fishaudio/agent-client";
    
    // Public agent: the SDK forwards the opt-out in its creation request.
    const session = await AgentSession.start({
      agentId: "YOUR_AGENT_ID",
      worldContext: false,
    });
    

## 

​

Going further

## Authenticated sessions

All session-creation parameters, including `timezone` and `world_context`.

## Dynamic variables

Personalize the rest of the prompt at session creation.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/build/time-timezone.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/build/time-timezone)

[Voice & Language](https://docs.fish.audio/agents/build/voice-language)[Knowledge Base](https://docs.fish.audio/agents/build/knowledge-base)
