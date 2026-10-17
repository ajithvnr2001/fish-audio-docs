---
url: https://docs.fish.audio/agents/test/preview-calls/
title: Preview Calls - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:03.161747+00:00
---

# Preview Calls - Fish Audio

> Source: https://docs.fish.audio/agents/test/preview-calls/

## On this page

  * Start a preview call
  * During the call
    * Live transcript
    * Tool calls
    * Controls
  * Drafts, not published versions
  * After the call
  * Going further



Test

# Preview Calls

Copy pageCopy page

Talk to your draft agent in a live voice call, right in the Builder

Copy pageCopy page

Preview calls let you hold a live voice conversation with your agent without leaving the Builder. Every call runs against your current **draft** configuration: edit the system prompt, pick a different voice, and call again to hear the difference immediately, no publish required.

## 

​

Start a preview call

1

Open your agent in the Builder

Preview works from any Builder section: Configuration, Tools, Knowledge base, and so on.

2

Click Test call

The **Test call** button in the top bar opens the Preview panel on the right side of the Builder.

3

Click Start call

Your browser asks for microphone access the first time. The call cannot start without a microphone: if you deny permission, the panel tells you to allow access in your browser settings and try again.

4

Talk to your agent

Once connected, the status pill shows **Live** with a running call timer. The agent opens the call according to your [first message settings](https://docs.fish.audio/agents/build/configuration), and the conversation begins.

The panel stays connected while you switch between Builder sections, so you can read your configuration mid-call. Navigating away from the Builder (back to the agent list, for example) hangs up. If the call fails to connect, the panel shows an error state and lets you retry; a connection drop mid-call simply ends the call.

## 

​

During the call

### 

​

Live transcript

The panel shows both sides of the conversation as it happens:

  * **Your speech** appears as it is transcribed, updating in place while you talk and settling when you finish a turn.
  * **Agent replies** stream in as text while the agent speaks them aloud.



### 

​

Tool calls

When the agent invokes a [tool](https://docs.fish.audio/agents/build/tools), the call appears inline in the transcript as a compact entry that flips from running to done or failed. Expand an entry to inspect the exact arguments the model sent and the response it received, as formatted JSON truncated at 4 KB.

Preview calls run your real configuration. [Webhook tools](https://docs.fish.audio/agents/build/webhook-tools) send real HTTP requests to your endpoints. Point them at a staging environment if you want to avoid side effects while testing.

### 

​

Controls

Control| Behavior  
---|---  
Mute| Toggles your microphone without ending the call  
End call| Ends the call and returns the panel to its ready state  
Timer| Shows elapsed time; preview calls are capped at 10 minutes (600 seconds), or the agent’s configured maximum call duration, whichever is lower  
  
## 

​

Drafts, not published versions

Preview calls and production sessions read different configurations:

Session| Configuration used  
---|---  
Preview call| Latest draft, autosaved as you edit in the Builder  
Production session| The published version, unchanged until you publish again  
  
This makes preview the fast inner loop: tweak the prompt, call, listen, repeat, and [publish](https://docs.fish.audio/agents/deploy/versions-publishing) when the draft is ready.

After a config change, hang up and start a new call. A preview call reflects the draft as it stood when the session was created.

## 

​

After the call

Preview sessions are built for iteration, not record-keeping:

  * **Post-call analysis runs in the panel.** If you have [post-call analysis](https://docs.fish.audio/agents/monitor/post-call-analysis) configured, ending the call triggers it and the results (summary, extracted data fields, and per-criterion success / failure / unknown verdicts) appear directly in the panel. Analysis runs however the call ends (including the automatic time limit or closing the tab mid-call), but results are viewable only in the panel.
  * **Nothing enters conversation history.** Preview calls never appear in [conversation history](https://docs.fish.audio/agents/monitor/conversation-history), and the transcript is not preserved after you hang up.
  * **No post-call webhook fires.** Preview sessions never trigger the `call.analyzed` [post-call webhook](https://docs.fish.audio/agents/monitor/webhooks), so Builder debugging doesn’t push analysis results to your production systems.



## 

​

Going further

## Agent tests

Scripted conversations with automated Pass/Fail judging: catch regressions without listening by ear.

## Versions & publishing

Ship the draft you just previewed as an immutable published version.

## Post-call analysis

Configure summaries, data extraction, and success criteria. Results show up in the preview panel.

## Web SDK

Put the same voice conversation in your own app.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/test/preview-calls.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/test/preview-calls)

[Custom LLM](https://docs.fish.audio/agents/build/custom-llm)[Agent Tests](https://docs.fish.audio/agents/test/agent-tests)
