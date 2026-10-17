---
url: https://docs.fish.audio/agents/quickstart/
title: Quickstart - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:46:43.367530+00:00
---

# Quickstart - Fish Audio

> Source: https://docs.fish.audio/agents/quickstart/

## On this page

  * Next steps



Get Started

# Quickstart

Copy pageCopy page

Create a voice agent and have your first conversation in minutes

Copy pageCopy page

Build a voice agent and talk to it in a few minutes. Use the console for a no-code path, or provision everything over the API and connect from the browser with the SDK. **Prerequisites**

  * A Fish Audio account. Agents is in public beta and open to every account, no application needed.
  * For the API path: a Fish Audio API key. Create one under [API keys](https://fish.audio/app/api-keys/) in the console
  * Every account starts with a $5 trial balance, about 60 minutes of agent conversation. It pays for web, phone, and API sessions at the normal rates, including token-billed LLMs. After that, usage is billed per second against your API credit.



  * Dashboard

  * API




1

Create an agent

Go to [Agents](https://fish.audio/app/agents) and click **New agent**. Give it a name. You land in the Builder immediately.

2

Write the system prompt

On the **Configuration** page, write the system prompt that defines who your agent is and how it should behave (up to 32,000 tokens). Optionally set a **First message** so the agent opens the conversation.Edits save automatically as a draft.

3

Pick a voice

Choose a voice and a speaking language for your agent. You can pick from the featured voices or browse the full library. See [Voice & language](https://docs.fish.audio/agents/build/voice-language) for details.

4

Test it with a preview call

Click **Test call** in the top bar, then **Start call** in the panel. Your browser asks for microphone access, then you talk to the agent directly, with a live transcript, call timer, and mute and hang-up controls in the side panel.Preview calls always run against your current draft, so you can iterate on the prompt and immediately hear the difference. See [Preview calls](https://docs.fish.audio/agents/test/preview-calls).

5

Publish

Click **Publish** to turn the draft into an immutable version. Published versions are what real sessions connect to.You can keep editing the draft afterwards; nothing goes live until you publish again. See [Versions & publishing](https://docs.fish.audio/agents/deploy/versions-publishing).

1

Create an agent

Create the agent and configure it in one call. The `config` section is optional at creation time, and you can update it later with `PATCH /v1/agent/agents/{agent_id}/config`.

Create an agent
    
    
    curl --request POST https://api.fish.audio/v1/agent/agents \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{
        "name": "Support agent",
        "config": {
          "prompt": {
            "system_prompt": "You are a friendly support agent for Acme. Keep answers short and conversational."
          },
          "voice": {
            "voice_id": "802e3bc2b27e49c2995d23ef70e6ac89"
          }
        }
      }'
    

The response includes the agent’s `agent_id`. Use it as `$AGENT_ID` below. `voice_id` accepts any voice model id from the [Voice Library](https://docs.fish.audio/features/manage-voices).

`system_prompt` is limited to 32,000 tokens; longer prompts return `422`. Keeping it under 2,000 tokens is recommended for latency and cost.

2

Publish it

Sessions only run **published** configuration. Creating a session for an agent that has never been published returns `409`.

Publish the draft
    
    
    curl --request POST https://api.fish.audio/v1/agent/agents/$AGENT_ID/publish \
      --header "Authorization: Bearer $FISH_API_KEY"
    

Each publish creates an immutable version with an auto-incremented `version_number`.

3

Create a session

From your backend, exchange your API key for a short-lived session token. This is the credential the browser uses to join the call. Your API key never leaves your server.

Create a session
    
    
    curl --request POST https://api.fish.audio/v1/agent/sessions \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{ "agent_id": "'$AGENT_ID'", "timezone": "Asia/Tokyo" }'
    

`timezone` overrides the agent’s timezone for this session: replace it with your user’s IANA timezone. The default is UTC, which you can change in the agent’s configuration. See [Time & timezone](https://docs.fish.audio/agents/build/time-timezone).

Response
    
    
    {
      "session_id": "...",
      "expires_at": "2026-07-23T12:34:56Z",
      "max_duration_seconds": 1800,
      "transport": "livekit",
      "livekit_url": "wss://...",
      "token": "<participant token>"
    }
    

Return this response to your frontend as-is. `expires_at` is the deadline for joining the call.

4

Connect from the browser

Install the client SDK:

Install
    
    
    npm install @fishaudio/agent-client
    

Pass the session token to `AgentSession.start`. The SDK requests the microphone, connects, and streams audio both ways:

Connect and talk
    
    
    import { AgentSession } from "@fishaudio/agent-client";
    
    // sessionToken: the JSON response from POST /v1/agent/sessions,
    // fetched from your backend
    const session = await AgentSession.start({
      sessionToken,
      callbacks: {
        onUserTranscript: ({ text }) => console.log("You:", text),
        onAgentResponse: ({ text }) => console.log("Agent:", text),
      },
    });
    
    // When you are done:
    await session.end();
    

Start talking. You hear the agent reply and both sides of the conversation arrive as transcript events. See the [Web SDK](https://docs.fish.audio/agents/deploy/web-sdk) for the full event and method surface, or the [React SDK](https://docs.fish.audio/agents/deploy/react-sdk) for hooks.

5

Put it together

A complete local setup is one backend route that creates the session with your API key, and a page that starts the call. The frontend is served by Vite, which also proxies `/api` to the backend so the browser never sees your key.

Install
    
    
    npm init -y
    npm install express @fishaudio/agent-client
    npm install --save-dev vite
    

server.mjs
    
    
    import express from "express";
    
    const app = express();
    
    app.post("/api/voice-session", async (req, res) => {
      const upstream = await fetch("https://api.fish.audio/v1/agent/sessions", {
        method: "POST",
        headers: {
          Authorization: `Bearer ${process.env.FISH_API_KEY}`,
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          agent_id: process.env.AGENT_ID,
          timezone: "Asia/Tokyo", // your user's IANA timezone
        }),
      });
      if (!upstream.ok) {
        console.error("session creation failed:", upstream.status);
        return res.status(502).json({ error: "session_unavailable" });
      }
      res.json(await upstream.json());
    });
    
    app.listen(3001, () => console.log("backend on http://localhost:3001"));
    

vite.config.mjs
    
    
    export default {
      server: {
        proxy: { "/api": "http://localhost:3001" },
      },
    };
    

index.html
    
    
    <!doctype html>
    <button id="start">Start call</button>
    <button id="end" disabled>Hang up</button>
    <pre id="log"></pre>
    <script type="module" src="/main.js"></script>
    

main.js
    
    
    import { AgentSession } from "@fishaudio/agent-client";
    
    const startButton = document.getElementById("start");
    const endButton = document.getElementById("end");
    const log = (line) => (document.getElementById("log").textContent += line + "\n");
    
    let session;
    
    // Start from a click: browsers only grant the microphone and
    // audio playback inside a user gesture.
    startButton.onclick = async () => {
      const sessionToken = await fetch("/api/voice-session", { method: "POST" })
        .then((r) => r.json());
    
      session = await AgentSession.start({
        sessionToken,
        callbacks: {
          onUserTranscript: ({ text, final }) => final && log("You: " + text),
          onAgentResponse: ({ text }) => log("Agent: " + text),
          onDisconnect: ({ reason }) => log("Call ended: " + reason),
        },
      });
      startButton.disabled = true;
      endButton.disabled = false;
    };
    
    endButton.onclick = () => session?.end();
    

Run the two processes in separate terminals, then open the Vite URL (`http://localhost:5173`) and click **Start call** :

Run
    
    
    FISH_API_KEY=your_key AGENT_ID=your_agent_id node server.mjs
    npx vite
    

Every request and response on this path is in the [Agents API reference](https://docs.fish.audio/api-reference/endpoint/agent/create-agent-session). For production, keep the same shape: your backend owns the API key and returns session tokens, and the SDK runs in the page.

## 

​

Next steps

## Core concepts

Agents, drafts, versions, and sessions: how the pieces fit together.

## Web SDK

Events, transcripts, client tools, and audio controls in the browser.

## Agents API reference

Every endpoint with full request and response schemas.

## Knowledge base

Ground your agent in your own documents.

## Conversation history

Review transcripts, tool calls, and recordings.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/quickstart.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/quickstart)

[Overview](https://docs.fish.audio/agents/overview)[Concepts](https://docs.fish.audio/agents/concepts)
