---
title: Span<T>とMemory<T>
description: >-
  Composite（コンポジット，混成）は，構造に関するデザインパターンの１つ．
categories: [C#]
tags:
  - C#
  - 構造体
  - GC
---


---
## 概要


---
## `Span<T>` / `ReadOnlySpan<T>` 型

`C#7`で導入された`System.Span<T>`は，配列や文字列などの**連続して並んだデータに効率的にアクセスする**ための型．`Span`を使用することで余計なアロケーションをさけつつ，高速な読み書きを可能とする．



---
## Memory型


---
## 参考資料
- [MS: System.Span<T> 構造体](https://learn.microsoft.com/ja-jp/dotnet/fundamentals/runtime-libraries/system-span%7Bt%7D )
- [_: 【C#】Span<T>とMemory<T>](https://annulusgames.com/blog/span-and-memory/)



<!-- リンク -->
[Span<T> 構造体]: https://learn.microsoft.com/ja-jp/dotnet/api/system.span-1?view=net-8.0
[ReadOnlySpan<T> 構造体]: https://learn.microsoft.com/ja-jp/dotnet/api/system.readonlyspan-1?view=net-8.0
