---
title: FileMaker Serverをコマンドで制御する方法
date: 2018-11-19T17:24:38+09:00
draft: false
tags: ['FileMaker']
summary: 'FileMaker Serverをコマンドで起動、停止、コマンドラインインターフェース (CLI) の使用'
slug: 'FileMaker-Server-CLI'
comments: true
---

## コマンドを使って制御できること

FileMaker Server プロセスの開始

```bash
sudo launchctl start com.filemaker.fms
```

FileMaker Server プロセスの停止

```bash
sudo launchctl stop com.filemaker.fms
```

## コマンドラインインターフェース (CLI)

CLI ヘルプ

```bash
fmsadmin help
```

CLI コマンド

- fmsadmin コマンド [オプション]
- 次の例は、Admin Console のユーザ名 admin とパスワード pword を認証し、確認を求めずに開いているすべてのデータベースを閉じます。

```bash
fmsadmin close -y -u admin -p pword
```

CLI ファイル

- CLI 実行可能ファイル「fmsadmin」は次のフォルダにあります。
- Windows: [ドライブ]:¥Program Files¥FileMaker¥FileMaker Server¥Database Server¥fmsadmin.exe
- macOS: /ライブラリ/FileMaker Server/Database Server/bin/fmsadmin
