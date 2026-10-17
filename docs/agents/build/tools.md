---
url: https://docs.fish.audio/agents/build/tools/
title: Tools - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:46:40.842077+00:00
---

# Tools - Fish Audio

> Source: https://docs.fish.audio/agents/build/tools/

## On this page

  * Choose a tool type
  * Where tools live
  * Detach vs. delete
  * Manage tools over the API
  * Going further



Tools

# Tools

Copy pageCopy page

Give your agent the ability to act during a conversation: call your backend, trigger actions in your app, or use built-in capabilities

Copy pageCopy page

Out of the box, an agent can only talk. Tools let it act: fetch an order status mid-call, open a page in your app, or hang up when the conversation is over. You describe what a tool does and what arguments it takes; the agent decides when to call it.

## Webhook tools

The platform calls your HTTP endpoint and speaks the result.

## Client tools

Your application executes the tool through the SDK.

## System tools

Built-in capabilities you switch on per agent.

## 

​

Choose a tool type

Type| Executed by| Use it for  
---|---|---  
[Webhook](https://docs.fish.audio/agents/build/webhook-tools)| Fish Audio: we call your HTTP endpoint during the conversation| Order lookups, CRM reads, bookings, and anything else your backend can answer  
[Client](https://docs.fish.audio/agents/build/client-tools)| Your app: the SDK hands the call to code you register| Navigation, UI updates, device actions, and anything else only the client can do  
[System](https://docs.fish.audio/agents/build/system-tools)| The platform: no code involved| Hanging up the call  
  
Webhook and client tools are **custom tools** : you define a name, a description, and arguments, and the agent fills in the argument values when it calls. System tools are ready-made. Enable them with a switch on each agent.

## 

​

Where tools live

Custom tools are **workspace resources** , not part of a single agent. Define a `lookup_order` tool once and attach it to your support, sales, and after-hours agents. You manage them in two places:

  * **Builder → Tools** shows the tools attached to the agent you are editing, plus that agent’s system-tool switches. Tools you create here are attached to the agent immediately.
  * **The workspace tool library** lists every custom tool with how many agents use it. Tools you create here start unattached. Grant agents access afterwards.



Editing a shared tool updates the draft of **every** agent that uses it. Those agents show unpublished changes until they are published again. See [Versions & publishing](https://docs.fish.audio/agents/deploy/versions-publishing).

## 

​

Detach vs. delete

  * **Detach** is agent-scoped. Removing a tool from an agent in the Builder leaves the tool (and its other attachments) untouched.
  * **Delete** is workspace-wide. Deleting a tool from the library in the console detaches it from every agent that uses it, and those agents show unpublished changes.

Over the API, `DELETE` is stricter: it returns `409` while the tool is still attached to any agent. List the tool’s dependent agents first and detach it from each one.

## 

​

Manage tools over the API

Every endpoint requires your API key. See the [API introduction](https://docs.fish.audio/api-reference/introduction).

Endpoint| Description  
---|---  
`GET /v1/agent/tools`| List the custom tools in your workspace  
`POST /v1/agent/tools`| Create a tool: starts unattached  
`GET /v1/agent/tools/{tool_id}`| Retrieve a tool’s configuration  
`PATCH /v1/agent/tools/{tool_id}`| Update a tool: every field is optional  
`DELETE /v1/agent/tools/{tool_id}`| Delete a tool: returns `409` while any agent still uses it  
`GET /v1/agent/tools/{tool_id}/agents`| List the agents that use this tool  
  
Create a webhook tool:
    
    
    curl --request POST https://api.fish.audio/v1/agent/tools \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{
        "tool_type": "webhook",
        "name": "lookup_order",
        "description": "Look up the status of a customer order.",
        "arguments": [
          { "name": "order_number", "description": "The order number the caller provides." }
        ],
        "method": "GET",
        "url": "https://api.example.com/orders/{{order_number}}",
        "timeout_seconds": 10
      }'
    

Arguments can be referenced anywhere in the request with `{{name}}` placeholders. Before deleting a tool, check which agents depend on it:
    
    
    curl https://api.fish.audio/v1/agent/tools/{tool_id}/agents \
      --header "Authorization: Bearer $FISH_API_KEY"
    

The response lists each dependent agent’s `agent_id` and `name`, plus a `total` count. Field-level configuration (custom headers, request body templates, timeouts, error handling, and mock responses) is covered in [Webhook tools](https://docs.fish.audio/agents/build/webhook-tools).

## 

​

Going further

## Test it live

Call your draft agent before publishing.

## Versions & publishing

Drafts, published versions, and what “unpublished changes” means.

## Web SDK

Register client tool handlers in your application.

## API introduction

API keys for the endpoints above.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/build/tools.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/build/tools)

[Knowledge Base](https://docs.fish.audio/agents/build/knowledge-base)[Webhook Tools](https://docs.fish.audio/agents/build/webhook-tools)
