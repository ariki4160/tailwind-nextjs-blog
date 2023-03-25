---
comments: true
date: '2016-05-15T18:03:25+09:00'
summary: 'TensorFlowでのMNISTの学習結果を動作確認できるプログラムを検証'
draft: false
slug: 'tensorflow-mnist-figure'
tags: ['tensorflow', 'mnist', 'deep learning']
title: '手書きの数字を判断するプログラム'
---

[![MNIST](/static/images/post/tensorflow-mnist-figure/MNIST.png 'MNIST')](https://vivo-tensorflow-mnist.herokuapp.com/)

[TensorFlow](https://www.tensorflow.org/)のインストールやチュートリアルの解説をしたページを沢山読みましたが、チュートルアルの MNIST を実際にどのように使うかを説明したページは、見たことがありませんでした。

TensorFlow の MNIST チュートルアルの内容については、[特にプログラマーでもデータサイエンティストでもないけど、Tensorflow を 1 ヶ月触ったので超分かりやすく解説](http://qiita.com/tawago/items/c977c79b76c5979874e8)がとてもわかりやすく、内部でどのような処理をしているのかが初めて分かりました。

しかし、元々、数学に関する素養が乏しいため「行列演算」と言われても良く分かりませんでした。「行列演算」の内容については、[量子力学入門：Ｑ＆Ａ](http://ryoushi-rikigaku.com/QA_why_mult.html)を読んでなんとなく分かりました。

機械学習で何をしているかというと、「求めたい"値"があってそれに限りなく近い数値を機械に計算させまくり学んでもらう。」という説明がありました。TED の[コンピュータが写真を理解するようになるまで](https://www.ted.com/talks/fei_fei_li_how_we_re_teaching_computers_to_understand_pictures?language=ja)でも同じようなことが言われていました。

    子供は教えられなくても 成長の初期にものの見方を身に付けるということです。子供は現実の世界における経験と例を通して学ぶのです。子供の目が生きたカメラで 200ミリ秒ごとに１枚写真を撮っていると考えてみましょう。これは目が動く平均時間です。すると子供は３歳になるまでに何億枚という現実世界の写真を見ていることになります。膨大な量の訓練例です。それで気が付いたのはアルゴリズムの改良ばかりに集中するのではなく、子供が経験を通じて受け取るような量と質の訓練データをアルゴリズムに与えてはどうかということでした。

MNIST の例で言うと、何万という数字の画像と、その数字が何かという情報（例えば 3 である）をコンピュータに見せて、覚えさせるということです。何万という画像から、数字ごとの特徴を覚えていくことで、数字が何であるかを判断できるようになります。

TensorFlow をインストールして、MNIST のチュートリアルを実行して、ロジスティック回帰を用いた単層と、多層畳み込みニューラルネットワークのものの識別率が違うことを確認しても、実際にその分別器をどのように使えば良いのかが分かりませんでした。

調べてみると、そのようなページを既に作られている方がいました。[TensorFlow での MNIST 学習結果を、実際に手書きして試す](http://d.hatena.ne.jp/sugyan/20151124/1448292129)。ソースは GitHub で公開されていたので、Mac で動作確認してみました。

修正したところ

    Macなのでrequirements.txtのtensorflowの対象ファイルを下記のものに変更しました。
    https://storage.googleapis.com/tensorflow/mac/tensorflow-0.7.0-py2-none-any.whl

正常動作を確認しました。heroku へのアップロードの手順も書かれていたので、heroku へアップしてみました。
2016 年当時は動作してましたが、2023/03/26 現在は動作していません。

[MNIST の分析結果を使って手書きの数字を判別するページ](https://vivo-tensorflow-mnist.herokuapp.com/)
