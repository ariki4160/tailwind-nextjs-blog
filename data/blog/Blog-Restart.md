---
title: ブログを再開します。ツールをHugoからGatsby.jsに変更しました。
date: '2020-08-15T15:05:19.18'
template: 'post'
draft: false
slug: 'blog-restart-from-hugo-to-gatsbyjs'
category: 'Web Development'
tags:
  - 'Gatsby.js'
  - 'Hugo'
  - 'Web Development'
summary: 'しばらく更新していなかったブログを再開します。以前は、Hugoを使って運用していましたが、Gatsby.jsとGitHub Pagesの構成での運用に変更しました。これまでのブログの運営方法の中で、冗長と思われるフローを改善して、記事作成に注力できる環境を構築しました。'
socialImage: '/media/blog-restart-from-hugo-to-gatsby.jpg'
---

しばらく更新していなかったブログを再開します。以前は、Hugo を使って運用していましたが、Gatsby.js と GitHub Pages の構成での運用に変更しました。これまでのブログの運用方法の中で、冗長と思われるフローを改善して、記事作成に注力できる環境を構築しました。

## 以前のブログの運用方法

以前のブログ　[Leisurely Web Programing](https://hugo.vivo-one.net/)　は静的サイトジェネレーターの Hugo を使って運用していました。Go で構築されている Hugo は、ビルドが圧倒的に速かったです。しかし、私の運用方法は、まだ改善の余地のあるものでした。その時の運用方法は、自分のパソコンで記事を書き、ビルドをして、生成された public フォルダの中身をレンタルサーバの公開ディレクトリに rsync でアップロードするというものでした。Bitbucket にて、ソースを管理していましたが、それはただ、ソースの保管をしている意味しかありませんでした。

ソースがレポジトリサービス上にあるのであれば、そこでビルドとテストをして、デプロイまで出来ることは分かっていたのですが、ブログの更新自体をしなくなって、手付かずの状態でした。

![blog-restart-from-hugo-to-gatsby](/static/images/post/blog-restart-from-hugo-to-gatsby.jpg)

## 改善したこのブログの運用方法

ブログを再開するにあたり上記の問題の解決も含めて、ツール、運用環境の検討をしました。Hugo と Bitbucket の環境でも、問題点を解消できる運用は出来るのですが、他のツール、運用環境を使ってみたいので調査をしました。Gatsby.js と GitHub Actions、GitHub Pages で運用することにしました。

- [Gatsby](https://www.gatsbyjs.com/)　静的サイトジェネレーター　 React で作られている
- [GitHub Actions](https://github.co.jp/features/actions)　 GitHub から直接コードをビルド、テスト、デプロイ
- [GitHub Pages](https://pages.github.com/)　 GitHub リポジトリから GitHub Actions を経由してホスト

Gatsby.js のスターターキットを使ってサイトを制作しました。自分のパソコンで記事を作成します。Hugo と同じ静的サイトジェネレーターのカテゴリのツールなので、プロジェクト内のファイルを確認すれば、なんとなく、そのファイルの役割は分かりました。

記事ができたら、GitHub のレポジトリに push します。push をきっかけに GitHub Actions の機能が動作して、GitHub 上でコードのビルド、テスト、デプロイが走ります。エラーが発生しても、どこでエラーが発生したのかが追えるように記録されています。GitHub Pages にデプロイされたサイトが公開されます。記事ファイルを Markdown 形式で書いて、GitHub に push するだけで、後の工程は、すべて自動化できました。
