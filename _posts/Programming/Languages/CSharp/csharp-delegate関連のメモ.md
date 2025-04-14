---
title: SharpLab
categories: [ C# ]
tags:
  - C#
  - ラムダ式
---



#### 関連する要素
- デリゲート (C#1~)
- `Predicate` (C#2~)
- 匿名メソッド (C#2~)
- `Action` / `Func` (C#3~)
- ラムダ式 (C~)

> ![C#の機能追加](https://anderson02.com/wp-content/uploads/2022/07/1-30.png)
> 引用: [C#でラムダ式を書く方法 #コラム_C#の歴史とここまでのまとめ](https://anderson02.com/cs/lambda/lambdacolumn/)





---

#### [デリゲート][MS デリゲート]
> デリゲートは、特定のパラメーター リストおよび戻り値の型を使用して、メソッドへの参照を表す型です。 

```cs
public delegate int PerformCalculation(int x, int y);
```

※同様のシナリオで，呼び出し規則をより細かく制御する必要がある場合のために、`C# 9`からは**関数ポインター**が追加された．

#### 匿名メソッド

```cs
```

#### ラムダ式

匿名関数や式木を簡単に生成できる．

```cs
```

以下の問題を引き起こすこともある
- クロージャ（閉包）の罠
- イベントの購読解除忘れ
- 読みやすさ・保守性の低下
- パフォーマンスとGC
- デバッグのしにくさ
- 共変性と反変性




---

## 参考資料
- 未確認飛行C: [デリゲート](https://ufcpp.net/study/csharp/sp_delegate.html)
- 未確認飛行C: [ラムダ式](https://ufcpp.net/study/csharp/sp3_lambda.html)
- ピーコックアンダーソン: [C#でラムダ式を書く方法1](https://anderson02.com/category/cs/lambda/)




<!-- Link -->
[MS デリゲート]: https://learn.microsoft.com/ja-jp/dotnet/csharp/programming-guide/delegates/?view=netframework-4.7.2
[MS 関数ポインター]: https://learn.microsoft.com/ja-jp/dotnet/csharp/language-reference/proposals/csharp-9.0/function-pointers
