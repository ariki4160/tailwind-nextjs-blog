---
comments: true
date: '2016-06-03T22:12:57+09:00'
summary: 'さくらインターネットの「Docker」を利用したホスティングサービスArukasでWordPressの環境を5分で構築'
draft: false
slug: 'arukas-docker-wordpress'
tags: ['Docker', 'WordPress']
title: 'ArukasでDockerを使ってWordPressの環境を5分で構築'
---

さくらインターネットで、「Docker」を利用したホスティングサービス「Arukas（アルカス）」が公開されています。現在、β 期間中につき無償利用できるので、試してみました。

Arukas は、2020/01/31 にサービスを終了しました。

![Arukas_01](/static/images/post/arukas-docker-wordpress/01.png 'Arukas_01')

GitHub のアカウントでログインします。

![Arukas_02](/static/images/post/arukas-docker-wordpress/02.png 'Arukas_02')

新しいアプリケーションを作成します。

![Arukas_03](/static/images/post/arukas-docker-wordpress/03.png 'Arukas_03')

ディスクイメージには、「tutum/wordpress」を指定します。

![Arukas_04](/static/images/post/arukas-docker-wordpress/04.png 'Arukas_04')

アプリを起動します。

![Arukas_05](/static/images/post/arukas-docker-wordpress/05.png 'Arukas_05')

「アプリはデプロイ中です」の表示になります。

![Arukas_06](/static/images/post/arukas-docker-wordpress/06.png 'Arukas_06')

すぐに、Port の URL が有効になります。

![Arukas_07](/static/images/post/arukas-docker-wordpress/07.png 'Arukas_07')

すでに、WordPress のウィザードが起動しています。必要な項目を設定します。

![Arukas_08](/static/images/post/arukas-docker-wordpress/08.png 'Arukas_08')
![Arukas_09](/static/images/post/arukas-docker-wordpress/09.png 'Arukas_09')
![Arukas_10](/static/images/post/arukas-docker-wordpress/10.png 'Arukas_10')
![Arukas_11](/static/images/post/arukas-docker-wordpress/11.png 'Arukas_11')

WordPress にログインして、動作を確認します。

![Arukas_12](/static/images/post/arukas-docker-wordpress/12.png 'Arukas_12')
![Arukas_13](/static/images/post/arukas-docker-wordpress/13.png 'Arukas_13')
![Arukas_14](/static/images/post/arukas-docker-wordpress/14.png 'Arukas_14')

Arukas でのアプリケーション作成から、WordPress にログインするまで、約 5 分ほどで完了しました。
