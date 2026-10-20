---
url: https://docs.fish.audio/api-reference/sdk/python/exceptions/
title: Exceptions - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-20T12:52:00.268765+00:00
---

# Exceptions - Fish Audio

> Source: https://docs.fish.audio/api-reference/sdk/python/exceptions/

## On this page

  * fishaudio.exceptions
  * FishAudioError Objects
  * APIError Objects
  * AuthenticationError Objects
  * PermissionError Objects
  * NotFoundError Objects
  * RateLimitError Objects
  * ServerError Objects
  * WebSocketError Objects
  * ValidationError Objects
  * DependencyError Objects



Reference

# Exceptions

Copy pageCopy page

Copy pageCopy page

# 

​

fishaudio.exceptions

Custom exceptions for the Fish Audio SDK.

## 

​

FishAudioError Objects
    
    
    class FishAudioError(Exception)
    

Base exception for all Fish Audio SDK errors.

## 

​

APIError Objects
    
    
    class APIError(FishAudioError)
    

Raised when the API returns an error response.

## 

​

AuthenticationError Objects
    
    
    class AuthenticationError(APIError)
    

Raised when authentication fails (401).

## 

​

PermissionError Objects
    
    
    class PermissionError(APIError)
    

Raised when permission is denied (403).

## 

​

NotFoundError Objects
    
    
    class NotFoundError(APIError)
    

Raised when a resource is not found (404).

## 

​

RateLimitError Objects
    
    
    class RateLimitError(APIError)
    

Raised when rate limit is exceeded (429).

## 

​

ServerError Objects
    
    
    class ServerError(APIError)
    

Raised when the server encounters an error (5xx).

## 

​

WebSocketError Objects
    
    
    class WebSocketError(FishAudioError)
    

Raised when WebSocket connection or streaming fails.

## 

​

ValidationError Objects
    
    
    class ValidationError(FishAudioError)
    

Raised when request validation fails.

## 

​

DependencyError Objects
    
    
    class DependencyError(FishAudioError)
    

Raised when a required dependency is missing.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/api-reference/sdk/python/exceptions.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/api-reference/sdk/python/exceptions)

[Utils](https://docs.fish.audio/api-reference/sdk/python/utils)[Legacy](https://docs.fish.audio/archive/python-sdk-legacy)
