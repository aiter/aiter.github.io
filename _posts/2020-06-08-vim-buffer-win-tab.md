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
|:bn| |gt|Go to next|
|:bp| |gT|Go to Previous|
|:ls| |:tabs|list|
| | Ctrl+w+h/j/k/l ||switch windows|
| | Ctrl+w+w ||switch windows|
|:bd | ||delete the current buffer, error if there are unwritten changes|
|:bd! | ||deletes the current buffer, no error if there are unwritten changes|
|:q|:q| | quit|