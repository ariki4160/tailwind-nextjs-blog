---
title: Laravel 5.7をUbuntu 18にインストールする
date: 2018-11-24T03:46:41+09:00
draft: false
tags: ['Laravel', 'PHP7']
summary: 'Laravel Framework 5.7.14をUbuntu 18.04.1にインストールして起動するまでの備忘録'
slug: 'laravel-ubunts'
comments: true
---

## インストールするマシンの環境、インストールの手順

- Ubuntu 18.04.1
- [公式サイトのインストール手順](https://laravel.com/docs/5.7)

## Ubuntu 18.04.1 で PHP 7.2 の環境を用意

Ubuntu のパッケージを最新に

```bash
$ sudo apt update
$ sudo apt upgrade
```

php7.2 と必要なパッケージもインストール

```bash
$ sudo apt install php7.2 php7.2-mbstring php7.2-xml php7.2-zip
```

php のバージョン確認

```bash
$ php -v
PHP 7.2.10-0ubuntu0.18.04.1 (cli) (built: Sep 13 2018 13:45:02) ( NTS )
```

## Composer の導入

Composer は、PHP のパッケージ管理システムです。インストールスクリプトを実行して、PATH の通っている場所に移動させます。

```bash
$ curl https://getcomposer.org/installer | php
$ sudo mv -i composer.phar /usr/local/bin/composer
```

Composer のバージョンを確認

```bash
$ composer -V
Composer version 1.7.3 2018-11-01 10:05:06
```

## Laravel のインストール

あとは、Composer を利用して、 Laravel のインストラーを取得して実行します。

```bash
$ composer global require "laravel/installer"
```

Laravel の PATH を通しておきます。.bashrc に下記を追加します。

```bash
export PATH="$HOME/.config/composer/vendor/bin:$PATH"
```

Mac の場合は、PATH が違います。

```bash
$HOME/.composer/vendor/bin
```

Laravel のバージョン確認

```bash
$ php artisan -V
Laravel Framework 5.7.14
```

## Laravel のプロジェクトを作成して、起動

Laravel コマンドで blog プロジェクトを作成、出来上がった blog フォルダに移動して、サイトを起動します。

```bash
$ laravel new blog
$ cd blog
$  php artisan serve
Laravel development server started: <http://127.0.0.1:8000>
[Sat Nov 24 04:26:12 2018] 127.0.0.1:46430 [200]: /robots.txt
[Sat Nov 24 04:26:13 2018] 127.0.0.1:46434 [200]: /favicon.ico
```

![Laravel started](/static/images/post/laravel-ubunts.png 'Laravel started')
