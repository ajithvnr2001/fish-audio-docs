---
url: https://docs.fish.audio/developer-guide/getting-started/changelog/
title: Changelog - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-20T12:52:01.189840+00:00
---

# Changelog - Fish Audio

> Source: https://docs.fish.audio/developer-guide/getting-started/changelog/

FiltersClear

Fish SpeechFish Audio

Get Started

# Changelog

Copy pageCopy page

Complete release history and version updates for all Fish Audio products

Copy pageCopy page

​

More normalization languages

Fish Audio

October 20, 2026

## 

​

More normalization languages

Text normalization now has rules for Turkish (`tr`) and Tagalog (`tl`, `fil`), and Portuguese follows Brazilian conventions, so `pt-BR` is supported too. Without `language`, Turkish and Tagalog text is detected, and Chinese written mostly in Traditional characters uses the Traditional Chinese rules.[Supported normalization languages](https://docs.fish.audio/features/text-to-speech#supported-normalization-languages)

​

TTS language field

Fish Audio

October 16, 2026

## 

​

TTS language field

Text-to-speech requests accept an optional `language` field, a BCP-47 tag of the text such as `en`, `es-MX`, or `zh-TW`. It selects the rules used to spell out numbers, dates, units, and symbols before synthesis, and the language used for word timestamps. It does not change the voice, accent, or audio quality. Omit it to keep detecting the language per text chunk.Available on `POST /v1/tts`, the with-timestamps routes, and the WebSocket start event. The official SDKs don’t expose it yet.[Language](https://docs.fish.audio/features/text-to-speech#language) | [Supported normalization languages](https://docs.fish.audio/features/text-to-speech#supported-normalization-languages)

​

Drama 3

Fish Audio

October 13, 2026

## 

​

Drama 3

Text-to-speech model you direct in plain language. Describe tone, pacing, and character without a fixed set of audio tags.Use model ID `drama-3` in the API.[Drama 3 guide](https://docs.fish.audio/features/text-to-speech/drama-3) | [Text to Speech API](https://docs.fish.audio/api-reference/endpoint/openapi-v1/text-to-speech)

​

Fish Audio S1 retirement

Fish Audio

October 8, 2026

## 

​

Fish Audio S1 retirement

S1 is deprecated and will be retired on December 31, 2026. After that date, requests that specify `s1` are served by `s2.1-pro` and billed as `s2.1-pro`, at the same price.To migrate, switch the model ID to `s2.1-pro` and convert `(parenthesis)` emotion tags to `[bracket]` tags.[Migrate from S1](https://docs.fish.audio/developer-guide/models-pricing/migrate-from-s1) | [Model deprecations](https://docs.fish.audio/developer-guide/models-pricing/deprecations)

​

Transcribe 1 Pro

Fish Audio

September 18, 2026

## 

​

Transcribe 1 Pro

Speech-to-text model for short clips and long recordings, including multi-speaker conversations. Transcripts can include inline speaker markers, speaker turns, and emotion and vocal-event cues.Use model ID `transcribe-1-pro` on `POST /v1/asr`[Speech to Text](https://docs.fish.audio/features/speech-to-text) | [Models overview](https://docs.fish.audio/developer-guide/models-pricing/models-overview)

​

Fish Audio S2.1 Pro

Fish Audio

June 23, 2026

## 

​

Fish Audio S2.1 Pro

Production text-to-speech model that improves on S2-Pro in quality, latency, and throughput. Supports 83 languages on one model, with the same `[bracket]` natural-language control and multi-speaker dialogue as S2.Use model ID `s2.1-pro` for production workloads that need TTFA and DPA guarantees. `s2.1-pro-free` is the same model at no cost through November 30, 2026 for testing, prototyping, development, and smaller businesses, under fair-use limits and without those guarantees.[Read more about S2.1 Pro](https://fish.audio/blog/s2-1-pro-free-api/) | [Models overview](https://docs.fish.audio/developer-guide/models-pricing/models-overview)

​

Fish Audio S2

Fish Audio

March 2026

## 

​

Fish Audio S2

Next-generation text-to-speech model with inline emotion cues, multi-speaker dialogue support, and 80+ languages.S2 introduces `[bracket]` syntax for natural language control over emotion and paralinguistic cues (e.g., `[whisper]`, `[laugh]`, `[emphasis]`). Tags are treated as standard text rather than dedicated control tokens, so you are not limited to a fixed set of expressions. Built on the Qwen3-4B backbone and fully open-source.Use model ID `s2-pro` in the API. At launch, S1 remained supported for existing integrations; it is now deprecated and will be retired on December 31, 2026 (see [Migrate from S1](https://docs.fish.audio/developer-guide/models-pricing/migrate-from-s1)).[GitHub](https://github.com/fishaudio/fish-speech) | [HuggingFace](https://huggingface.co/fishaudio)

​

Fish Audio S1

Fish Audio

June 2025

## 

​

Fish Audio S1

Historic rebrand from Fish Speech to Fish Audio. #1 ranking on TTS-Arena2 with industry-leading performance.S1 (4B params): 0.008 WER, 0.004 CER - Available on Fish Audio Playground S1-mini (0.5B params): 0.011 WER, 0.005 CER - Open source on Hugging Face64+ emotional expressions with RLHF integration and multilingual support for English, Chinese, Japanese, and more.[Read More about S1](https://fish.audio/blog/introducing-s1/)

​

v1.5.1

Fish Speech

May 27, 2025

## 

​

v1.5.1

Fixed critical PyTorch security settings and improved inference speed significantly. Added ONNX export support for better deployment options and enhanced text processing for Arabic and Hebrew languages. Includes bug fixes for Apple Silicon (MPS) compatibility and reorganized library structure for cleaner codebase.

​

v1.5.0

Fish Speech

December 21, 2024

## 

​

v1.5.0

Introduced v1.5 model architecture with improved dataset handling and bearer token authentication for APIs.Added reference audio caching by hash for faster performance and better Apple Silicon support. Includes OpenAPI documentation refactoring and base64 reference data support in JSON format.

​

v1.4.3

Fish Speech

November 23, 2024

## 

​

v1.4.3

Introduced Fish Agent for conversational AI with streaming capabilities and real-time interactions.Added comprehensive Korean language documentation and fixed critical non-English speech issues. Improved WebUI streaming functionality and PyTorch version compatibility.

​

v1.4.2

Fish Speech

October 25, 2024

## 

​

v1.4.2

Documentation-focused release with comprehensive updates for v1.4, macOS support, and multiple language translations.Improved Docker support and API enhancements for JSON format handling. Added audio selection to WebUI and fixed various stability issues including cache handling and backend performance.

​

v1.4.1

Fish Speech

September 15, 2024

## 

​

v1.4.1

Infrastructure improvements focused on Docker optimization and multi-platform builds.Updated PyTorch version and replaced audio backend from sox for better performance. Enhanced CI/CD pipeline with buildx support and fixed various Docker-related issues.

​

v1.4.0

Fish Speech

September 12, 2024

## 

​

v1.4.0

Major release with new VQGAN architecture for improved audio quality and faster inference.Updated WebUI with enhanced interface and better language switching. Added Japanese documentation translation and fixed inference warmup issues for better performance.

​

v1.2.1

Fish Speech

September 8, 2024

## 

​

v1.2.1

Replaced Whisper with SenseVoice for better ASR and added native Apple Silicon support.Includes Portuguese (Brazil) localization, streaming audio functionality, and CPU-only inference improvements. Pinned PyTorch to 2.3.1 to fix inference speed issues and aligned API with official closed-source version.

​

v1.2

Fish Speech

July 18, 2024

## 

​

v1.2

Introduced auto-reranking system for better results along with bilingual support and model quantization.Replaced standard Whisper with Faster Whisper for improved speed and added Japanese documentation. Enhanced model stability and inference performance with optimized v1.2 architecture.

​

v1.1.2

Fish Speech

June 27, 2024

## 

​

v1.1.2

Minor release adding Chinese text normalization support and a streaming audio download button in the WebUI.Fixed LoRA merging issues and improved Firefly performance.

​

v1.1.1

Fish Speech

June 8, 2024

## 

​

v1.1.1

Breaking changes: Replaced zibai with uvicorn for API server, new text-splitter with byte-based length calculation, and license change to CC-BY-NC-SA 4.0.Added Apple Silicon (MPS) support, Windows one-click installation, and automatic model downloading with resume capability. Improved WebUI with better file selection and download progress indicators.

​

v1.1.0

Fish Speech

May 11, 2024

## 

​

v1.1.0

Added VITS decoder integration with full streaming support and queue management for real-time audio generation.Introduced internationalization (i18n) with Spanish translation and improved Windows packaging. Optimized GPU memory usage and CPU-only inference performance while adding LoRA support to the Gradio UI.

​

v1.0.0

Fish Speech

April 30, 2024

## 

​

v1.0.0

Major milestone release introducing new VQ-GAN architecture with VITS decoder support, LoRA fine-tuning, and streaming inference capabilities.Breaking changes include removal of the Rust-based data server, new tokenizer replacing phonemizer, and updated model architecture (VQ + DiT + Reflow). Achieved 4x memory reduction during loading and added WebUI for training and annotation.

​

v0.2.0

Fish Speech

December 23, 2023

## 

​

v0.2.0

First public release of Fish Speech featuring a complete text-to-speech pipeline with VQ-GAN audio codec and LLAMA-based language model.Includes multi-language support (Chinese, English, Japanese), Gradio WebUI for inference, HTTP API server, and Docker support. Added special optimizations for Chinese users including mirror downloads and localized documentation.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/getting-started/changelog.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/getting-started/changelog)

[Coding Assistants](https://docs.fish.audio/developer-guide/resources/agent-quickstart)[Overview](https://docs.fish.audio/features/text-to-speech)
