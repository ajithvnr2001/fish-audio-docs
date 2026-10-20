---
url: https://docs.fish.audio/agents/telephony/inbound-calls/
title: Inbound Calls - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-20T12:51:59.033169+00:00
---

# Inbound Calls - Fish Audio

> Source: https://docs.fish.audio/agents/telephony/inbound-calls/

## On this page

  * Set up inbound calling
  * Phone sessions in history
  * Personalize calls before the agent answers
  * Phone sessions behave like any session
  * Going further



Telephony

# Inbound Calls

Copy pageCopy page

Bind an agent to a phone number and it answers every call to that number

Copy pageCopy page

Point a phone number at an agent and it picks up every inbound call. Phone calls are ordinary agent sessions: they appear in session history with caller attribution, they are [stored](https://docs.fish.audio/agents/monitor/conversation-history#what-gets-stored) and analyzed under the same per-agent settings as any other conversation, and they trigger the same webhooks.

## Phone numbers

Get a number and manage its agent binding.

## Conversation history

Review transcripts, tool calls, and recordings.

## Webhooks

Get notified when calls end and analysis completes.

## 

​

Set up inbound calling

1

Get a phone number

Add a number to your workspace; see [Phone numbers](https://docs.fish.audio/agents/telephony/phone-numbers). Numbers are stored and displayed in E.164 format (for example `+15551234567`).

2

Publish your agent

Calls connect to the agent’s published configuration, not the draft. [Publish](https://docs.fish.audio/agents/deploy/versions-publishing) before pointing traffic at the number.

3

Bind the agent to the number

Bind in the console, or set `agent_id` on the number via the API:

Bind an agent

Unbind
    
    
    curl --request PATCH https://api.fish.audio/v1/agent/phone-numbers/PHONE_NUMBER_ID \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{ "agent_id": "YOUR_AGENT_ID" }'
    
    
    
    curl --request PATCH https://api.fish.audio/v1/agent/phone-numbers/PHONE_NUMBER_ID \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{ "agent_id": null }'
    

The number-to-agent binding is resolved on each incoming call, so a rebind takes effect on the next call, useful for moving a number from a staging agent to a production agent.

## 

​

Phone sessions in history

Every answered call becomes a session with `source: "phone"` and these attribution fields:

Field| Description  
---|---  
`caller_number`| The caller’s number, E.164. `null` for non-phone sessions.  
`dialed_number`| The workspace number that was called, E.164. `null` for non-phone sessions.  
`sip_call_id`| The SIP `Call-ID` of the carrier’s INVITE, for [matching your SIP records](https://docs.fish.audio/agents/telephony/byo-sip#match-calls-with-your-sip-records).  
`call_sid`| Twilio’s CallSid on a call through a Twilio number, the same value the [inbound call webhook](https://docs.fish.audio/agents/monitor/webhooks#inbound-call-webhook) sends. `null` on other calls.  
  
List calls with the standard sessions endpoint. The `caller_number` filter is an exact match; bare numbers are automatically prefixed with `+`, so `15551234567` matches `+15551234567`:
    
    
    curl --request GET "https://api.fish.audio/v1/agent/sessions?agent_id=YOUR_AGENT_ID&caller_number=15551234567" \
      --header "Authorization: Bearer $FISH_API_KEY"
    
    
    
    {
      "sessions": [
        {
          "session_id": "9c41f0d2e8a34b7f",
          "agent_id": "YOUR_AGENT_ID",
          "agent_name": "Support line",
          "status": "completed",
          "source": "phone",
          "caller_number": "+15551234567",
          "dialed_number": "+14155550100",
          "created_at": "2026-07-23T09:14:01Z",
          "started_at": "2026-07-23T09:14:02Z",
          "ended_at": "2026-07-23T09:16:45Z",
          "duration_seconds": 163,
          "metadata": {}
        }
      ],
      "has_more": false,
      "next_cursor": null
    }
    

You can combine `caller_number` with the other list filters (`agent_id`, `status`, `created_after`, `created_before`); see [Conversation history](https://docs.fish.audio/agents/monitor/conversation-history) for the full parameter list. The agent can read both numbers too, as `{{system.caller_number}}` and `{{system.dialed_number}}` in its system prompt, first message, and webhook tool requests. No variable needs to be passed; see [System variables](https://docs.fish.audio/agents/build/dynamic-variables#system-variables).

System prompt
    
    
    The caller is calling from {{system.caller_number}}. Confirm the last four digits before discussing the account.
    

## 

​

Personalize calls before the agent answers

Inbound calls have no session-creation request to carry [dynamic variables](https://docs.fish.audio/agents/build/dynamic-variables), so the agent has a dedicated hook instead: the [inbound call webhook](https://docs.fish.audio/agents/monitor/webhooks#inbound-call-webhook). When configured, the platform posts the caller’s number to your endpoint while the call is being set up, and the `dynamic_variables` you return fill the `{{placeholders}}` in the published prompt and first message before the agent speaks. They fill [webhook tool](https://docs.fish.audio/agents/build/dynamic-variables#custom-variables-in-webhook-tools) requests too, so a lookup tool can send the caller’s record id without the agent repeating it.

First message
    
    
    Hi {{customer_name}}, thanks for calling Acme. Are you calling about order {{last_order}}?
    

Set it on the agent’s **Webhooks** page in the console (**Inbound call webhook**) or through `webhooks.conversation_init` in the config API, then publish. A slow or failing endpoint never blocks the call: after the configured timeout (up to 8 seconds, default 5) the call connects and every placeholder takes its configured [default value](https://docs.fish.audio/agents/build/dynamic-variables#default-values) (`Hi there, thanks for calling Acme.`). Set a default for each placeholder the first message depends on, or set the agent’s `on_missing` to `reject` if the call must not connect without them. To have callers pick an option before the agent answers, the way a phone menu does, add a [keypad menu](https://docs.fish.audio/agents/telephony/keypad). The choice fills a variable the same way.

## 

​

Phone sessions behave like any session

Nothing about a phone call needs special handling downstream:

  * **Transcript and tool timeline** : `GET /v1/agent/sessions/{session_id}` returns the conversation, including tool calls and results, when the agent [stores transcripts](https://docs.fish.audio/agents/monitor/conversation-history#what-gets-stored). See [Conversation history](https://docs.fish.audio/agents/monitor/conversation-history).
  * **Recording** : `GET /v1/agent/sessions/{session_id}/recording` returns signed URLs, one track per speaker, when the session was recorded.
  * **Post-call analysis** : summaries, data fields, and evaluation criteria run on phone sessions like any other. See [Post-call analysis](https://docs.fish.audio/agents/monitor/post-call-analysis).
  * **Webhooks** : `call.ended` and `call.analyzed` fire for phone sessions too. See [Webhooks](https://docs.fish.audio/agents/monitor/webhooks).
  * **Hang up via API** : end an in-progress call with `POST /v1/agent/sessions/{session_id}/end`.



## 

​

Going further

## Phone numbers

Number management and agent bindings.

## Versions & publishing

Control which configuration answers your calls.

## Post-call analysis

Extract structured data from every call.

## Webhooks

React to call lifecycle events from your backend.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/telephony/inbound-calls.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/telephony/inbound-calls)

[Bring Your Own Number](https://docs.fish.audio/agents/telephony/byo-sip)[Outbound Calls](https://docs.fish.audio/agents/telephony/outbound-calls)
