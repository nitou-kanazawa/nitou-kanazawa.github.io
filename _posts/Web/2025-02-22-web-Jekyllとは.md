---
title: Jekyllとは
category: Web
tags:
  - Jekyll
  - Ruby
id: e3ae5516-8075-4dd0-b368-8819db6ff114
---

`Jekyll(ジキル)`は`Ruby`で開発されている静的サイトジェネレータ．
データベースを必要とせず、WordPressのようなコンテンツ管理システムを使用することなく、個人ブログ、ポートフォリオサイト、ドキュメントサイトなど、様々なタイプの静的サイトを構築することが可能．

<!-- more -->

`GitHub`の共同創業者であるTom Preston-Wernerによって開発されており，`GitHub Pages`のバックエンドエンジンにも使用されている．

[GitHubリポジトリ](https://github.com/jekyll)

ドットインストールの[Jekyll入門](https://dotinstall.com/lessons/basic_jekyll)を参考に学習した．

## Jekyllの導入
`Jekyll`を利用するには，先に`Ruby`をインストールしておく必要がある.
公式サイトの[ドキュメント](https://jekyllrb.com/docs/installation/#requirements)にしたがってWindowsに導入する．

> **Requirements**
> - `Ruby` version 2.7.0 or higher, including all development headers (check your Ruby version using ruby -v)
> - `RubyGems` (check your Gems version using gem -v)
> - `GCC` and `Make` (check versions using gcc -v,g++ -v, and make -v)

<details>
<summary>インストール手順</summary>

#### 
Windowsに`Ruby`をインストールするため，[`RubyInstaller`](https://rubyinstaller.org/)を使用する．
[RubyInstaller Downloads](https://rubyinstaller.org/downloads/)から`Ruby+Devkit`版をダウンロードして，インストール．

<img src="{8E1E9F7C-9570-43CB-BC7A-0A306C6BDB81}.png" alt="" width="300">
<img src="{8C855C44-9583-4961-AA4F-2C61A3338E70}.png" alt="" width="300">

</details>


## JekyllのCLIコマンド

- `jekyll build`：_siteディレクトリに静的なサイトを生成する
- `jekyll serve`：サイトを構築し、ローカルマシンでウェブサーバーを起動することで、http://localhost:4000を使いブラウザでサイトをプレビューすることが可能になる
- `jekyll new [site name]`：指定されたサイト名で新しいディレクトリに新しいJekyllサイトを作成する
- `jekyll doctor`：設定や依存関係の問題があれば出力する
- `jekyll clean`：生成されたサイトファイルが格納されている_siteディレクトリを削除する
- `jekyll help`：Jekyllのヘルプドキュメントを出力する
- `jekyll serve` --draft：_draftsディレクトリにあるすべての投稿を含めJekyllサイトを生成

> ![NOTE]
> プロジェクト毎のgemファイル設定を反映させるには，`bundle exec jekyll serve`のように`bundle exec`を先頭に入れる必要がある？（要確認）

詳細は[ドキュメント](https://jekyllrb.com/docs/usage/)を確認


## Jekyllプロジェクトのディレクトリ構成

- `_layouts` : 
- `posts` : 
- 



## Jekyllの設定ファイル

#### サイト全体（_config.yaml）

サイト全体の設定は`_config.yml`という名前のYAMLファイルに記述する．
一般的な設定オプションを以下に示す．

- `title` : サイトのタイトル
- `description` : サイトの短い説明
- `baseurl` : （サブディレクトリでホストする場合）サイトのサブディレクトリ
- `url` : サイトのベースURL
- `permalink` : 投稿とページのURL構造
- `exclude` : サイト生成プロセスから除外するファイルまたはディレクトリの一覧
- `include` : サイト生成プロセスに含めるファイルまたはディレクトリの一覧
- `paginate` : ページネーション使用時に1ページに表示する投稿の数
- `plugins` : 読み込むJekyllプラグインの一覧
- `thema` : デフォルトで`minima`に設定される
  - 各種設定を行うことで，任意の他のテーマを使用することができる

設定ファイルにカスタム変数を作成し、サイトのテンプレート、レイアウト、およびインクルードでそれを使用することができまる．例えば、`author_name`という変数を作成し、テンプレートで`{{ site.author_name }}`のように使用することができます。


#### Markdown記事（YAML front matter）

各記事の設定は`Markdown`上部に`YAML front matter`で記述する．
`#`以降はコメントとして扱われる．

```md
---
# YAML front matter
layout: default
title: Blogging Like a Hacker
---
  :
記事本文
  :
```

[](https://jekyllrb.com/docs/front-matter/)



- `layout`
- `title` : 記事のタイトル
- `description` : 記事の説明文





## 静的サイトの作成

以下のコマンドを実行すると静的サイトを作成することができる．

```
jekyll new my-blog
```

実行すると以下のディレクトリとファイルが生成される

```
├── _posts
├── .gitignore
├── _config.yml
├── 404.html
├── about.markdown
├── Gemfile.lock
├── index.md
└── README.md
```






## Tips

#### execulete要素

デフォルトでは、Jekyllでは以下に当てはまるファイルやフォルダをビルドしない．

- /node_modules または /vendor フォルダーに配置されている
- `_`、`.`、または`#`で始まる
- `~` で終わる
- 構成ファイルの exclude 設定によって除外される

これらのファイルの中に Jekyll で処理したいものがある場合、構成ファイルの include 設定を利用できる．



## テーマ


## 

---

## 参考資料

- [wiki: Jekyll](https://ja.wikipedia.org/wiki/Jekyll)
- [_: Jekyllで静的サイトを構築する方法](https://kinsta.com/jp/blog/jekyll-static-site/)
- [_: Jekyllとはなにか](https://www.codegrid.net/articles/jekyll-1/)
- [_: URLs and links in Jekyll](https://mademistakes.com/mastering-jekyll/how-to-link/)
