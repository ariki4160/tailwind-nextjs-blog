---
comments: true
date: '2016-06-01T22:02:50+09:00'
summary: '早稲田大学で開発、公開されたディープラーニングで白黒写真をカラーにするプログラムを試してみました。'
draft: false
slug: 'deep-learning-monochrome-color'
tags: ['deep learning']
title: 人工知能で白黒写真をカラーにするプログラムを試してみました
---

[人工知能で白黒写真をカラーに　早大が技術開発、GitHub でコード公開](http://www.itmedia.co.jp/news/articles/1605/31/news119.html)という記事を読みました。ソースが公開されていたので、試してみました。

ソース

- [siggraph2016_colorization](https://github.com/satoshiiizuka/siggraph2016_colorization)
- [ディープネットワークを用いた大域特徴と局所特徴の学習による
  白黒写真の自動色付け](http://iizuka.cs.tsukuba.ac.jp/projects/colorization/ja/)
- [Getting started with Torch](http://torch.ch/docs/getting-started.html)

MacOS X El Capitan‎ の Macbook Air で検証します。ソースを見ると、[Lua](https://www.lua.org/)を使っているようです。

まず、Torch のインストール

```bash
$ git clone https://github.com/torch/distro.git ~/torch --recursive
$ cd ~/torch; bash install-deps;
$ ./install.sh
$ source ~/.profile
$ th

  ______             __   |  Torch7
 /_  __/__  ________/ /   |  Scientific computing for Lua.
  / / / _ \/ __/ __/ _ \  |  Type ? for help
 /_/  \___/_/  \__/_//_/  |  https://github.com/torch
                          |  http://torch.ch

th>
```

siggraph2016_colorization を git clone して、必要なモデルをダウンロードします。

```bash
$ ./download_model.sh
```

下記のコマンドで白黒写真にカラーの色を付けます。

```bash
$ th colorize.lua ansel_colorado_1941.png out.png
```

いくつかの写真を変換してみました。

サンプルとして付いている山の写真。

![山](/static/images/post/deep-learning-monochrome-color/mountain.png '山')

![山カラー](/static/images/post/deep-learning-monochrome-color/mountain_after.png '山カラー')

外国のどこかの駅の写真

![駅](/static/images/post/deep-learning-monochrome-color/station.jpg '駅')

![駅カラー](/static/images/post/deep-learning-monochrome-color/station_after.png '駅カラー')

明治時代あたりと思われる写真

![明治時代](/static/images/post/deep-learning-monochrome-color/meiji_period.jpg '明治時代')

![明治時代カラー](/static/images/post/deep-learning-monochrome-color/meiji_period_after.png '明治時代カラー')

朝日か夕暮れ前の写真

![朝日か夕暮れ前](/static/images/post/deep-learning-monochrome-color/sunrise.jpg '朝日か夕暮れ前')

![朝日か夕暮れ前カラー](/static/images/post/deep-learning-monochrome-color/sunrise_after.png '朝日か夕暮れ前カラー')

私の子どもの頃のモノクロ写真

![子どもの頃](/static/images/post/deep-learning-monochrome-color/masayuki.jpg '子どもの頃')

![子どもの頃カラー](/static/images/post/deep-learning-monochrome-color/masayuki_after.png '子どもの頃カラー')

モノクロでも保存状態の良くないものは、綺麗な色は付かない感じがします。
