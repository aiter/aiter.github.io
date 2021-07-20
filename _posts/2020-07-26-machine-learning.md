---
layout: post
keywords: Machine Learning
description: Machine Learning 
title: "机器学习基础"
categories: [ML]
tags: [ai,ml]
---
{% include codepiano/setup %}

## AI算法
> AI > 机器学习  > 深度学习

* supervised
* Unsupervised
* Reinforcement learning

### 深度学习
* 胶囊神经网络
* Attention 机制
* 深度学习 - Deep learning | DL
* 长短期记忆网络 - Long short-term memory | LSTM
* 生成对抗网络 - Generative Adversarial Networks | GAN
* 循环神经网络 - Recurrent Neural Network | RNN
* 卷积神经网络 - CNN
* 强化学习-Reinforcement learning | RL
* RNN->LSTM
* Encoder-Decoder  Seq2Seq
* Transformer   BERT|Bidirectional Encoder Representation from Transformers

### 机器学习
* 线性回归 - linear regression
* 逻辑回归 - Logistic regression
* 朴素贝叶斯 - Naive Bayes classifier | NBC
* Adaboost 算法
* 随机森林 - Random forest
* 支持向量机 - Support Vector Machine | SVM
* 决策树 - Decision tree
* K均值聚类（k-means clustering）
* 集成学习（Ensemble Learning）

## 基础科普
* 深度学习、神经网络、机器学习、人工智能的关系
    * 机器学习是AI的一个分支
    * 深度学习是机器学习的一个重要分支
    * 深度学习的概念源于人工神经网络的研究，但是并不完全等于传统神经网络。（是传统神经网络的升级，约等于神经网络）
    * 神经网络是一个网络结构，深度学习就是对这个网络结构进行调整()
```
   传统机器学习： 数据预处理  -->  特征提取  --> 选择分类器
   深度学习   ： 数据预处理  -->  设计模型  --> 训练
```

* 4种典型的深度学习算法
    * CNN 卷积神经网络,最擅长图片处理
        * CNN 的基本原理：
            卷积层 – 主要作用是保留图片的特征(提取图像中的局部特征)
            池化层 – 主要作用是把数据降维，可以有效的避免过拟合（用来大幅降低参数量级(降维)）
            全连接层 – 根据不同任务输出我们想要的结果
        * 运用场景
            图像分类、检索：图像搜索
            目标定位检测：自动驾驶、安防、医疗
            目标分割：美图、视频后期加工、图像生成
            人脸识别：安防、金融、生活
            骨骼识别：安防、电影、图像视频生成、游戏
    * RNN 循环神经网络
        * 特点
            卷积神经网络 – CNN 和普通的算法大部分都是输入和输出的一一对应，也就是一个输入得到一个输出。不同的输入之间是没有联系的。
            RNN 跟传统神经网络最大的区别在于每次都会将前一次的输出结果，带到下一次的隐藏层中，一起训练。
            RNN 有短期记忆问题，无法处理很长的输入序列
            训练 RNN 需要投入极大的成本
            由于 RNN 的短期记忆问题，后来又出现了基于 RNN 的优化算法
        * 优化 LSTM 和 GRU
            RNN 是一种死板的逻辑，越晚的输入影响越大，越早的输入影响越小，且无法改变这个逻辑。
            LSTM 做的最大的改变就是打破了这个死板的逻辑，而改用了一套灵活了逻辑——只保留重要的信息。
            GRU 主要是在 LSTM 的模型上做了一些简化和调整，在训练数据集比较大的情况下可以节省很多时间
        * 使用场景
            文本生成：填空题，给出前后文，然后预测空格中的词是什么。
            机器翻译：翻译工作也是典型的序列问题，词的顺序直接影响了翻译的结果。
            语音识别：根据输入音频判断对应的文字是什么。
            生成图像描述：类似看图说话，给一张图，能够描述出图片中的内容。这个往往是 RNN 和 CNN 的结合。
            视频标记：他将视频分解为图片，然后用图像描述来描述图片内容。
    * GANs 生成对抗网络
    * RL 深度强化学习
