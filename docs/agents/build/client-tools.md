---
url: https://docs.fish.audio/agents/build/client-tools/
title: Client Tools - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:46:40.736654+00:00
---

# Client Tools - Fish Audio

> Source: https://docs.fish.audio/agents/build/client-tools/

## On this page

  * How it works
  * Declare a client tool
    * Naming rules
  * Handle the call in your app
    * What the agent receives
  * Fire-and-forget tools
  * Observe tool activity
  * Going further



Tools

# Client Tools

Copy pageCopy page

Let the agent trigger actions in your own app: declared on the agent, executed by your code through the SDK

Copy pageCopy page

Client tools run inside your application, not on Fish Audio’s servers. You declare the tool on the agent (name, description, parameters) and register a handler in your app with the [Web SDK](https://docs.fish.audio/agents/deploy/web-sdk). When the agent decides to call the tool mid-conversation, the SDK invokes your handler and returns its result to the agent. Use client tools for anything only your frontend can do: navigate to a page, highlight a product, open a modal, read app state, or hand off to a human.

Client tools need code on your side. For tools that call an HTTP endpoint from Fish Audio’s side, use [webhook tools](https://docs.fish.audio/agents/build/webhook-tools). For built-in capabilities like hanging up, see [system tools](https://docs.fish.audio/agents/build/system-tools).

## 

​

How it works

1

Declare the tool on the agent

Add a tool of type `client` to the agent’s tool list, alongside any webhook tools. The name, description, and arguments tell the model what the tool does and when to call it.

2

Register a handler in your app

Pass a handler for the same tool name when starting a session with `@fishaudio/agent-client`.

3

The agent calls the tool

During the conversation, the agent invokes the tool with parameter values. The SDK dispatches the call to your handler.

4

Your result goes back to the agent

The handler’s return value is JSON-serialized and sent back, and the agent continues with the result, unless the tool is fire-and-forget.

## 

​

Declare a client tool

Client tools sit alongside webhook tools in the agent’s tool list. A declaration looks like this:

Tool definition
    
    
    {
      "tool_type": "client",
      "name": "highlight_product",
      "description": "Visually highlight a product on the page the user is viewing.",
      "arguments": [
        { "name": "product_id", "description": "ID of the product to highlight." }
      ],
      "expects_response": true
    }
    

Field| Description  
---|---  
`name`| How the model refers to the tool. Must match the name you register in the SDK exactly  
`description`| Tells the model what the tool does and when to use it  
`arguments`| Named inputs the model fills in; delivered to your handler as one JSON object  
`expects_response`| Whether the agent waits for your handler’s return value before continuing  
  
### 

​

Naming rules

Tool names must match `^[a-zA-Z][a-zA-Z0-9_-]{0,63}$`: start with a letter, then letters, digits, underscores, or hyphens, up to 64 characters total.

  * Built-in tools live under a leading underscore (like `_transfer_call`), which the pattern makes unreachable.
  * Names must be unique per agent. Declaring a duplicate fails with a `400`.



## 

​

Handle the call in your app

Register handlers with the `clientTools` option when starting a session, or later with `registerClientTool`:

At session start

After session start
    
    
    import { AgentSession } from "@fishaudio/agent-client";
    
    const session = await AgentSession.start({
      agentId: "YOUR_AGENT_ID",
      clientTools: {
        highlight_product: async (params) => {
          const el = document.getElementById(String(params.product_id));
          el?.scrollIntoView({ behavior: "smooth" });
          el?.classList.add("highlighted");
          return { highlighted: true };
        },
      },
    });
    
    
    
    session.registerClientTool("open_page", (params, { callId, toolName }) => {
      window.location.assign(`/products/${String(params.product_id)}`);
    });
    

A handler receives the parameter values as a single object, plus a context object with `callId` and `toolName`. It can be synchronous or async:

Handler signature
    
    
    type ClientToolHandler = (
      params: Record<string, unknown>,
      ctx: { callId: string; toolName: string },
    ) => unknown | Promise<unknown>;
    

Parameter values are produced by the model. Validate them in your handler before acting on them, just as you would any external input.

### 

​

What the agent receives

Handler outcome| Result  
---|---  
Returns a value| JSON-serialized and sent back to the agent  
Throws| An error result is sent back; the SDK emits an `error` event with code `tool_failed`  
Exceeds the timeout (default 15 s)| An error result is sent back automatically; code `tool_timeout`  
Tool called but no handler registered| An error result is sent back automatically  
Returns a value that cannot be sent: larger than about 60 KB serialized (`MAX_CLIENT_TOOL_RESULT_BYTES`) or not JSON-serializable| An error result explaining why is sent back instead (SDK 0.2.1 and later); code `tool_failed`  
  
The agent is never left hanging: while `expects_response` is `true` the agent suspends that tool call until your result arrives or the timeout fires, then continues either way. Errors and timeouts return to the model as tool errors, so the agent can recover in conversation (“I couldn’t open that page. Let me try something else”). Keep results small: they travel over the realtime data channel, which caps a message at 64 KB, and the model reads the whole result on every turn. Return a summary or a reference (an id, a URL) rather than a large payload. To change the handler timeout, pass `clientToolTimeoutMs` (in milliseconds) when starting the session. Note there is a second, server-side deadline: the agent stops waiting after the tool’s `timeout_seconds` (default 30 s, settable 1–120 on the tool), and a handler result arriving after that is ignored, so `clientToolTimeoutMs` can only tighten the client-side deadline, not extend the agent’s wait.

## 

​

Fire-and-forget tools

Set `expects_response` to `false` for tools that are pure side effects: the agent triggers your handler and keeps talking without waiting. Any return value is ignored. This suits UI actions where confirmation adds nothing: scrolling, opening a panel, firing an analytics event. If the agent should react to the outcome (“the page is open, now walk the user through it”), keep `expects_response: true`.

## 

​

Observe tool activity

Every tool call (client and webhook alike) emits `toolCallStarted`, `toolCallCompleted`, and `toolCallFailed` events on the session, with the call ID, tool name, and payloads. The events are on by default; sessions created with `tool_events: false` don’t emit them. Use them to render tool activity in your UI. See the [Web SDK](https://docs.fish.audio/agents/deploy/web-sdk) for the event reference.

## 

​

Going further

## Web SDK

Full `@fishaudio/agent-client` API: sessions, events, audio.

## Webhook tools

Tools that call your HTTP endpoints server-side.

## System tools

Built-in capabilities you toggle per agent.

## Tools overview

How the agent chooses and combines tools.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/build/client-tools.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/build/client-tools)

[Webhook Tools](https://docs.fish.audio/agents/build/webhook-tools)[System Tools](https://docs.fish.audio/agents/build/system-tools)
