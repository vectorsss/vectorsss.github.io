---
title: "{{ replace .TranslationBaseName "-" " " | title }}"
subtitle:    ""
description: ""
date: {{ .Date }}
lastmod: {{ .Date }}
tags: ["tag1", "tag2"]
categories: ["cat1", "cat2"]
author: "Chi Zhao(Vector)"
keywords: ["kw1", "kw2"]
slug: "{{ dateFormat "2006-01-02" .Date }}-{{.Name}}"
draft: true
hiddenFromHomePage: false
hideHeaderAndFooter: false
---


<!--more-->
