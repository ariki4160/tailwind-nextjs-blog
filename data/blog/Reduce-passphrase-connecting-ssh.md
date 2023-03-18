---
title: sshの接続時にパスフレーズの入力を減らす方法
date: 2018-12-01T03:45:23+09:00
draft: false
tags:
  - 'ssh'
summary: 'Macの場合は「ssh-add -K」、Ubuntuの場合は、keychainを使ってssh接続時にパスフレーズの入力を減らす方法'
slug: 'ssh-passphrase'
comments: true
---

公開鍵と秘密鍵を使った ssh でのサーバ接続時に、秘密鍵に設定したパスフレーズを毎回入力するのは面倒なので、作業時のパスフレーズ入力回数を減らす方法を調べました。

## Mac10.13.6 High Sierra の場合

ssh-add コマンドに-K オプションをつけることにより、Mac を終了するまで、パスフレーズが記憶できます。

```
$ ssh-add -K ~/.ssh/id_rsa
```

あとは、~/.ssh/config に「my-server」という接続情報を設定している場合、下記のコマンドで接続できます。

```
$ ssh my-server
```

## Ubuntu18 の場合

ssh-add コマンドに-K オプションは、Mac でしか有効でないので、keychain というツールを使います。

keychain のインストール

```
$ sudo apt install keychain
```

keychain の起動

```
$ keychain ~/.ssh/id_rsa
$ source ~/.keychain/srv1-sh
```

サーバへの接続

```
$ ssh my-server
```
