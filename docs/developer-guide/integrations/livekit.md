---
url: https://docs.fish.audio/developer-guide/integrations/livekit/
title: LiveKit - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:31.721487+00:00
---

# LiveKit - Fish Audio

> Source: https://docs.fish.audio/developer-guide/integrations/livekit/

## On this page

  * Prerequisites
  * Installation
  * Configuration
  * Basic usage
    * Key parameters
    * Streaming modes
  * Resources



Integrations

# LiveKit

Copy pageCopy page

Build real-time voice AI agents with Fish Audio and LiveKit

Copy pageCopy page

[LiveKit Agents](https://github.com/livekit/agents) is an open source framework for building real-time voice and multimodal AI agents. It handles streaming audio pipelines, turn detection, interruptions, and LLM orchestration so you can focus on your agent’s behavior. Fish Audio integrates with LiveKit through the `fishaudio` plugin, providing text-to-speech synthesis with support for both chunked and real-time WebSocket streaming modes.

## 

​

Prerequisites

  * A [Fish Audio account](https://fish.audio) with an API key
  * Python 3.9 or higher



## 

​

Installation

Install LiveKit Agents with Fish Audio support:
    
    
    pip install "livekit-agents[fishaudio]"
    

## 

​

Configuration

Set your Fish Audio API key as an environment variable:
    
    
    export FISH_API_KEY=your_api_key_here
    

## 

​

Basic usage

Add Fish Audio TTS to your LiveKit agent:
    
    
    from livekit.plugins.fishaudio import TTS
    
    tts = TTS(
        reference_id="your_voice_model_id",  # Optional: use a specific voice
        model="s2.1-pro",
        sample_rate=24000,
        latency_mode="balanced"
    )
    

### 

​

Key parameters

Parameter| Description  
---|---  
`api_key`| Your Fish Audio API key (or use `FISH_API_KEY` env var)  
`model`| TTS model/backend to use (default: `s2.1-pro`)  
`reference_id`| Voice model ID from the [Fish Audio library](https://fish.audio/discover)  
`output_format`| Audio format: `pcm`, `mp3`, `wav`, or `opus` (default: `pcm`)  
`sample_rate`| Audio sample rate in Hz (default: `24000`)  
`num_channels`| Number of audio channels (default: `1`)  
`base_url`| Custom API endpoint (default: `https://api.fish.audio`)  
`latency_mode`| `normal` (~500ms) or `balanced` (~300ms, default)  
  
### 

​

Streaming modes

The plugin supports two synthesis modes:
    
    
    # Chunked (non-streaming) synthesis
    stream = tts.synthesize("Hello, world!")
    
    # Real-time WebSocket streaming
    stream = tts.stream()
    

## 

​

Resources

  * [LiveKit Agents Documentation](https://docs.livekit.io/agents/)
  * [LiveKit GitHub](https://github.com/livekit/agents)
  * [Fish Audio Plugin Reference](https://docs.livekit.io/reference/python/v1/livekit/plugins/fishaudio/index.html)
  * [Fish Audio Voice Library](https://fish.audio/discovery)



Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/integrations/livekit.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/integrations/livekit)

[Pipecat](https://docs.fish.audio/developer-guide/integrations/pipecat)[n8n](https://docs.fish.audio/developer-guide/integrations/n8n)
