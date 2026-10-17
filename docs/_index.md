---
url: https://docs.fish.audio
title: Overview - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:44.882238+00:00
---

# Overview - Fish Audio

> Source: https://docs.fish.audio

## On this page

  * Core features
  * Also in the web app
  * Models
  * Pick your path



Get Started

# Overview

Copy pageCopy page

Everything Fish Audio can do, and how to build with it

Copy pageCopy page

Fish Audio is a voice AI platform. Every core feature is available three ways: in the [web app](https://docs.fish.audio/overview/platform) (no code), through the [REST API](https://docs.fish.audio/api-reference/introduction), and via the official [SDK](https://docs.fish.audio/developer-guide/sdk-guide/quickstart).

## 

​

Core features

## Text to Speech

Convert text into lifelike speech with the `s2.1-pro`, `s2-pro`, and deprecated `s1` models.

## Speech to Text

Transcribe audio with `transcribe-1-pro`: multi-speaker conversations, long recordings, emotion cues, and optional timestamps.

## Voice Cloning

Clone a voice instantly from a clip, or train a persistent model.

## Realtime Streaming

Stream audio as it generates, for voice agents and live apps.

## Manage Voices

List, inspect, update, and delete your voice models.

## 

​

Also in the web app

These run in the browser, no code required. See the [Platform guide](https://docs.fish.audio/overview/platform).

## Professional Voice Clone

Clone a real, verified voice at studio quality, then release it.

## Voice Design

Design a voice from a plain-text description. Best for original characters.

## Voice Changer

Transform existing audio into a different voice.

## Story Studio

Produce multi-speaker, long-form audio: audiobooks and narration.

## Music & Sound Effects

Generate music and cinematic sound effects from a prompt.

## Audio Separation

Split audio into stems, and related processing utilities.

## 

​

Models

These text-to-speech models power most capabilities:

  * **`s2.1-pro`** : the recommended production model, with improved quality, latency, and throughput over S2-Pro.
  * **`s2.1-pro-free`** : the same model at $0 for testing, prototyping, development, and smaller businesses, without TTFA or DPA guarantees.
  * **`s2-pro`** : the previous-generation S2 model, with multi-speaker and natural-language expression control.
  * **`s1`** : the previous generation, with `(parenthesis)` emotion tags. S1 is deprecated and will be retired on December 31, 2026. After that date, requests that specify `s1` are served by `s2.1-pro`. See [Migrate from S1](https://docs.fish.audio/developer-guide/models-pricing/migrate-from-s1).

For speech to text, select the model with the `model` header on `POST /v1/asr`:

  * **`transcribe-1-pro`** : the recommended model, for everything from short clips to multi-speaker conversations (speaker markers and speaker turns) and long recordings, with inline emotion cues. Send `model: transcribe-1-pro` explicitly.
  * **`transcribe-1`** : general transcription of short recordings. A request whose `model` header is missing or not an exact match is served by this model.

See [Models Overview](https://docs.fish.audio/developer-guide/models-pricing/models-overview) and [Choosing a Model](https://docs.fish.audio/developer-guide/models-pricing/choosing-a-model) for the full lineup and languages, and [Speech to Text](https://docs.fish.audio/features/speech-to-text#input-audio) for transcription formats and limits.

## 

​

Pick your path

## Use the web app

No code: generate audio, clone voices, and produce projects in your browser.

## Build with the SDK

The Python library for your application.

## Call the API

Raw REST and WebSocket endpoints for any language.

## Use your AI coding agent

Install the Fish Audio skill so your agent writes correct code.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/overview/capabilities.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/overview/capabilities)

[Get Your API Key](https://docs.fish.audio/developer-guide/getting-started/api-key)
