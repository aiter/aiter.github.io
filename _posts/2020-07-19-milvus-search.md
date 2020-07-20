---
layout: post
keywords: search vector engine
description: vector search engine
title: "Milvus"
categories: [search]
tags: [search,vector]
---
{% include codepiano/setup %}

## What is Milvus
> * vector similarity search engine 
> * vector index libraries
>   * Faiss
>   * NMSLIB
>   * Annoy

## 工程能力
* 分片 / cluster sharding
* 读写分离 / read/write separation
* 水平扩展 / horizontal scalability
* 动态扩展 / dynamic scalability
* on docker/k8s

## 场景
* 图片、视频、音频
* 文字搜索、推荐系统、交互式问答系统和其他文字搜索的领域

## NN-Nearest Neighbor
* K-NN
* R-NN (Radius Nearest Neighbor)
* ANN (Approximate Nearest Neighbor)

## 向量检索方法
> 如何找到相关的doc(召回，把所有的doc都召回，也是一种方法）
* BF Brute Force。这个就是把所有召回，适合小数据量
* KD-Tree  适合维度比较小的场景
* HC Hierarchical Clustering 分层、聚类
* HNSW Hierarchical Navigable Small World
* PQ Product Quantization
* KNN Graph
* QGraph Quantization Graph
* LSH


## 相关项目
[faiss](https://github.com/facebookresearch/faiss)
[nmslib](https://github.com/nmslib/hnswlib)
[Nearest neighbor search-NNS](https://en.wikipedia.org/wiki/Nearest_neighbor_search#Approximate_nearest_neighbor)