---
title: readonlyで宣言されたstruct
description:
categories: [C#]
tags:
  - C#
---

##### struct で宣言

sturct内で`readonly`で宣言されたフィールドに対して，[^1]

```cs
public struct Foo {
    private readonly int _num;
    public int Num => _num;

    public int GetNum() => _num;
}

var foo = new Foo(5);
int num1 = foo.num;         // フィールドアクセス コピー無し
int num2 = foo.Num;         // プロパティアクセス コピー発生
int num3 = foo.GetNum();    // 関数呼び出し コピー発生
```


#### readonly struct で宣言

```cs
public readonly struct Foo {
    private int _num;
    public int Num => _num;

    public int GetNum() => _num;
}

var foo = new Foo(5);
int num1 = foo.num;         // フィールドアクセス コピー無し
int num2 = foo.Num;         // プロパティアクセス コピー無し
int num3 = foo.GetNum();    // 関数呼び出し コピー無し
```


## 参考資料
- [qiita: C# Structパフォーマンス向上Tips](https://qiita.com/old_friend/items/1c9a0e47066c1ad0c987)


<!-- リンク -->
[^1]: https://ufcpp.net/study/csharp/resource/readonlyness/#struct-readonly