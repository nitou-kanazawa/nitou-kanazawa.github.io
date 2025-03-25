---
title: Awaitable パターン
categories: [C#]
tags:
  - C#
  - 非同期
---






## Awaitable パターン

```cs
class Awaitable {
    public Awaiter GetAwaiter() { }
}

struct Awaiter {
    public bool IsCompleted { get; }
    public void OnCompleted(Action continuation) { }
    public T GetResult() { }
}
```

await可能な型は，

※ Unity6（2023）から追加された`Awaitable`クラスはこのAwaitableパターンに則って，async/await


## 参考記事

- 未確認飛行C: [非同期メソッドの内部実装]
- _: [第3回　非同期メソッドの内部実装とAwaitableパターンの独自実装](https://atmarkit.itmedia.co.jp/ait/articles/1211/02/news066.html)


- zenn: [Unity6以降のWeb向けライブラリにおけるAwaitableという選択肢](https://zenn.dev/drumath2237/articles/unity6-awaitable-web)
- qiita: [Awaitable 使いづらそう問題](https://qiita.com/sator_imaging/items/76fdd84373fca79269e2)