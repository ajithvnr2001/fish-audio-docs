---
url: https://docs.fish.audio/overview/mcp/
title: MCP Server - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:41.305777+00:00
---

# MCP Server - Fish Audio

> Source: https://docs.fish.audio/overview/mcp/

## On this page

  * Connect
  * Try it
  * Good to know



Platform (Web App)

# MCP Server

Copy pageCopy page

Connect Claude, Cursor, or any MCP client to your Fish Audio account: search voices, generate speech, transcribe audio, and create images and videos

Copy pageCopy page

The Fish Audio MCP server gives AI agents direct access to your Fish Audio account: they can browse the voice library, generate speech, transcribe audio, and generate or edit images and videos for you.

  * **Endpoint** : `https://api.fish.audio/mcp` (streamable HTTP)
  * **Authentication** : OAuth. Your MCP client opens a browser window, you sign in with your Fish Audio account, and choose the team the connection works in.
  * **Billing** : usage draws from your plan’s package credits, exactly like the [web app](https://fish.audio/app). It does not consume developer API credits. Image and video generation is quoted first, and the agent asks you to confirm the price before it generates.



## 

​

Connect

  * Claude Code

  * Claude.ai

  * Cursor

  * Codex CLI

  * Windsurf



    
    
    claude mcp add --transport http fish-audio https://api.fish.audio/mcp
    

Run `/mcp` inside Claude Code to sign in, then ask “Generate a short greeting with a warm English voice.”

Go to **Settings → Connectors → Add custom connector** and enter `https://api.fish.audio/mcp`. Claude walks you through the sign-in.

Open the command palette (`Cmd/Ctrl+Shift+P`) → “Open MCP settings” → “Add custom MCP”, and add:
    
    
    {
      "mcpServers": {
        "fish-audio": { "url": "https://api.fish.audio/mcp" }
      }
    }
    

Cursor prompts you to sign in on first use.
    
    
    codex mcp add fish-audio https://api.fish.audio/mcp
    codex mcp login fish-audio
    

`codex mcp login` opens the browser sign-in. Verify with `codex mcp list`.

Go to `Settings → Cascade → MCP Servers → View raw config` (`~/.codeium/windsurf/mcp_config.json`) and add:
    
    
    {
      "mcpServers": {
        "fish-audio": { "url": "https://api.fish.audio/mcp" }
      }
    }
    

## 

​

Try it

Once connected, ask in plain language and the agent picks the right tools. Click a card to copy its prompt; the copied text also names the server, so the agent can help you connect it if you have not yet.

In coding agents like Claude Code and Codex, tools compose with the shell: the agent can download generated audio, images, and videos with `curl`, upload local recordings for transcription or reference images for editing, or batch-generate a directory of scripts.

## 

​

Good to know

  * Add audio tags in square brackets inside the text to control delivery: `[whispering]`, `[excited]`, `[laughing]`. Tags are performed, never spoken.
  * If no voice is specified, a curated default voice for the requested language is used.
  * Local files can be transcribed too. The agent uploads them to a temporary slot that is deleted automatically after 7 days.
  * Before an image or video is generated, the agent requests a credit estimate and asks you to confirm it. The server re-checks the price when the job is submitted and never charges more than the amount you approved.
  * Video generation needs a Plus plan or higher. Free plans have a daily image allowance and a smaller image count per request; the estimate reports these limits before you are asked to approve anything.
  * Reference images for editing or image-to-video are JPEG, PNG, or WebP files up to 20 MB. The agent uploads them for you, and an image it just generated can be reused as input without downloading it.
  * Generated audio, images, and videos are returned as permanent URLs; failed generations are refunded.
  * A connection is bound to the team you chose at sign-in. To work in another team, add the server again and choose that team.



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/overview/mcp.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/overview/mcp)

[Voice Design](https://docs.fish.audio/overview/platform/create-voice/voice-design)[Models Overview](https://docs.fish.audio/developer-guide/models-pricing/models-overview)
