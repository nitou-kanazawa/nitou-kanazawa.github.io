---
title: UniTaskAsyncEnumerable
categories: [C#]
tags:
  - UniTask
  - UniRx
  - IAsyncEnumerable
---

## 概要

UniTaskAsyncEnumerableは`IAsyncEnumerable<T>`をベースとした非同期ストリームの機構．複数個の非同期処理を直列に扱うことが得意であり，`Observable`とは違った使い方ができる．


## IAsyncEnumerable

`IAsyncEnumerable<T>`は`C#8`で追加された非同期ストリームを表現するインタフェース．

```cs
public interface IAsyncEnumerable<out T> {
    IAsyncEnumerator<T> GetAsyncEnumerator(CancellationToken token);
}

public interface IAsyncEnumerator<out T> : IAsyncDisposable{
    T Current {get;}
    ValueTask<bool> MoveNextAsync();
}

public interface IAsyncDisposable{
    ValueTask DisposeAsync();
}
```

`IAsyncEnumerable<T>`からはイテレータである`IAsyncEnumerator<T>`が取得でき，この`MoveNextAsync()`メソッドを呼び出すことでイテレータを非同期的に進めることができる．

```cs
static async Task UseAsyncEnumerableAsync(IAsyncEnumerable<T> asyncValues){
    // 非同期イテレータを取得
    var e = asyncValues.GetAsyncEnumerator();

    // 
    while(e.MoveNextAsync()){
        var value = e.Current;
        Console.WriteLine(value);
    }
}
```

なお，実際に利用する際は糖衣構文の`foreach`を用いるのが一般的である．

```cs
static async Task UseAsyncEnumerableAsync(IAsyncEnumerable<T> asyncValues){
    // await foreach で IAsyncEnumerable を消費できる
   await foreach(var value in asyncValues){
        Console.WriteLine(value);
   }
}
```

## UniTaskAsyncEnumerable



## 参考資料
- [Cygame: UniTask v2 – Unityのためのゼロアロケーションasync/awaitと非同期LINQ](https://tech.cygames.co.jp/archives/3417/)
- [qiita: UniTask Ver2 、UniTaskAsyncEnumerableまとめ](https://qiita.com/toRisouP/items/8f66fd952eaffeaf3107)
- [hackMD: UniTaskがパワーアップ！『UniTask v2』を使おう！](https://hackmd.io/@-xLrSnFfROOeIeRnENCWcQ/HkVAMY5Sd)