---
title: Nodeの環境構築、Windows11のWSL2、Ubuntu 22.04.1 LTS、Voltaの場合
date: '2023-02-26T18:05:19.18'
template: 'post'
draft: false
slug: 'node-development-ubuntu-volta'
category: 'Web Development'
tags:
  - 'Node.js'
  - 'WSL2'
  - 'Ubuntu'
  - 'volta'
summary: 'Windows11のWSL2、Ubuntu 22.04.1 LTSでのNodeの環境構築。JavaScript ツール マネージャには、Voltaを利用をして、Next.jsのImage Gallery Starterをセットアップする前までの記録'
socialImage: '/media/node-development-ubuntu-volta_01.png'
---

Windows11 の WSL2、Ubuntu 22.04.1 LTS での Node の環境構築の記録です。

## WSL と node のバージョン

WSL のバージョン

```bash
PS C:\Users\Owner> wsl -l -v
  NAME      STATE           VERSION
* Ubuntu    Running         2
```

node の確認

```bash
root@DESKTOP-RAS40GK:~# node -v
Command 'node' not found, but can be installed with:
apt install nodejs
```

node はまだ入っていません。

## Volta をインストール

JavaScript ツール マネージャには、[Volta](https://volta.sh/) を利用します。インストールをしようとしますが、curl が使えませんでした。

```
root@DESKTOP-RAS40GK:~# curl https://get.volta.sh | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:09 --:--:--     0curl: (6) Could not resolve host: get.volta.sh
```

[【WSL2】「Could not resolve host: hogehoge」を解決する - アルゴリズム弱太郎](https://01futabato10.hateblo.jp/entry/2021/05/11/224937) の手順に従います。

- root でしか起動できないので、Ubuntu 22.04.1 LTS 　を一度削除
- PowerShell 5 系を PowerShell 7.3.2 にバージョンアップ

再度 Ubuntu 22.04.1 LTS をインストール

```
PS C:\Users\Owner> wsl.exe --install Ubuntu-22.04
```

Volta のインストール完了

```
ariki@DESKTOP-RAS40GK:~$ curl https://get.volta.sh | bash https://get.volta.sh | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 10930  100 10930    0     0  10501      0  0:00:01  0:00:01 --:--:-- 10509
  Installing latest version of Volta (1.1.1)
    Checking for existing Volta installation
    Fetching archive for Linux, version 1.1.1
######################################################################## 100.0%
    Creating directory layout
  Extracting Volta binaries and launchers
    Finished installation. Updating user profile settings.
Updating your Volta directory. This may take a few moments...
success: Setup complete. Open a new terminal to start using Volta!
```

## Node をインストール

volta install node で、その時点の最新版がインストールされます。

```
ariki@DESKTOP-RAS40GK:~$ volta install node
success: installed and set node@18.14.1 (with npm@9.3.1) as default
```

node の起動確認

```
ariki@DESKTOP-RAS40GK:~$ node
Welcome to Node.js v18.14.1.
Type ".help" for more information.
```

Windows のディレクトリの一部のように Ubuntu のディレクトリを操作可能

![Windowsのディレクトリの一部のようにUbuntuのディレクトリを操作可能](/static/images/post/node-development-ubuntu-volta_01.png)

Volta をインストールした後のホームディレクトリ

![Voltaをインストールした後のホームディレクトリ](/static/images/post/node-development-ubuntu-volta_02.png)
