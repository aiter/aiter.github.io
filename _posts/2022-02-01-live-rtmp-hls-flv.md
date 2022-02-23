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

## WebSocket

* over HTTP
* ws/wss

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

[RTMP](https://en.wikipedia.org/wiki/Real-Time_Messaging_Protocol)
[HTTP Live Streaming](https://en.wikipedia.org/wiki/HTTP_Live_Streaming)
[WebRTC](https://en.wikipedia.org/wiki/WebRTC)
[WebSocket](https://en.wikipedia.org/wiki/WebSocket)
[The WebSocket Protocol](https://datatracker.ietf.org/doc/html/rfc6455)
