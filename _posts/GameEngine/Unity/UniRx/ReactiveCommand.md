---
title: ReactiveCommand
categories: [Unity]
tags:
  - Unity
  - UniRx
---

`ReactiveCommand` は「実行可能かどうか」を動的に制御できる `ICommand` のリアクティブ版．`IObservable<bool>` から生成される．


---


```cs
var canExecute = Observable.Return(true);
var command = new ReactiveCommand(canExecute);

command.Subscribe(_ => {
    Debug.Log("Execute");
})
```


---
## 参考資料
- qiita: [【UniRx】 ReactiveCommand/AsyncReactiveCommandについて](https://qiita.com/toRisouP/items/c6fba9f01e6d15dabd79)
