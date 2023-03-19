---
title: GatsbyJSのサイトをsurge.shで公開する
date: 2018-11-25T16:36:16+09:00
draft: false
tags: ['node.js', 'gatsby', 'surge.sh']
summary: 'GatsbyJSのgatsby-starter-hero-blogをsurge.shで公開する'
slug: 'gatsby-surge-publish'
comments: true
---

## GatsbyJS とは

Gatsby は React で作られている静的サイトジェネレーターです。

[GatsbyJS](https://www.gatsbyjs.org/)

![GatsbyJS site top page](/static/images/post/gatsbyjs-surge-sh/25-11-2018-07.png 'GatsbyJS site top page')

![GatsbyJS site flow](/static/images/post/gatsbyjs-surge-sh/25-11-2018-09.png 'GatsbyJS site flow')

## GatsbyJS のバージョンをアップ

以前、gatsby-cli のコマンドをインストールをしていましたが、バージョンが古いので、最新バージョンにアップデートします。

```bash
$ gatsby -v
1.1.50
$ npm i -g gatsby-cli
$ gatsby -v
2.4.5
```

## GatsbyJS のスターターをインストール

![gatsby-starter-hero-blog](/static/images/post/gatsbyjs-surge-sh/25-11-2018-05.png 'gatsby-starter-hero-blog')

[gatsby-starter-hero-blog](https://www.gatsbyjs.org/starters/gatsby-starter-hero-blog)を利用してプロジェクトを作成します。

```bash
$ gatsby new vivo-gatsby https://github.com/greglobinski/gatsby-starter-hero-blog.git
$ cd vivo-gatsby/
```

ローカルマシン上でプロジェクトを起動します。

```bash
$ gatsby develop
```

http://localhost:8000 で動作確認

gatsby-starter-hero-blog では、algolia でサイト内を検索するので、algolia に signup して、必要な API キー等を取得して、プロジェクトフォルダ内に「.env」というファイルを作成して、下記の API キー等を設定しておきます。

```bash
GOOGLE_ANALYTICS_ID=...
ALGOLIA_APP_ID=...
ALGOLIA_SEARCH_ONLY_API_KEY=...
ALGOLIA_ADMIN_API_KEY=...
ALGOLIA_INDEX_NAME=...
FB_APP_ID=...
```

![Algolia site](/static/images/post/gatsbyjs-surge-sh/25-11-2018-11.png 'Algolia site')

![Algolia manage](/static/images/post/gatsbyjs-surge-sh/25-11-2018-06.png 'Algolia manage')

gatsby build で、public フォルダ内に公開用のファイルを生成します。

```bash
$ gatsby build
success open and validate gatsby-configs — 0.007 s
success load plugins — 0.286 s
success onPreInit — 0.504 s
success delete html and css files from previous builds — 0.081 s
success initialize cache — 0.005 s
success copy gatsby files — 0.013 s
success onPreBootstrap — 0.008 s
success source and transform nodes — 0.121 s
success building schema — 0.274 s
success createPages — 0.074 s
success createPagesStatefully — 0.029 s
success onPreExtractQueries — 0.004 s
success update schema — 0.166 s
success extract queries from components — 0.139 s
success run graphql queries — 0.495 s — 28/28 56.74 queries/second
success write out page data — 0.002 s
success write out redirect data — 0.000 s
success onPostBootstrap — 0.001 s

info bootstrap finished - 3.583 s

success Building production JavaScript and CSS bundles — 9.105 s
success Building static HTML for pages — 4.078 s — 27/27 41.10 pages/second
success index to Algolia — 9.507 s
Generated public/sw.js, which will precache 9 files, totaling 309016 bytes.
info Done building in 26.432 sec
```

build が完了すると、WebPack で生成された js の構成がブラウザで表示されます。すごい！

![WebPack js image](/static/images/post/gatsbyjs-surge-sh/25-11-2018-04.png 'WebPack js image')

## 出来た公開用ファイルを Sarge.sh で公開

[Surge.sh](https://surge.sh/)

![Surge top page](/static/images/post/gatsbyjs-surge-sh/25-11-2018-02.png 'Surge top page')

Sarge.sh の特徴

- 静的ホスティングサービス
- ウェブアプリケーションをホスト可能
- コマンドだけでサイトの公開作業が完結
- 無料

コマンドラインツールのインストールします。

```bash
$ npm install --global surge
```

初回のみメールアドレスとパスワードを入力してアカウントを作成します。

```bash
$ surge
```

確認用メールが送られてくる。確認用のリンクをクリックして認証完了です。

![Surge confirmed](/static/images/post/gatsbyjs-surge-sh/25-11-2018-08.png 'Surge confirmed')

surge コマンドの引数として、「該当のフォルダ」「使用したい surge.sh より前の名前」を指定して起動　このコマンドでサイトへの公開が完了します。

```bash
$ surge public vivo-gatsby.surge.sh

   Welcome to Surge! (surge.sh)
   Login (or create surge account) by entering email & password.

          email: ariki1068@gmail.com
       password:

   Running as ariki1068@gmail.com (Student)

        project: public
         domain: vivo-gatsby.surge.sh
         upload: [] 100% eta: 0.0s (485 files, 28371923 bytes)
            CDN: [====================] 100%

             IP: 45.55.110.124

   Success! - Published to vivo-gatsby.surge.sh
```

よく使うコマンドの確認　公開しているサイト一覧の確認　サイトの削除

```bash
$ surge list
	1543124581655 vivo-gatsby.surge.sh         1 hour ago    surge   surge.sh   Standard
$ surge teardown vivo-gatsby.surge.sh
	Success - vivo-gatsby.surge.sh has been removed.
$ surge list
	Empty
```

## サイト公開

サイトが公開できました。

https://vivo-gatsby.surge.sh
