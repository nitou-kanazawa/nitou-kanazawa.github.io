---
title: ジェネリックの共変性と反変性
description: 
categories: [C#]
tags:
  - C#
  - Generic
---

## 概要

`C#4`から，ジェネリックなインタフェース，もしくはデリゲートに対して，共変性・反変性を実現するための仕組みが追加された．

共変性のためには「型を出力(get)にしか使わない」，反変性のためには「型を入力(set)にしか使わない」という保証が必要なため，`in`/`out`の修飾子をつける必要がある．

また，それぞれ以下のように読みかえるとイメージしやすい．
- 共変性 → 出力互換性
- 反変性 → 入力互換性

```cs
Func<Derived> y = a;
Func<Base> x = y;
```

## 共変性 (convariance)

例として`IReadOnlyList<T>`について考えてみる．`IReadOnlyList<T>`はList<T>や１次元配列を読み取り専用とするインタフェースである．




## 反変性 (contravariance)

## 余談

#### C#の配列は共変

ジェネリックがなかった`C#1`の頃の名残で，配列には以下のような代入ができる．

```cs
string[] derivedItems = {"alpha", "beth", "gamma"};
object[] basedItems = derivedItems;
```

しかし，配列が読み取り専用(`out`)になっているわけではないため，値の代入は行えてしまう．例えば以下のコードのように不正な代入をすると実行時エラーとなる．

```cs
string[] derivedItems = {"alpha", "beth", "gamma"};
object[] baseItems = derivedItems;

// コンパイルは通るが，実行時エラーが出る
baseItems[1] = 100;
```



## 参考資料
- [MS: ジェネリックの共変性と反変性](https://learn.microsoft.com/ja-jp/dotnet/standard/generics/covariance-and-contravariance)
- [未確認飛行C: ジェネリクスの共変性・反変性](https://ufcpp.net/study/csharp/sp4_variance.html)
- [qiita: そういうことか！ どこで何を読んでも「はあ？」だった人が最後にもう一度だけ挑戦する「共変性」と「反変性」](https://qiita.com/CodeOne/items/730480791c2e98b40d66)
- [hatena: C# - 共変性（covariance）・反変性（contravariance）](https://fineworks-fine.hatenablog.com/entry/2023/06/29/073000)
- [hatena: 【Unity C#】 IReadOnlyListの紹介](https://tsgcpp.hateblo.jp/entry/2021/10/30/184507)