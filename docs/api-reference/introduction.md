---
url: https://docs.fish.audio/api-reference/introduction/
title: Introduction - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:22.730033+00:00
---

# Introduction - Fish Audio

> Source: https://docs.fish.audio/api-reference/introduction/

## On this page

  * Welcome
  * Quick Start
  * Errors
  * OpenAPI Schema
  * Distributed Tracing
  * Create a Voice Clone
  * Generate Speech
  * Design a Voice
  * Real-time Streaming
  * Rate Limits



API Reference

# Introduction

Copy pageCopy page

How to use the Fish Audio API

Copy pageCopy page

## 

​

Welcome

You can generate a new API key at <https://fish.audio/app/api-keys/>.

## 

​

Quick Start

See our [Quick Start](https://docs.fish.audio/developer-guide/getting-started/quickstart) guide to generate audio in under 2 minutes.

## 

​

Errors

Errors return a JSON body with a `message` and a `status`; some endpoints add fields. Errors from the network edge in front of the API, such as some `413` or `5xx` responses, may not have a JSON body. See [Errors](https://docs.fish.audio/api-reference/errors) for the full status-code table, retry guidance, and SDK exception handling.

## 

​

OpenAPI Schema

Fish Audio publishes a canonical OpenAPI schema at <https://api.fish.audio/openapi.json>. When working with AI coding agents or IDE assistants, mention this schema URL as part of your prompt or project context so the agent can understand Fish Audio’s endpoints, request and response models, authentication requirements, and supported parameters directly from the machine-readable API contract.

## 

​

Distributed Tracing

Fish Audio inference APIs accept the W3C `traceparent` header so your business-side trace and Fish Audio’s inference-side trace can share the same trace ID. See [Tracing & Performance Analysis](https://docs.fish.audio/api-reference/observability) for supported endpoints, examples, and enterprise performance analysis details.

## 

​

Create a Voice Clone

Use our [/model endpoint](https://docs.fish.audio/api-reference/endpoint/model/create-model) to create a voice clone model.

## 

​

Generate Speech

Use our [/v1/tts endpoint](https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech) to generate speech.

## 

​

Design a Voice

Use our [/v1/voice-design endpoint](https://docs.fish.audio/api-reference/endpoint/openapi-v1/voice-design) to generate candidate voices from a prompt.

## 

​

Real-time Streaming

Use our [Python SDK](https://docs.fish.audio/features/realtime-streaming) or [JavaScript SDK](https://docs.fish.audio/features/realtime-streaming) for real-time audio streaming with WebSocket.

## 

​

Rate Limits

You can find the rate limits for each endpoint in the [Rate Limits](https://docs.fish.audio/developer-guide/models-pricing/pricing-and-rate-limits) section.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/introduction.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/introduction)

[Tracing & Performance Analysis](https://docs.fish.audio/api-reference/observability)
