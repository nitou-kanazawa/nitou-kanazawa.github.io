---
title: Jekyllで使用できる変数
category: Web
tags:
  - Jekyll
---

`Jekyll`では、さまざまな変数を利用してコンテンツを動的に生成することができる．以下に、Jekyllで使用できる主要な変数をカテゴリ別にまとめる．

<!-- more -->

## グローバル変数

- `site`: 
- `page`: 
- `layout`: 
- `jekyll`: 
- `theme`: 
- `content`: 
- `paginator`: 


## サイト全体に関する変数

#### site
`_config.yml` の設定やサイト全体の情報を取得できる．

```
{{ site.title }}
{{ site.url }}
{{ site.posts }}
```

- `site.title`: サイトのタイトル
- `site.url`: サイトのベースURL
- `site.posts`: すべての投稿のリスト

## ページごとの変数

#### page
現在のページに関する情報を取得できます。

```
{{ page.title }}
{{ page.url }}
{{ page.date }}
```

- `page.title`: ページのタイトル
- `page.url`: ページのURL
- `page.date`: ページの作成日

## 投稿に関する変数

### post
各投稿に関連する情報を取得できる．

```
{{ post.title }}
{{ post.date }}
{{ post.content }}
```

- `post.title`: 投稿のタイトル
- `post.date`: 投稿の日付
- `post.content`: 投稿の本文

## ループ内で使用する変数

### forloop
ループの現在の状態を把握するための変数．

```liquid
{% for post in site.posts %}
  {{ forloop.index }}: {{ post.title }}
{% endfor %}
```

- `forloop.index`: ループのインデックス（1から開始）
- `forloop.first`: 最初の要素かどうか（true/false）
- `forloop.last`: 最後の要素かどうか（true/false）


## 参考資料
- [Jekyll: 公式ドキュメント](https://jekyllrb.com/docs/variables/)