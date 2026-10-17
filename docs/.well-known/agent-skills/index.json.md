---
url: https://docs.fish.audio/.well-known/agent-skills/index.json
title: https://docs.fish.audio/.well-known/agent-skills/index.json
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:45.221330+00:00
---

# https://docs.fish.audio/.well-known/agent-skills/index.json

> Source: https://docs.fish.audio/.well-known/agent-skills/index.json

{"$schema":"https://schemas.agentskills.io/discovery/0.2.0/schema.json","skills":[{"name":"fish-audio-api","type":"skill-md","description":"Write direct HTTP / WebSocket calls to the Fish Audio platform (TTS, ASR, voice design, voice models, wallet, real-time TTS streaming) without depending on the Python or JavaScript SDK. Use when the user asks to call Fish Audio from curl, a language without an official SDK, an edge/runtime environment that cannot install the SDK, or when they explicitly want raw REST / WebSocket code. Covers authentication, endpoint URLs, required headers, request / response schemas, MessagePack vs JSON vs multipart encoding rules, multi-speaker dialogue, voice-design candidate generation, and the WebSocket streaming protocol.","url":"/.well-known/agent-skills/fish-audio-api/skill.md","digest":"sha256:47ffe4a3ba5e580ce55406aa287828ac55430cbf9ca06895e367fe7cb697e938"},{"name":"fish-audio-sdk","type":"skill-md","description":"Write code with the official Fish Audio SDKs, Python (`fishaudio`, PyPI `fish-audio-sdk`) and JavaScript/TypeScript (`fish-audio`). Use when the user wants text-to-speech, speech-to-text, voice cloning / voice-model management, or realtime WebSocket TTS through the installed SDK rather than raw HTTP. Covers install and auth, sync + async Python, the TypeScript client, exact method signatures and defaults, model selection (including the S2.1 typing caveat), the real exception types, and the Python↔JavaScript naming differences. For raw REST/WebSocket calls without an SDK (curl, unsupported languages, edge runtimes), use the `fish-audio-api` skill instead.","url":"/.well-known/agent-skills/fish-audio-sdk/skill.md","digest":"sha256:a4f19c9ff2684c38995f340619fcaa89f019bf18326106489096d38fb4ae0b65"}]}
