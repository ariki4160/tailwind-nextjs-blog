---
comments: true
date: '2016-05-18T22:11:37+09:00'
summary: '大量の重複しないIDをpythonでuuidモジュールを使って作成します'
draft: false
slug: 'a-large-amount-id-generate'
tags: ['python']
title: '大量の重複しないIDを生成する方法'
---

## uuid モジュールを使用

大量の重複しない ID を生成する必要があり、python で uuid モジュールを使って作成しました。

random_id_generate.py

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import sys
import uuid

argv = sys.argv

with open('list.txt', mode = 'a') as fh:
	for x in range(int(argv[1])):
		fh.write(str(uuid.uuid4())+"\n")
```

使い方

生成したい件数を引数で渡すと、同階層にある list.txt に ID を記録します

```bash
S ./random_id_generate.py 100
```

生成された ID

```
ea46ed1c-9eb4-4e76-99ff-95a040daefac
ec1a6c64-e1a9-4ebe-9a72-8b1cab8059f9
b7281fe7-8606-4a06-8236-51dfa73f8366
4b9edb80-e0f0-4d54-8eb7-53f7cec8e758
5c416197-736c-4a5e-b018-ff0f28025964
```

動作制作環境動作

- Mac OSX El Capitan
- メモリ 8GB
- Python 2.7.11

上記の環境にて、150 万の ID を約 30 秒で生成

## shortuuid モジュールを使用

uuid モジュールを使うと、生成される ID が長いので、短い ID を制作するために、shortuuid モジュールを使ってみました。

random_id_generate_short.py

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import sys
import shortuuid

argv = sys.argv

with open('list_short.txt', mode = 'a') as fh:
    for x in range(int(argv[1])):
        fh.write(str(shortuuid.uuid())+"\n")
```

生成された ID

```
aa7dUkQxezFAKbL3LDjRFi
bStaGc9JBe8pnSFf4Suhxe
jB6reqypzBun9edb6dJuQf
9rg5nVp5JXrKE5wVSD3mjb
Tu7dUuYx4gpZmHvGcBa44T
```

## 数字だけの重複しない ID を生成するバージョンも作ってみました。

random_id_generate_int_only.py

```python
#!/usr/bin/env python
#-*- coding:utf8 -*-
import random

with open('list_int.txt', mode = 'a') as fh:
    for x in random.sample(xrange(10**13,10**14-1),15*100000):
        fh.write(str(x)+"\n")
```

生成された ID

```
61767622238267
66897014686910
46554447403332
45406664575959
87298412556304
```
