---
layout: post
keywords: rtmp 
description: live stream
title: "rtmp,hls"
categories: [live]
tags: [live,rtmp,hls]
---
{% include codepiano/setup %}

## RTMP(Real-Time Messaging Protocol)

* works on top of TCP and uses port number 1935 by default
* RTMPS, which is RTMP over a TSL/SSL connection

RTMP,HLS, and WebRTC

What is a Streaming Protocol?
[Video Streaming Protocol](https://www.dacast.com/blog/video-streaming-protocol/)

Video->chunks->transport->reassemble

[Steaming Protocols](https://www.dacast.com/blog/streaming-protocols/)

What is RTMP?
[RTMP](https://www.dacast.com/blog/rtmp-real-time-messaging-protocol/)
>
> * streaming protocol
> * low latency streaming
> * RTMP has taken a new role in live streaming. Ingesting media from the encoder or other source to a video streaming platform.
> * the most accessible and affordable option since it works with most modern encoders, including many free encoding software.
> * ❗️不兼容很多的视频播放器(not compatible with more modern video players)
> * ✅ very effective in its ingestion role

What is HLS?
[HLS](https://www.dacast.com/blog/hls-streaming-protocol/)
>
> * developed by Apple from streaming with an HTML5 video player
> * RTMP delivery to the Adobe Flash player —> HLS delivery to the HTML5 video player 
> * HLS is very secure
> * produces high-quality steams
> * supports adaptive bitrate steaming (at the professional broadcasting level)
> * both delivery(更多场景) and ingest(和编码器encoders的兼容还不太好)
> * ❗️latency of 15-30 seconds (时延比较高)

What is WebRTC?
[WebRTC](https://www.dacast.com/blog/webrtc-web-real-time-communication/)
>
> * rather than a protocol
> * was created to support web conferencing and VoIP
> * make peer-to-peer streaming with real-time latency possible
> * adaptive bitrate streaming

WebRTC Tutorial

* Audience
* Prerequisites
* Basic Scheme

> * Media Capture
> * codec: H.264, iSAC, Opus and VP8
> * Transportation Layer
> * Session Management

* Browser Compatibility

> * Trying out WebRTC: [apprtc](https://apprtc.appspot.com/)

Comaring RTMP vs. HLS vs. WebRTC
>
> * HLS delivery with RTMP ingest. Low latency, ultra-compatibility, affordability
> * HLS delivery + RTMP ingest
> * HLS delivery + HLS ingest(编码器支持的少)
> * WebRTC: more and more popular. 主要的限制：编码器支持的少
> * professional broadcasting level比较低(不能选择bitrate?)

## WebSocket

* over HTTP
* ws/wss

## container format

### Design Philosophy

> there should be minimal framing
> It is expected that metadata would be layered on top of WebSocket by the application layer, in the same way that metadata is layered on top of TCP by the application layer (e.g., HTTP).
>
> * adds a web origin-based security model for browsers
> * adds an addressing and protocol naming mechanism to support multiple services on one port and multiple host names on one IP address
> * layers a framing mechanism on top of TCP to get back to the IP packet mechanism that TCP is built on, but without length limits
> * includes an additional closing handshake in-band that is designed to work in the presence of proxies and other intermediaries

### Security Model

### Relationship to TCP and HTTP

### Security considerations

### Proxy traversal

### Establishing a Connection

### Subprotocols Using the WebSocket Protocol

### references

* [RTMP](https://en.wikipedia.org/wiki/Real-Time_Messaging_Protocol)
* [HTTP Live Streaming](https://en.wikipedia.org/wiki/HTTP_Live_Streaming)
* [WebRTC](https://en.wikipedia.org/wiki/WebRTC)
* [WebRTC Tutorial](https://www.tutorialspoint.com/webrtc/index.htm)
* [WebSocket](https://en.wikipedia.org/wiki/WebSocket)
* [The WebSocket Protocol](https://datatracker.ietf.org/doc/html/rfc6455)
* [aws-live-streaming](https://aws.amazon.com/cn/blogs/media/awse-choosing-aws-live-streaming-solution-for-use-case/)
* [DASH](https://en.wikipedia.org/wiki/Dynamic_Adaptive_Streaming_over_HTTP)
