---
layout: post
keywords: interface, virtual networking
description: Linux interfaces for virtual networking
title: "Linux interfaces for virtual networking"
categories: [networking]
tags: [interface,networking]
---
{% include codepiano/setup %}

## tun/tap

### OpenVPN

### flannel UDP

## veth-pair

## veth-pair + bridge

### vxlan

## Network Policies k8s

## docker network

* bridge
* macvlan
* ipvlan

## QEMU virtio-networking

Bridging with Netfilter

* [tun/tap & veth-pair](https://www.sobyte.net/post/2022-07/cloud-native-virtual-networking/)
* [flannel](https://github.com/flannel-io/flannel#deploying-flannel-manually)
* [network-policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/)
* [introduction-virtio-networking-and-vhost-net](https://www.redhat.com/en/blog/introduction-virtio-networking-and-vhost-net)
* [deep-dive-virtio-networking-and-vhost-net](https://www.redhat.com/en/blog/deep-dive-virtio-networking-and-vhost-net)
* [Virtio网络的演化之路](https://cloud.tencent.com/developer/beta/article/1540284)
* [](https://developers.redhat.com/articles/2022/04/06/introduction-linux-bridging-commands-and-features#)
* [子网划分、子网掩码、CIDR 、路由聚合相关计算详解](https://blog.csdn.net/qq_38289815/article/details/107114875)
