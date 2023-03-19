---
title: 0.01を10000回足しても100にならない
date: 2018-11-18T03:24:10+09:00
draft: false
tags: ['python']
summary: '実数と浮動小数点数は違うと言うことが、「数値計算の常識」に書かれているという話'
slug: 'Real-and-loating-point-numbers-are-different'
comments: true
---

「0.01 を 10000 回足しても 100 にならない」というツイートを見ました。

有名な話のようで、「数値計算の常識」という本に書かれているようです。今度読んでみたいと思います。Python で検証してみました。

まず、10 個の「0.01」を足してみます。

```python
Python 3.6.4 |Anaconda custom (64-bit)| (default, Jan 16 2018, 10:22:32) [MSC v.1900 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> lst=[0.01]*10
>>> lst
[0.01, 0.01, 0.01, 0.01, 0.01, 0.01, 0.01, 0.01, 0.01, 0.01]
>>> sum(lst)
0.09999999999999999
```

この段階で、既に誤差が出ているようです。次に、10000 個を足してみました。

```python
>>> lst: [0.01] * 10000
>>> sum(lst)
100.00000000001425
```

確かに、100 にはなりませんでした。こういうものなのでしょう。
