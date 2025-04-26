---
title: Builder パターン
description: >-
  Composite（コンポジット，混成）は，構造に関するデザインパターンの１つ．
categories: [設計]
tags:
  - デザインパターン
  - GoF
mermaid: true
---

`Builder` （ビルダー， 建設業者） は，複雑なオブジェクトを段階的に構築できる生成に関するデザインパターン． このパターンを使用すると，同じ構築コードを使用して異なる型と表現のオブジェクトを生成することが可能．

身近な例だと，DIContainerの構築，Tweenインスタンスの生成などに用いられている．


ただし，適用できるのは必須のパラメータが少数であるときに限られる．

> <img src="https://refactoring.guru/images/patterns/content/builder/builder-ja.png?id=8a0ec32cd855b2abd8183768466a112a" width=450>
> 
> 画像出典: [Refactoring Guru – Builder パターン](https://refactoring.guru/ja/design-patterns/builder)  



---
## パターンの必要性

#### 課題


特にJavaでは，コンストラクタにデフォルト引数を与えることができないため，この問題が深刻なようだ．

[`Telescoping Constructor`](https://www.javabyexamples.com/telescoping-constructor-in-java) 

#### 解決策
この解決策の1つにあたるのが `Builder` パターンである．


---
## 他パターンとの関連
- `Abstract Factory` がすぐにプロダクトを返すのに対し，`Builder` ではプロダクト取得の前に幾つかの追加ステップが入る．
- `Abstract Factory`，`Builder`，`Prototype` はいずれも `Singleton` で実装できる．

---
## 参考資料
- Guru: [Builder](https://refactoring.guru/ja/design-patterns/builder)
- qiita: [Builderパターン](https://qiita.com/takutotacos/items/33cfda205ab30a43b0b1)
