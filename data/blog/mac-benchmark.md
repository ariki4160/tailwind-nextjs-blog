---
comments: true
date: '2016-06-26T05:55:20+09:00'
summary: 'はじめてのSwift「ファイル書き込み速度を測るベンチマークソフトを作る」を検証する'
draft: false
slug: 'mac-benchmark'
tags: ['mac']
title: Macでのファイル書き込み速度を測るベンチマークソフトを検証する
---

日経ソフトウエアの連載記事「はじめての Swift」の第 2 回、第 3 回の「ファイル書き込み速度を測るベンチマークソフト」を検証してみました。Mac に接続しているデバイス別（SSD、HDD、USB メモリ）へのファイルの読み込み、書き込み速度を検証するソフトを作成する講座記事です。

内蔵の SSD ドライブの場合です。書き込みディレクトリを指定して、書き込むファイルのサイズ、書き込み回数を選択することができます。

![SSDへの読み込み、書き込み検証](/static/images/post/mac-benchmark/file_make_01.png 'SSDへの読み込み、書き込み検証')

外付 USB-HDD の場合

![HDDへの読み込み、書き込み検証](/static/images/post/mac-benchmark/file_make_02.png 'HDDへの読み込み、書き込み検証')

SSD ドライブが、USB-HDD に比べて、どれくらい速いかが数値で確認できました。
