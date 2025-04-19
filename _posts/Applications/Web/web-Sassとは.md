---
title: Sassとは
categories: [ Web ]
tags:
  - CSS
  - Sass
---

`Sass（サース）`とは Syntactically Awesome Style Sheets の略で，CSSをより効率的に記述するためのスタイルシート言語．


## Sassの特徴

#### 変数の定義

Sassでは`$変数名`で変数を定義し、色やフォントサイズなどを一元管理できる．

```scss
$primary-color: #3498db;

body {
  background-color: $primary-color;
}
```

#### ネスト構造

```scss
nav {
  background: #333;
  ul {
    list-style: none;
    li {
      display: inline-block;
      a {
        color: white;
      }
    }
  }
}
```

#### 継承
共通のスタイルを複数のセレクタで共有できる．

```scss
%button-style {
  padding: 10px;
  border: none;
  cursor: pointer;
}

.btn-primary {
  @extend %button-style;
  background-color: blue;
  color: white;
}
```


---
## 参考資料
- [qiita: Sassで最初に覚えること4選](https://qiita.com/f-ono/items/3e947c32dc0a35d0f77d)


<!-- リンク -->
