---
url: https://docs.fish.audio/overview/mcp/
title: MCP Server - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-20T12:52:01.114033+00:00
---

# MCP Server - Fish Audio

> Source: https://docs.fish.audio/overview/mcp/

## On this page

  * Connect
  * Try it
  * Tools
  * Credits
  * Good to know



MCP Server

# MCP Server

Copy pageCopy page

Connect Claude, Cursor, or another MCP client to your Fish Audio account for voices, speech, images, video, and Story Studio

Copy pageCopy page

The Fish Audio MCP server gives AI agents direct access to your Fish Audio account: they can browse the voice library, clone a voice, generate speech, transcribe audio, generate or edit images and videos, and produce multi-speaker [Story Studio](https://fish.audio/app/story-studio) projects for you.

  * **Endpoint** : `https://api.fish.audio/mcp` (streamable HTTP)
  * **Authentication** : OAuth. Your MCP client opens a browser window, you sign in with your Fish Audio account, and choose the team the connection works in.
  * **Billing** : usage is billed the same way as the [web app](https://fish.audio/app), not through the developer API. See Credits for what each tool costs.



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
    
    
    codex mcp add fish-audio --url https://api.fish.audio/mcp
    

Codex opens the browser sign-in when it adds the server. If it doesn’t, run `codex mcp login fish-audio`. Verify with `codex mcp list`.

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

Tools

The [tools reference](https://docs.fish.audio/overview/mcp/tools) lists what each tool does, by area:

  * [Voices](https://docs.fish.audio/overview/mcp/tools#voices): search the voice library and clone voices
  * [Speech and transcription](https://docs.fish.audio/overview/mcp/tools#speech-and-transcription): text to speech and speech to text
  * [File uploads](https://docs.fish.audio/overview/mcp/tools#file-uploads): local files for transcription, cloning, and generation
  * [Images and video](https://docs.fish.audio/overview/mcp/tools#images-and-video): models, estimates, and generation
  * [Story Studio](https://docs.fish.audio/overview/mcp/tools#story-studio): long-form, multi-speaker audio projects
  * [Asset library](https://docs.fish.audio/overview/mcp/tools#asset-library): saved files, folders, and avatars
  * [Account and feedback](https://docs.fish.audio/overview/mcp/tools#account-and-feedback): credits, workspaces, and feedback to Fish Audio



## MCP tools reference

The tools the server exposes, with the exact tool names and what each one does.

## 

​

Credits

Tool or area| Cost  
---|---  
Speech (`text_to_speech`)| 1 credit per UTF-8 byte of text, audio tags included  
Story Studio audio (`studio_generate`, `studio_export`)| 1 credit per UTF-8 byte of text; blocks with up-to-date audio are free  
Transcription (`speech_to_text`)| By length of audio; `flash` costs less than `pro`  
Images and video| The price in the estimate  
  
In UTF-8, English letters, digits, and basic punctuation are one byte each, and most Chinese, Japanese, and Korean characters are three. Voice search and cloning, uploads, Story Studio import and editing, estimates and quotes, and the asset library are free. Speech and Story Studio audio in another team’s [professional voice clone](https://docs.fish.audio/overview/platform/create-voice/professional-voice-clone) cost double, and failed generations are refunded.

## 

​

Good to know

  * Add [audio tags](https://docs.fish.audio/developer-guide/core-features/emotions) in square brackets inside the text to control delivery, such as `[whispering]`, `[excited]`, or `[laughing]`.
  * If no voice is specified, a curated default voice for the requested language is used.
  * Local files for transcription or cloning go to temporary storage that is deleted after 7 days, while files you upload as inputs for image or video generation are kept in your workspace.
  * The agent asks you to approve an image or video estimate before it generates; if the credit price changes before it submits, nothing is charged and the agent asks you again.
  * Every account sees the same tools, and plan requirements are checked when a tool runs.
  * Video (including lip sync and talking avatars) needs a Plus plan or higher, and Story Studio export needs a paid plan.
  * Free plans limit how many images you can generate, and your [plan](https://fish.audio/app/billing) sets how many private or unlisted voices you can keep.
  * The estimate or quote tells you when a request is over your plan, before anything is charged.
  * New voice clones are unlisted by default, so anyone with the voice ID can use them; ask for a private voice to keep one to your workspace.
  * Generated audio, images, and videos are returned as permanent links that anyone with the link can open.
  * A connection is bound to the team you chose at sign-in; to work in another team, add the server again and choose that team.
  * Voice, speech, transcription, and Story Studio tools use your team’s default workspace, while image, video, and asset library tools use the workspace you choose (`list_my_workspaces` lists them).
  * Tools can change between releases; reconnect your client to refresh its tool list.



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/overview/mcp.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/overview/mcp)

[Voice Design](https://docs.fish.audio/overview/platform/create-voice/voice-design)[Tools](https://docs.fish.audio/overview/mcp/tools)
