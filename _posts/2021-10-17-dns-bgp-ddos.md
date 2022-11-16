---
layout: post
keywords: dns
description: dns bgp
title: "dns bgp"
categories: [network]
tags: [network,dns,bgp,ddos]
---
{% include codepiano/setup %}

## DNS

### DNS recursor  DNS解析器

### Root nameserver

### TLD nameserver

### 什么是ASN

### 什么是任播(Anycast)DNS?

> UniCast 单播
> MultiCast 多播
> BroadCast 广播
> 实际是 BGP Anycast 任意播或泛播
> AnyCast IP拥有MultiCast和UniCast各自的部分特性：
> 主要靠BGP的路由协议，有多个相同的ip的server，路由协议找到“最近”的一台server

任播指一个IP可以应用到多个服务器上

## Ip show / manipulate routing, devices, policy routing and tunnels

## What is a DNS zone?

> A DNS zone is a portion of the DNS namespace that is managed by a specific organization or administrator.
> 一个DNS zone是DNS名字空间的一部分，它被特定组织和管理机构管理。

## DNS root server

## TLD server

### Akamai

* Keywords  Akamai, CDN, overlay networks, application acceleration, HTTP, DNS, content delivery, quality of service, streaming media
* 2. INTERNET APPLICATION REQUIREMENTS
* 3. INTERNETDELIVERYCHALLENGES
* 4. DELIVERY NETWORK OVERVIEW
* 4.1 Delivery Networks as Virtual Networks
* 4.2 Anatomy of a Delivery Network
* 4.3 System Design Principles
* 5. HIGH-PERFORMANCE STREAMING AND CONTENT DELIVERY NETWORKS
* 5.1 Video-grade Scalability
* 5.2 StreamingPerformance
* 5.3 A Transport System for Contentand Streaming Media Delivery
* 6. HIGH-PERFORMANCE APPLICATION DELIVERY NETWORKS
* 6.1 A Transport System for Application Acceleration
* 6.2 Distributing Applications to the Edge
* 7. PLATFORM COMPONENTS
* 7.1 Edge Server Platform
* 7.2 Mapping System
* 7.3 Communications and Control System
* 7.4 Data Collection and Analysis System
* 7.5 Additional Systems and Services
* 8. EXAMPLE:MULTI-LEVEL FAILOVER

### Akamai DNS:Providing Authoritative Answers to the World’s Queries

* 2 CHARACTERIZING QUERY TRAFFIC
* 3 SYSTEM ARCHITECTURE
* 3.1 Authoritative Nameservers
* 3.2 Supporting Components
* 4 RESILIENCY
* 4.1 Anycast Failover Mechanism
* 4.2 Failure Resiliency
* 4.3 Attack Resiliency
* 5 DNS PERFORMANCE
* 5.1 Anycast Performance Tuning
* 5.2 Two-Tier Delegation System

### End-User Mapping: Next Generation Request Routing for Content Delivery

* 2. THE MAPPING SYSTEM
* 2.1 End-User Mapping
* 2.2 Mapping System Architecture
* 3. UNDERSTANDING CLIENTS AND THEIR NAME SERVERS
* 3.1 Collecting Client-LDNS pairs
* 3.2 How far are clients from their LDNSes
* 3.3 How far are clients that use the same LDNS from each other?

## references

* [rfc1034 DNS](https://datatracker.ietf.org/doc/html/rfc1034)
* [rfc1035 DNS](https://datatracker.ietf.org/doc/html/rfc1035)
* [what-is-the-difference-between-authoritative-and-recursive-dns-nameservers)](https://umbrella.cisco.com/blog/what-is-the-difference-between-authoritative-and-recursive-dns-nameservers)
* [dns-zone](https://www.cloudflare.com/zh-cn/learning/dns/glossary/dns-zone/)
* [dns-root-server](https://www.cloudflare.com/learning/dns/glossary/dns-root-server/)
* Akamai DNS: Providing Authoritative Answers to the World’s Queries
