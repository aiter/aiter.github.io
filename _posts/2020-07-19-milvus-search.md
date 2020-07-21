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
> [overview](https://www.milvus.io/docs/overview.md)
> 
> * vector similarity search engine, 向量相似度搜索引擎 
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
* BF 暴力 Brute Force。这个就是把所有召回，适合小数据量
* KD-Tree  适合维度比较小的场景
* HC 分层聚类 Hierarchical Clustering 
* HNSW 分层的可导航小世界 Hierarchical Navigable Small World
* PQ 乘积量化 Product Quantization 
* KNN 近邻图 Graph
* QGraph 量化图 Quantization Graph
* LSH 局部敏感哈希 Locality sensitive hashing


## 相关项目
[faiss](https://github.com/facebookresearch/faiss)
* search time
* search quality
* memory used per index vector
* training time
* need for external data for unsupervised training
[nmslib](https://github.com/nmslib/hnswlib)
[Nearest neighbor search-NNS](https://en.wikipedia.org/wiki/Nearest_neighbor_search#Approximate_nearest_neighbor)