### 标量 scalar
> 标量只有大小概念，没有方向的概念。

点——标量（scalar）
线——向量（vector） 大小(箭头的长度)和方向(箭头的方向)
面——矩阵（matrix）
体——张量（tensor）

### 分类模型评估指标
> * T=机器判断对不对    T=对，F=不对
> * P=机器判断是不是    P=是，N=不是
> * TP=对/是       判断是对的，是=1 
> * FP=不对/是     判断是不对的，所以本身应该是0
> * FN=不对/不是   判断是不对的，所以本身应该是1 
> * TN=对/不是     判断是对的，本身应该是0

* 准确率 Accuracy = (TP + TN)/(TP+TN+FP+FN)   判断的对不对(是和不是都判断对了)
* 精准率 Precision = TP/(TP+FP)               判断对的比例(机器认为是正例，但是有不对的)
* 召回率 Recall = TP/(TP+FN)                  判断对的，占本身是的比例，还有一部分也是，但是判断错F了成N
* F1 F1= (2*Precision*Recall)/(Precision+Recall)
* ROC曲线 （Receiver Operating Characteristic）
* AUC曲线

### 线性回归
```
             无监督学习
                    |  ---> 回归 ---> 线性回归
机器学习-->   监督学习
                    |  ---> 分类 ---> 逻辑回归(二分类)
             强化学习
```

回归的目的是：预测

### 决策树
> 分类。 根节点、内部节点、叶节点

* 特征选择
* 决策树生成
* 决策树剪枝，主要目的是对抗「过拟合」

* 主要算法
    * ID3 算法 ： 利用信息增益来选择特征的
    * C4.5 算法： ID3的改进版，不是直接使用信息增益，而是引入“信息增益比”指标作为特征的选择依据。
    * CART（Classification and Regression Tree）即可以用于分类，也可以用于回归问题。CART 算法使用了基尼系数取代了信息熵模型。

### Encoder-Decoder 和 Seq2Seq

## 机器学习

### SVM 支持向量机 – Support Vector Machine | SVM
* 超平面
* 支持向量

### 逻辑回归
* 主要解决二分类问题，用来表示某件事情发生的可能性。

#### 逻辑回归 & 线性回归 对比
* 线性回归： 解决回归问题；连续的变量；符合线性关系；     直观表达变量关系
* 逻辑回归： 解决分类问题；离散的变量；可以不符合线性关系；无法直观表达变量关系

### 朴素贝叶斯 – Naive Bayes classifier | NBC


## 深度学习

### 前馈神经网络（Feedforward neural network）
* 一种最简单的神经网络，各神经元分层排列。每个神经元只与前一层的神经元相连。
* 接收前一层的输出，并输出给下一层，各层间没有反馈。

## 强化学习
> 强化学习是机器学习的一种学习方式，它跟监督学习、无监督学习是对应的.
> 强化学习并不是某一种特定的算法，而是一类算法的统称。

强化学习的主流算法
* 免模型学习（Model-Free）
* 有模型学习（Model-Based）

## 自然语言处理
* 词性标注 - Part of speech
* Word2vec
* 命名实体识别 - Named-entity recognition | NER
* 自然语言理解 - NLU | NLI

## 计算机视觉
* CNN

## 语音交互
* LSTM



## BM25
* 单词和目标文档的相关性   WD
* 单词和查询关键词的相关性  WQ
* 单词的权重部分   WT

WD*WQ*WT 

### BM25变种
* BM25F  F=field
* BM25 + PageRank

## 语言模型
> 核心思想：希望用概率模型(Probabilistic Model)来描述查询关键字和目标文档之间的关系。
> 最简单的类型：
> * 查询关键字似然检索模型(Query Likelihood Retrieval Model)。简单来说，一个语言模型就是一个针对词汇表的概率分布。

## links
[分类模型评估指标](https://easyai.tech/ai-definition/accuracy-precision-recall-f1-roc-auc/)