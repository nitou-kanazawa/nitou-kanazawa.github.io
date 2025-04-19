---
title: IDisposable関連の便利なクラス
categories: [Unity]
tags:
  - Unity
  - UniRx
---

`UniRx` は `IDisposable` 関連で便利なクラスがいくつか実装されている．

`CompositeDisposable`，`SerialDisposable`，`CancellationDisposable` あたりは挙動がシンプルなので，導入しやすいと思う．これらを用いることで、生の `IDisposable` を直接扱うよりもコードの意図が明確になり、リソース管理の安全性も向上します．


---
## 購読のライフサイクル管理
1. `CompositeDisposable`
2. `CancellationDisposable`
3. `SerialDisposable`



ちなみに，UniRxの購読処理で返される `Disposable`オブジェクトは，複数回Dispose()を呼んでも例外は投げない実装になっているようだ．

---
## 1. CompositeDisposable

#### 特徴
- 複数の `IDisposable` をまとめて管理・破棄するためのクラス．
- Dispose() を呼ぶとすべての `IDisposable` をまとめて破棄．
- `AddTo()` 拡張メソッドで簡単に追加可能。

#### 使い方
```cs
var disposables = new CompositeDisposable();

var subscription1 = observable1.Subscribe(...);
disposables.Add(subscription1);                   // Addメソッドで追加
observable2.Subscribe(...).AddTo(disposables);    // IDisposableの拡張メソッドで追加


// 使いまわすならClear
disposables.Clear();  

observable3.Subscribe(...).AddTo(disposables);
observable4.Subscribe(...).AddTo(disposables);


// 使いまわさないならDispose
disposables.Dispose();  // Clear() + _disposedフラグをON

// ※これ以降にAddされた要素は即時Disposeされる
observable5.Subscribe(...).AddTo(disposables);  // Dispose!
```

#### 実装

`CompositeDisposable` は `ICollection<IDisposable>` を実装しており，内部に `List<IDisposable>` を保持している．



---
## 2. SerialDisposable

#### 特徴
- 常に1つの `IDisposable` だけを保持し，差し替えると前のを自動Disposeするクラス．
- 主に 再購読のたびに前の購読を捨てたいときに使う．

#### 使い方

```cs
var serialDisposable = new SerialDisposable();

// 購読1回目
serialDisposable.Disposable = observable1.Subscribe(...);

// 購読2回目 → 前のobservable1はDisposeされる
serialDisposable.Disposable = observable2.Subscribe(...);
```

以下のように、明示的な Dispose を省略し、より簡潔なコードにできる．

置き換え前のコード：
```cs
IDisposable _subscription;

void RunXXX() {
    _subscription?.Dispose();
    _subscription = observable.Subscribe(...);
}

void OnEnd() {
    _subscription?.Dispose();
    _subscription = null;
}
```

`SerialDisposable` を使った書き換え：
```cs
private readonly SerialDisposable _serial = new SerialDisposable();

void RunXXX() {
    _serial.Disposable = observable.Subscribe(...);
}

void OnEnd() {
    _serial.Dispose(); // 最後に一度DisposeするだけでOK
}
```






#### 実装

## 3. CancellationDisposable
`CancellationTokenSource` をラップし，`IDisposable` として扱えるようにしたクラス．非同期処理との連携に便利．

```cs
CancellationDisposable _cancelToken;

void StartTask() {
    _cancelToken = new CancellationDisposable();
    SomeAsync(_cancelToken.Token).Forget();
}

async UniTask SomeAsync(CancellationToken token) {
    await UniTask.Delay(3000, cancellationToken: token);
}

void CancelTask() {
    _cancelToken?.Dispose(); // tokenにキャンセルが通知される
}
```





--- 

| クラス名                     | 目的                                             | 上書き可能    | Disposeのたびに<br>前をDispose | 複数回<br>Dispose可能 | 備考                         |
| ---------------------------- | ------------------------------------------------ | ------------- | ------------------------------ | --------------------- | ---------------------------- |
| CompositeDisposable          | 複数の IDisposable をまとめて管理                | ✔（追加）     | ―                              | ✔                     | Add() / AddTo()で追加        |
| StableCompositeDisposable    | 最大8個までの軽量高速版 Composite                | ✖（固定数）   | ―                              | ✔                     | Create(d1, d2, …)で一括指定  |
| SerialDisposable             | 常に1つだけ保持し、代入ごとに前をDispose         | ✔             | ✔                              | ✔                     | Disposableプロパティで上書き |
| BooleanDisposable            | 単一フラグ付きの軽量Disposable                   | ✖             | ―                              | ✔                     | フラグチェック用などに便利   |
| SingleAssignmentDisposable   | 一度だけ Disposable を設定可能                   | ✖（一度のみ） | ―                              | ✔                     | 2回目以降の設定は例外        |
| MultipleAssignmentDisposable | 複数回代入可。ただし明示的に前を破棄しないと残る | ✔             | ✖                              | ✔                     | 自動Disposeなし注意          |


---
## 参考資料
- Cluster TechBlog: [UniRxのディープなつまずきの紹介](https://tech-blog.cluster.mu/entry/2022/02/21/174529)
- qiita: [UniRx入門 その2 - メッセージの種類/ストリームの寿命](https://qiita.com/toRisouP/items/851087b4c990d87641e6)
