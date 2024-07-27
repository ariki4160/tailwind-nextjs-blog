---
title: Cristian MihaiさんのNext.jsのポートフォリオサイトの構築の模写　その1
date: '2024-07-27T18:34:36'
template: 'post'
draft: false
slug: 'cristian-mihai-nextjs-tracing-01'
category: 'Web Development'
tags:
  - 'Next.js'
  - 'Tailwind CSS'
  - 'Framer Motion'
  - 'YouTube'
summary: 'Cristian MihaiさんのNext.jsのポートフォリオサイトの構築のYouTubeを拝見して、模写をしてみる　その1　環境構築編'
socialImage: '/media/node-development-ubuntu-volta_01.png'
---

## Cristian Mihai さんの YouTube

[Build and Deploy a Portfolio Website Using Next JS, Tailwind CSS & Framer Motion - YouTube](https://www.youtube.com/watch?v=dImgZ_AH7uA)

## 構築環境

- Windows11 Home
- WSL Ubuntu 22.04

## Next.js の最新版インストール時にアラート

```javascript
$ npx create-next-app@latest
Need to install the following packages:
  create-next-app@14.2.5
Ok to proceed? (y) y
npm WARN EBADENGINE Unsupported engine {
npm WARN EBADENGINE   package: 'create-next-app@14.2.5',
npm WARN EBADENGINE   required: { node: '>=18.17.0' },
npm WARN EBADENGINE   current: { node: 'v18.14.2', npm: '9.6.7' }
npm WARN EBADENGINE }
```

## バージョンの確認

Node.js のバージョン管理は volta を使用している

```bash
$ volta list node
⚡️ Node runtimes in your toolchain:

    v11.15.0
    v12.22.12
    v13.14.0
    v14.21.3
    v16.19.1
    v18.14.1
    v18.14.2 (default)
    v19.7.0
```

## node の最新バージョンをインストールしようとするとエラー

```bash
$ volta install node@latest

error: Could not unpack Node v22.5.1

Please ensure the correct version is specified.
Error details written to /home/ariki/.volta/log/volta-error-2024-07-26_00_09_58.510.log
```

## volta のハウツーサイト

- [Node.js のバージョン管理に Volta を推したい](https://zenn.dev/taichifukumoto/articles/how-to-use-volta)
- [Volta で npm パッケージのグローバルインストール - kun432's blog](https://kun432.hatenablog.com/entry/install-npm-packages-globally-with-volta)

## volta 自体のバージョン確認

```bash
$ volta --version
1.1.1
```

## 安定版の最新 node の確認

```bash
$ volta install node
success: installed and set node@20.16.0 as default
   note: this version of Node includes npm@10.8.1, which is higher than your default version (9.6.7).
      To use the version included with Node, run `volta install npm@bundled`
```

## メッセージに従い bundle のアップデートをしようとするがエラー

```bash
$ volta install npm@bundle
error: Could not find Node version matching "bundle" in the version registry.

Please verify that the version is correct.
```

## カレントバージョンは最新になっている

```bash
$ volta list node
⚡️ Node runtimes in your toolchain:

    v11.15.0
    v12.22.12
    v13.14.0
    v14.21.3
    v16.19.1
    v18.14.1
    v18.14.2
    v19.7.0
    v20.16.0 (default)
```

## 再度、Next.js の最新版をインストール

```bash
$ npx create-next-app@latest .
✔ Would you like to use TypeScript? … No / Yes
✔ Would you like to use ESLint? … No / Yes
✔ Would you like to use Tailwind CSS? … No / Yes
✔ Would you like to use `src/` directory? … No / Yes
✔ Would you like to use App Router? (recommended) … No / Yes
✔ Would you like to customize the default import alias (@/*)? … No / Yes
Creating a new Next.js app in /home/ariki/src/site/vivo-protfolio.

Using npm.

Initializing project with template: app-tw


Installing dependencies:
- react
- react-dom
- next

Installing devDependencies:
- postcss
- tailwindcss
- eslint
- eslint-config-next

npm WARN deprecated inflight@1.0.6: This module is not supported, and leaks memory. Do not use it. Check out lru-cache if you want a good and tested way to coalesce async requests by a key value, which is much more comprehensive and powerful.
npm WARN deprecated @humanwhocodes/config-array@0.11.14: Use @eslint/config-array instead
npm WARN deprecated rimraf@3.0.2: Rimraf versions prior to v4 are no longer supported
npm WARN deprecated @humanwhocodes/object-schema@2.0.3: Use @eslint/object-schema instead
npm WARN deprecated glob@7.2.3: Glob versions prior to v9 are no longer supported

added 355 packages, and audited 356 packages in 28s

136 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
Initialized a git repository.

Success! Created vivo-protfolio at /home/ariki/src/site/vivo-protfolio
```
