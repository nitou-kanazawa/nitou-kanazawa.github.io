---
title: データの編集UIを作成する
categories: [ Unity ]
tags:
  - Unity
  - uGUI
  - UniRx
---


## 概要

以下のような`Person`型のパラメータ編集を行うUIを作成する．また，`Person`型はそれなりに大きなサイズであるとする．※例題では，編集対象をパブリックなフィールドとしている．

```cs
public class Person {
  public string name;
  public int age;
}
```


#### 要件
- 編集画面は各 `Person` パラメータ（例：name, age）を編集するためのUIを持つ。
- 編集画面には `Save`, `Cancel` ボタンがある。
- `Save` を押下すると、編集内容が `Person` インスタンスへ反映される。
- `Cancel` を押下すると、編集前の値に戻る。
- 元のデータと編集中の値に差分がある場合のみ、`Save` と `Cancel` を押せるようにする。
- データ構造が拡張されても対応しやすいように ViewModel を導入する。


## 設計

編集対象のデータを一時格納するためのデータ型と，それを`Person`型へ適用するためのヘルパーを用意する．

 `PersonData` 構造体（編集データ）
```cs
public readonly struct PersonData {
    public readonly string Name;
    public readonly int Age;

    public PersonData(string name, int age) {
        Name = name;
        Age = age;
    }

    public PersonData WithName(string name) => new(name, Age);
    public PersonData WithAge(int age) => new(Name, age);

    public bool Equals(PersonData other) => Name == other.Name && Age == other.Age;
}

```
