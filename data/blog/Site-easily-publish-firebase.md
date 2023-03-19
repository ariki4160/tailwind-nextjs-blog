---
title: Firebaseで簡単に無料でサイトを公開する
date: 2018-11-24T09:08:27+09:00
draft: false
tags: ['Google', 'Firebase']
summary: 'Firebase CLIで簡単に無料でサイトを公開する'
slug: 'firebase-site-publish'
comments: true
---

下記のサイトを参考にさせていただき、Firebase でサイトの公開を試してみました。

- [Firebase で Web サイトを無料でサクッと公開してみる](https://qiita.com/Ijoru/items/5b27f1c32df2222514fb)

- [Firebase で初めてのデプロイ](https://qiita.com/Watakatsu/items/667f45081a6dfbc11074)

## 必要な環境

- Ubunt18 で検証
- Google アカウント
- Firebase のプロジェクトを用意

## Firebase CLI の確認

以前、Firebase CLI はインストールしていました。しかし、バージョンが古いと言われたので、アップデートします。

```bash
$ firebase login
Already logged in as hogehoge@gmail.com

Update available 3.18.0 → 6.1.1
Run npm i -g firebase-tools to update

$ npm i -g firebase-tools
```

ローカルマシンの任意のディレクトリで、プロジェクトを初期化します。Firebase project は、どこに作るかをたずねられますので、事前に作成しておいた Firebase project を選択します。

```bash
$ firebase init

       ######## #### ########  ######## ########     ###     ######  ########
       ##        ##  ##     ## ##       ##     ##  ##   ##  ##       ##
       ######    ##  ########  ######   ########  #########  ######  ######
       ##        ##  ##    ##  ##       ##     ## ##     ##       ## ##
       ##       #### ##     ## ######## ########  ##     ##  ######  ########

You're about to initialize a Firebase project in this directory:

    /home/ariki/program/firebase/vivoApp

? Which Firebase CLI features do you want to setup for this folder? Press Space to s
elect features, then Enter to confirm your choices. Hosting: Configure and deploy Fi
rebase Hosting sites

=== Project Setup

First, let's associate this project directory with a Firebase project.
You can create multiple project aliases by running firebase use --add,
but for now we'll just set up a default project.

? Select a default Firebase project for this directory: vivo-firebase (vivo-firebase
)
i  Using project vivo-firebase (vivo-firebase)

=== Hosting Setup

Your public directory is the folder (relative to your project directory) that
will contain Hosting assets to be uploaded with firebase deploy. If you
have a build process for your assets, use your build's output directory.

? What do you want to use as your public directory? public
? Configure as a single-page app (rewrite all urls to /index.html)? No
✔  Wrote public/404.html
✔  Wrote public/index.html

i  Writing configuration info to firebase.json...
i  Writing project information to .firebaserc...
i  Writing gitignore file to .gitignore...

✔  Firebase initialization complete!
```

ローカルにできたプロジェクトフォルダ内の　 public/index.html 　を少し編集して、deploy します。

```bash
$ firebase deploy

=== Deploying to 'vivo-firebase'...

i  deploying hosting
i  hosting[vivo-firebase]: beginning deploy...
i  hosting[vivo-firebase]: found 2 files in public
✔  hosting[vivo-firebase]: file upload complete
i  hosting[vivo-firebase]: finalizing version...
✔  hosting[vivo-firebase]: version finalized
i  hosting[vivo-firebase]: releasing new version...

✔  hosting[vivo-firebase]: release complete

✔  Deploy complete!

Project Console: https://console.firebase.google.com/project/vivo-firebase/overview
Hosting URL: https://vivo-firebase.firebaseapp.com
```

## サイトが公開されました。

https://vivo-firebase.firebaseapp.com
