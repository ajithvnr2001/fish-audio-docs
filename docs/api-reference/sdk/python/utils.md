---
url: https://docs.fish.audio/api-reference/sdk/python/utils/
title: Utils - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:25.933581+00:00
---

# Utils - Fish Audio

> Source: https://docs.fish.audio/api-reference/sdk/python/utils/

## On this page

  * fishaudio.utils.play
    * play
  * fishaudio.utils.save
    * save
  * fishaudio.utils.stream
    * stream



Reference

# Utils

Copy pageCopy page

Copy pageCopy page

# 

​

fishaudio.utils.play

Audio playback utility.

#### 

​

play
    
    
    def play(audio: Union[bytes, Iterable[bytes]],
             *,
             notebook: bool = False,
             use_ffmpeg: bool = True) -> None
    

Play audio using various playback methods. **Arguments** :

  * `audio` \- Audio bytes or iterable of bytes
  * `notebook` \- Use Jupyter notebook playback (IPython.display.Audio)
  * `use_ffmpeg` \- Use ffplay for playback (default, falls back to sounddevice)

**Raises** :

  * `DependencyError` \- If required playback tool is not installed

**Examples** :
    
    
    from fishaudio import FishAudio, play
    
    client = FishAudio(api_key="...")
    audio = client.tts.convert(text="Hello world")
    
    # Play directly
    play(audio)
    
    # In Jupyter notebook
    play(audio, notebook=True)
    
    # Force sounddevice fallback
    play(audio, use_ffmpeg=False)
    

# 

​

fishaudio.utils.save

Audio saving utility.

#### 

​

save
    
    
    def save(audio: Union[bytes, Iterable[bytes]], filename: str) -> None
    

Save audio to a file. **Arguments** :

  * `audio` \- Audio bytes or iterable of bytes
  * `filename` \- Path to save the audio file

**Examples** :
    
    
    from fishaudio import FishAudio, save
    
    client = FishAudio(api_key="...")
    audio = client.tts.convert(text="Hello world")
    
    # Save to file
    save(audio, "output.mp3")
    
    # Works with iterators too
    audio_stream = client.tts.convert(text="Another example")
    save(audio_stream, "another.mp3")
    

# 

​

fishaudio.utils.stream

Audio streaming utility.

#### 

​

stream
    
    
    def stream(audio_stream: Iterator[bytes]) -> bytes
    

Stream audio in real-time while playing it with mpv. This function plays the audio as it’s being generated and simultaneously captures it to return the complete audio buffer. **Arguments** :

  * `audio_stream` \- Iterator of audio byte chunks

**Returns** : Complete audio bytes after streaming finishes **Raises** :

  * `DependencyError` \- If mpv is not installed

**Examples** :
    
    
    from fishaudio import FishAudio, stream
    
    client = FishAudio(api_key="...")
    audio_stream = client.tts.convert(text="Hello world")
    
    # Stream and play in real-time, get complete audio
    complete_audio = stream(audio_stream)
    
    # Save the captured audio
    with open("output.mp3", "wb") as f:
        f.write(complete_audio)
    

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/sdk/python/utils.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/sdk/python/utils)

[Core](https://docs.fish.audio/api-reference/sdk/python/core)[Exceptions](https://docs.fish.audio/api-reference/sdk/python/exceptions)
