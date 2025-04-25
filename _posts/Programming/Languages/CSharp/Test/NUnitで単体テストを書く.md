---
title: NUnitで単体テストを書く
categories: [C#]
tags:
  - C#
  - .NET
  - NUnit
---

`NUnit`はJavaの単体テストフレームワーク（`JUnit`）に触発されて開発された，.NET用の単体テストフレームワーク．元々は独立した開発者によって作成されていたが，現在は .NET Foundation によってサポートされている．

---

## テストに使用する属性

`NUnit`ではテストコードに属性を付与して

```cs
public class FooTests {

    [OneTimeSetUp]
    public void Init() { /* ... */ }

    [OneTimeTearDown]
    public void Cleanup() { /* ... */ }

    [SetUp]
    public void SetUp() { ... }

    [Test]
    public void Test() { }

    [TestCase(1, 1, 2)]
    [TestCase(3, 5, 8)]
    public void AddTest(int a, int b, int anser) { }
}
```

[属性一覧](https://docs.nunit.org/articles/nunit/writing-tests/attributes.html)

#### 主要な属性

| 属性            | 説明                                             |
| --------------- | ------------------------------------------------ |
| SetUp           | [Test] 属性ごとに直前に実行される                |
| TearDown        | [Test] 属性ごとに直後に実行される                |
| OneTimeSetUp    | [TestFixture] 属性ごとに1度だけ直前に実行される  |
| OneTimeTearDown | [TestFixture] 属性ごとに1度だけ直後に実行される  |
| TestCase        | 書いたTestCaseの数だけ変数値を指定してテストする |

---

## アサーション

どのテストフレームワークであっても，アサーションは単体テストの中心的な存在である．`NUnit`では`Assert`クラスの静的メソッドとして各種アサーションが用意されている．



#### Classic Model

`Assert.That()` 以外のメソッドでの評価を [**Classic Model**][ClassicModel] と呼ぶ．

> Classic Meodel は新機能の追加が止まっているため，公式からは次に挙げるConstraint Modelを使用することが推奨されている

```cs
```

#### Constraint Model

`Assert.That()` での評価を [**Constraint Model**][Constraint Model] と呼ぶ．`Assert.That()`では第１引数に「評価対象」，第２引数に「制約条件」を引き渡す．例えば，文字列の簡単なアサーションは次のようになる．

```cs
Assert.That(myString, Is.EqualTo("Hello"));
```

`Is.EqualTo`はNUnitの**構文ヘルパー**の１つで，`EqualConstraint`を生成している．先ほどの更新コードは以下と等しくなる．

```cs
Assert.That(myString, new EqualConstraint("Hello"));
```

制約条件の詳細は[ドキュメント](https://docs.nunit.org/articles/nunit/writing-tests/constraints/Constraints.html)を確認するとして，ここでは`Assert.That()`の一般的な使用例を示す．

```cs
// 条件式がtrueだったら成功
Assert.That(1 < 10);
            
// 1個目の引数が2個目より小さければ成功
Assert.That(10, Is.LessThan(100));

// 1個目の引数が2個目の引数の範囲内なら成功
Assert.That(10, Is.InRange(0, 100));

// 1個めの引数の文字列が2個目の文字列で始まっていたら成功
Assert.That("Example", Does.StartWith("Ex"));

// 1個めの引数の文字列に2個目の文字列が含まれていたら成功
Assert.That("Example", Does.Contain("xamp"));

// 1個めの引数の文字列が2個目の文字列で終わっていたら成功
Assert.That("Example", Does.EndWith("ple"));

// 1個めの引数の文字列が2個目の正規表現にマッチしたら成功
Assert.That("Example", Does.Match("Ex*"));
```

#### Special Assertions

**Special Assertions** には明示的にテスト結果を返すメソッドが分類される．検査ロジックを自前で用意する場合に使用する．他のアサーションと同様に引数にメッセージを渡すこともできる．

- `Assert.Pass()`: テスト結果を成功にする．
- `Assert.Fail()`: テスト結果を失敗にする．
- `Assert.Ignore()`: テストを無視する．
- `Assert.Inconclusive()`: テストを保留する．

---

## 参考資料
- qiita: [[.NET][C#]NUnitを使用して単体テスト自動化　基本編](https://qiita.com/suganury/items/d255ae140373af7d0146)


<!-- Link | Document -->
[NUnit Document]: https://docs.nunit.org/articles/nunit/intro.html
[ClassicModel]: https://docs.nunit.org/articles/nunit/writing-tests/assertions/assertion-models/classic.html
[Constraint Model]:https://docs.nunit.org/articles/nunit/writing-tests/assertions/assertion-models/constraint.html
