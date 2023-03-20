---
comments: true
date: '2016-06-06T21:50:50+09:00'
summary: 'Windows10へのアップグレードでエラー'
draft: false
slug: 'windows-ten-upgrade-error'
tags: ['windows']
title: Windows10へのアップグレードでコードc1900104エラーが表示される
---

Windows7 を Windows10 へアップグレードする際、エラーが表示されて、アップグレードできませんでした。

環境

- HP Compaq Elite 8300 SFF
- メモリ 16GB
- C ドライブの空き容量が、200GB 以上あることを確認

かなり時間が経ってから、エラー表示

![windows10_error](/static/images/post/windows_error.png 'windows10_error')

[【C1900104】Windows10 がインストールされません](https://answers.microsoft.com/ja-jp/windows/forum/windows_10-windows_install/c1900104windows10%E3%81%8C%E3%82%A4%E3%83%B3/0fa2ad4c-5f2a-44d8-b4be-1c7ca84522e8?auth=1)の内容に従って、いくつか設定を変更しました。

- [Windows Update トラブルシューティング ツール](http://windows.microsoft.com/ja-jp/windows7/open-the-windows-update-troubleshooter%E3%83%B3/0fa2ad4c-5f2a-44d8-b4be-1c7ca84522e8?auth=1)の実行
- 外付けの USB-HDD 　 2 台を外す
- Bluetooth 接続の無線マウスを外す

上記の環境にて、アップグレードをすると、無事に Windows10 へアップグレードが完了しました。その後、外付けの USB-HDD、Bluetooth 接続の無線マウスを接続して、問題なく利用できることを確認しました。
