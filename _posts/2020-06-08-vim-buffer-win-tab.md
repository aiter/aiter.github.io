---
layout: post
keywords: vim 
description: buffer、windows、tab
title: "vim的buffer windows tab"
categories: [tools]
tags: [vim,tools,buffer,windows,tab]
---
{% include codepiano/setup %}



|Buffers|Windows|Tabs|说明|
|---|---|---|---|
||:split [filename]|:tabnew|Open a new|
|:e [filename]|vsplit [filename]|:tabedit [filename]|Edit the file with the provided name|
|:b[num]|||Open buffer number N（as shown in ls）|