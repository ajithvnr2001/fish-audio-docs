---
url: https://docs.fish.audio/api-reference/sdk/python/client/
title: Client - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-18T12:09:26.757068+00:00
---

# Client - Fish Audio

> Source: https://docs.fish.audio/api-reference/sdk/python/client/

## On this page

  * fishaudio.client
  * FishAudio Objects
    * __init__
    * tts
    * asr
    * voices
    * account
    * close
  * AsyncFishAudio Objects
    * __init__
    * tts
    * asr
    * voices
    * account
    * close



Reference

# Client

Copy pageCopy page

Copy pageCopy page

# 

​

fishaudio.client

Main Fish Audio client classes.

## 

​

FishAudio Objects
    
    
    class FishAudio()
    

Synchronous Fish Audio API client. **Example** :
    
    
    from fishaudio import FishAudio
    
    client = FishAudio(api_key="your_api_key")
    
    # Generate speech
    audio = client.tts.convert(text="Hello world")
    with open("output.mp3", "wb") as f:
        for chunk in audio:
            f.write(chunk)
    
    # List voices
    voices = client.voices.list(page_size=20)
    print(f"Found {voices.total} voices")
    

#### 

​

__init__
    
    
    def __init__(*,
                 api_key: Optional[str] = None,
                 base_url: str = "https://api.fish.audio",
                 timeout: float = 240.0,
                 httpx_client: Optional[httpx.Client] = None)
    

Initialize Fish Audio client. **Arguments** :

  * `api_key` \- API key (can also use FISH_API_KEY env var)
  * `base_url` \- API base URL
  * `timeout` \- Request timeout in seconds
  * `httpx_client` \- Optional custom HTTP client



#### 

​

tts
    
    
    @property
    def tts() -> TTSClient
    

Access TTS (text-to-speech) operations.

#### 

​

asr
    
    
    @property
    def asr() -> ASRClient
    

Access ASR (speech-to-text) operations.

#### 

​

voices
    
    
    @property
    def voices() -> VoicesClient
    

Access voice management operations.

#### 

​

account
    
    
    @property
    def account() -> AccountClient
    

Access account/billing operations.

#### 

​

close
    
    
    def close() -> None
    

Close the HTTP client.

## 

​

AsyncFishAudio Objects
    
    
    class AsyncFishAudio()
    

Asynchronous Fish Audio API client. **Example** :
    
    
    from fishaudio import AsyncFishAudio
    
    async def main():
        client = AsyncFishAudio(api_key="your_api_key")
    
        # Generate speech
        audio = client.tts.convert(text="Hello world")
        async with aiofiles.open("output.mp3", "wb") as f:
            async for chunk in audio:
                await f.write(chunk)
    
        # List voices
        voices = await client.voices.list(page_size=20)
        print(f"Found {voices.total} voices")
    
    asyncio.run(main())
    

#### 

​

__init__
    
    
    def __init__(*,
                 api_key: Optional[str] = None,
                 base_url: str = "https://api.fish.audio",
                 timeout: float = 240.0,
                 httpx_client: Optional[httpx.AsyncClient] = None)
    

Initialize async Fish Audio client. **Arguments** :

  * `api_key` \- API key (can also use FISH_API_KEY env var)
  * `base_url` \- API base URL
  * `timeout` \- Request timeout in seconds
  * `httpx_client` \- Optional custom async HTTP client



#### 

​

tts
    
    
    @property
    def tts() -> AsyncTTSClient
    

Access TTS (text-to-speech) operations.

#### 

​

asr
    
    
    @property
    def asr() -> AsyncASRClient
    

Access ASR (speech-to-text) operations.

#### 

​

voices
    
    
    @property
    def voices() -> AsyncVoicesClient
    

Access voice management operations.

#### 

​

account
    
    
    @property
    def account() -> AsyncAccountClient
    

Access account/billing operations.

#### 

​

close
    
    
    async def close() -> None
    

Close the HTTP client.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/sdk/python/client.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/sdk/python/client)

[Overview](https://docs.fish.audio/api-reference/sdk/python/overview)[Resources](https://docs.fish.audio/api-reference/sdk/python/resources)
