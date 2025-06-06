---
title: Swiftの基本文法
category: Swift
tags:
  - Swift
id: 0a7062ebbc9787f2d9c8
---

Swiftの基本文法に関するメモ．初学者の躓きどころは`Optional`と`Closures`だと耳にしたので、その辺を押さえておきたい．


---
## 項目
- 変数と定数
- Optional
- 関数

## 変数と定数

変数は`var`，定数は`let`で宣言する．

```swift
// 変数
var mutable = "Apple"
mutable = "Lemon"

// 定数
let immutable = "Apple"
immutable = "Lemon"   // Error - Cannot assign to value: 'immutable' is a 'let' constant
```

またnullは


## Optional

`nil`(null)を安全に扱うための型．（おそらく C#の null 許容型のようなもの）
値を取り出すにはアンラップ処理が必要．

```swift
// 宣言
let age: Int? = 42

// 値の取得
if age != nil{
  let unrap = age!  // アンラップ処理 (この方法でnilをアンラップするとエラー)
  …
}
```

アンラップ処理には以下のように複数の方法があるらしい．

- 強制アンラップ
- 暗黙的アンラップ
- Optional Binding
- Optinal Chaining
- Nil 結合演算子 (Nil-Coalescing Operator)

`nil`かどうかによる分岐は，`Optional Binding`によって簡単に書くことができる．
以下の if-else スコープ内では`Int型`として扱えている．

```swift
var optionalValue: Int? = 1
if let value = optionalValue {
    print("Value: '\(value)'")
} else {
    print("Couldn't bind an optional value")
}
```

#### 参考
- [Apple: ドキュメント](https://developer.apple.com/documentation/swift/optional)
- [zenn: オプショナル型の意味と使い方をおさらい](https://zenn.dev/z_ypi/articles/7a3778ffdf4d9f)
- [_: SwiftでNullの判定をするための10選](https://jp-seemore.com/app/15407/)

## 関数

関数は以下のように定義する．

```swift
func greet(person: String) -> String {
    let greeting = "Hello, " + person + "!"
    return greeting
}
```

１行のみの場合は return を省略できる．

```swift
func greet(person: String) -> String {
    "Hello, " + person + "!"
}
```

また，特徴的な機能として，
関数の引数に「引数ラベル（呼び出し用の名前）」をつけて可読性をあげることが可能．

```swift
// 定義
func move(to office: String, from home: String) {
    print("\(home)から\(office)に移動")
}
// 使用
move(to: "渋谷", from: "中目黒")  // ※引数ラベルによって自然な英文として表現
```

## クロージャ

他言語のラムダ式や匿名関数などにあたる．
以下のように使用する．

```swift
// 定義
var decorate: (Int) -> String = { number in
    return "[[\(number)]]"
}
// 使用
decorate(100) // "[[100]]"
```



以下のようにクロージャは省略記法が用意されている．
（特に最後の２つは多言語でみないものに思える）

```swift
let names = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]
// 通常
var sortedNames = names.sorted(by: { (s1: String, s2: String) -> Bool in
    return s1 > s2
})

// 型推論
sortedNames = names.sorted(by: { s1, s2 in s1 > s2 })

// $による引数参照
sortedNames = names.sorted(by: { $0 > $1 } )

// 引数の最後がクロージャの場合、省略可能
sortedNames = names.sorted { $0 > $1 }

// sorted(by:)に大なりオペレータだけを渡す書き方もできる
sortedNames = names.sorted(by: >)
```

#### トレイリングクロージャ
最後の引数がクロージャだった場合，`()`を省略できる？
    [TODO] 詳細を確認する

<!-- 基本的に`{...}`という形になる． -->


## 列挙型

列挙型は以下のように定義する．

```swift
enum CompassPoint {
    case north
    case south
    case east
    case west
}

var point = CompassPoint.north
point = .south  // 型推論で省略可（※pointの型が分かっている）
```

Switch 文に列挙型を渡した場合，すべての case が網羅されていなければコンパイルエラーとなる．
（default case がある場合を除く）

また`Associated Value`という任意の値と紐づける？機能もある．

```swift
// 定義
enum State {
  case success
  case failure(Error)
}

// Switch文
struct DummyError: Error {}
let state: State = .failure(DummyError())
switch state {
case .success: print("Success")
case let .failure(error): print("Failure: \(error)")  // ※パターンマッチングで関連付けられた値を取得
}
```

## struct と class

以下のように定義できる．
Swift では基本的に struct を使用することが推奨されているらしい．

```swift
struct SomeStructure {
    // structure definition goes here
}
class SomeClass {
    // class definition goes here
}
```

#### 型プロパティ


## Protocols

protocol は、特定の機能に適したメソッドや property 等の I/F を定義するもの．
protecol の適用（実装）は通常の型の後ろに対象 protocol を指定する方法と，
`extension`キーワードで指定する方法の２パターンがある．

```swift
// Protocol定義
protocol ProtocolA {
    var mustBeSettable: Int { get set }
    var doesNotNeedToBeSettable: Int { get }
    func foo()
}
protocol ProtocolB{
    func hoge()
}

// ※extensionによるprotocolのデフォルト実装
extension ProtocolA {
    func foo() {
        print("someMethod called")
    }
}

// structへのprotocolの適用
struct SomeStructure: ProtocolA {
    var mustBeSettable: Int
    let doesNotNeedToBeSettable: Int
}

// ※extensionによるprotocolの適用
extension SomeStructure: ProtocolB {
    func hoge() {
        print("anotherMethod called")
    }
}
```

`extension`で何らかの定義を行うファイルを作成する場合，
慣習的に`Hoge+fuga.swift`と命名するらしい．
（例えば `User` クラスのモックは`User+mock.swift`）

## Generics


## 参考資料
- [Mixi: iOS研修](https://www.youtube.com/watch?v=-CIJkjv8yJA&t=4300s)
- [](https://github.com/mixigroup/ios-swiftui-training/tree/main)
