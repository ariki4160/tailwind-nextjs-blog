---
title: node.jsのバージョン切り替えツール Windows,Mac,Ubuntuの場合
date: 2018-11-29T08:08:31+09:00
draft: false
tags: ['node.js']
summary: 'Windows,Mac,Ubuntuでのnode.jsのバージョン切り替えツールの使い方'
slug: 'nodejs-change'
comments: true
---

node.js のバージョン切り替えツールを Windows,Mac,Ubuntu で調査しました。

## Windows 10 の場合

### nodist を使用

node.js がインストールされている場合は、事前に削除

nodist 0.8.8 をインストール

https://github.com/marcelklehr/nodist/releases

nodist のバージョン確認

```bash
PS J:\workspace\node> nodist -v
0.8.8
```

インストール可能な　 node.js のバージョン表示

```bash
PS J:\workspace\node> nodist dist
沢山バージョンが表示される
```

node.js 9.6.1 　をインストール

```bash
PS J:\workspace\node> nodist + 9.6.1
9.6.1 [===============] 21872/21872 KiB 100% 0.0s
9.6.1
```

利用する　 node.js 　を　 9.6.1 　に設定

```bash
PS J:\workspace\node> nodist 9.6.1
9.6.1
```

インストールした　 node.js 　を　確認

```bash
PS J:\workspace\node> nodist ls
  (x64)
   6.9.1
> 9.6.1  (global: 9.6.1)
```

## macOS 10.13.4 High Sierra の場合

### nodebrew を使用

node.js がインストールされている場合は、事前に削除

```bash
先にnpmをアンインストール

$ cd /usr/local/lib
$ sudo npm uninstall npm
$ rm -rf /usr/local/bin/npm

node.jsをhomebrewからアンインストール

$ sudo brew uninstall node.js
```

nodebrew のインストール

```bash
$ curl -L git.io/nodebrew | perl - setup

$ export PATH=$HOME/.nodebrew/current/bin:$PATH
$ source ~/.bash_profile
```

インストールされている node.js を確認

```bash
$ nodebrew ls
v9.7.1

current: none
```

v9.7.1 を利用する設定

```bash
$ nodebrew use v9.7.1
use v9.7.1
```

node.js のバージョン確認

```bash
$ node -v
v9.7.1
```

インストール可能な　 node.js のバージョン表示

```bash
$ nodebrew ls-remote
沢山バージョンが表示される
```

v8.5.0 をインストール

```bash
$ nodebrew install-binary v8.5.0
Fetching: https://nodejs.org/dist/v8.5.0/node-v8.5.0-darwin-x64.tar.gz
Installed successfully
```

v8.5.0 を利用する設定

```bash
$ nodebrew use v8.5.0
use v8.5.0
```

利用できる node.js のバージョンを確認

```bash
$ nodebrew ls
v8.5.0
v9.7.1

current: v8.5.0
```

## Ubuntu16 の場合

### nvm を使用

nvm のインストール

```bash
$ git clone https://github.com/creationix/nvm.git ~/.nvm
$ source ~/.nvm/nvm.sh

$ nvm --version
0.33.8
```

nvm コマンドで Node.js をインストール

```bash
$ nvm ls-remote
$ nvm install 9.11.1
$ node -v
v9.11.1
```

nvm の設定

```bash
$ nvm alias default v9.11.1
default -> v9.11.1
```

~/.bashrc に、ターミナル起動時に nvm コマンドが適用されるように設定

```bash
$ vi ~/.bashrc

if [[ -s ~/.nvm/nvm.sh ]];
 then source ~/.nvm/nvm.sh
fi
```
