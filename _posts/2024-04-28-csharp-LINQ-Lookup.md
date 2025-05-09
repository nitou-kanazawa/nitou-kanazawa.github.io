---
title: LINQ | Lookup<TKey,TElement>
description: >-
  `System.Linq`名前空間に所属する`Lookup<TKey,TElement>`はキーを値または値のコレクションにマップする辞書のようなデータ構造をもつ．
date: 2024-04-28
categories: [C#]
tags:
  - C#
  - LINQ
---

## 概要

`System.Linq`名前空間に所属する`Lookup<TKey,TElement>`はキーを値または値のコレクションにマップする辞書のようなデータ構造をもつ．キーに値のコレクションを割り当てる場合は`Dictonary<TKey, IEnumerable<TElement>>`に類似した構造になるが，インスタンス生成後にキーや要素の追加は出来ないという違いがある．

<!-- more -->


## `Lookup<TKey,TElement>` の作成方法

`Lookup<TKey,TElement>` は直接インスタンス化できず，通常 `ToLookup` 拡張メソッドを使用して作成される

#### 例: `ToLookup` を使用した `Lookup<TKey,TElement>` の生成

```csharp
using System;
using System.Linq;
using System.Collections.Generic;

class Person {
    public string Name { get; }
    public string Department { get; }
    public Person(string name, string department) {
        Name = name;
        Department = department;
    }
}

class Program {
    static void Main() {
        var people = new List<Person> {
            new Person("Alice", "HR"),
            new Person("Bob", "IT"),
            new Person("Charlie", "IT"),
            new Person("David", "HR"),
            new Person("Eve", "Finance")
        };

        var lookup = people.ToLookup(p => p.Department);

        foreach (var group in lookup) {
            Console.WriteLine($"Department: {group.Key}");
            foreach (var person in group) {
                Console.WriteLine($"  {person.Name}");
            }
        }
    }
}
```

**出力例**
```
Department: HR
  Alice
  David
Department: IT
  Bob
  Charlie
Department: Finance
  Eve
```

## `Lookup<TKey,TElement>` の特長

1. **キーの重複が可能**
   - `Dictionary<TKey, TValue>` とは異なり，`Lookup<TKey,TElement>` では同じキーに複数の要素を関連付けることができる．

2. **不変のデータ構造**
   - インスタンス化後に変更ができないため，安全なデータ管理が可能．

3. **パフォーマンスの最適化**
   - `Lookup<TKey,TElement>` は `Dictionary<TKey, List<TElement>>` のような構造を内部的に持っており，高速な検索が可能．


## `Lookup<TKey,TElement>` の使用例

#### 指定したキーの要素を取得する

```csharp
var itDepartment = lookup["IT"];
foreach (var person in itDepartment) {
    Console.WriteLine(person.Name);
}
```

#### キーが存在するか確認する

```csharp
if (lookup.Contains("Marketing")) {
    Console.WriteLine("Marketing 部門が存在します。");
}
else {
    Console.WriteLine("Marketing 部門は存在しません。");
}
```

## `Lookup<TKey,TElement>` と `Dictionary<TKey, List<TElement>>` の比較

| 特性         | Lookup<TKey,TElement> | Dictionary<TKey, List<TElement>> |
| ------------ | --------------------- | -------------------------------- |
| 追加・削除   | できない              | 可能                             |
| 検索         | 高速                  | 高速                             |
| メモリ使用量 | 少なめ                | 多め                             |
| 初期化方法   | `ToLookup`            | コンストラクタ or `Add`メソッド  |


## まとめ

- `Lookup<TKey,TElement>` は `ToLookup` メソッドを使用して作成される．
- キーごとに要素をグループ化し，変更が不要なデータに適している．
- `Dictionary<TKey, List<TElement>>` に比べてメモリ効率がよく，高速な検索が可能．
- ただし、一度作成した後の変更ができないため，用途に応じて使い分ける必要がある．


## 参考資料
- [zenn: Lookup型使ってみたら便利だったっていう話](https://zenn.dev/amenonegames/articles/cac18c20ae72fa)
- [_: Lookup in C# - Code Maze](https://code-maze.com/csharp-lookup/)
- [_: LINQ ToLookup Method in C#](https://dotnettutorials.net/lesson/linq-tolookup-operator/)


<!-- リンク -->
[Lookup<TKey,TElement>]: https://learn.microsoft.com/ja-jp/dotnet/api/system.linq.lookup-2?view=net-8.0
