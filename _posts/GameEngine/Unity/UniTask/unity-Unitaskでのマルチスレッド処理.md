---
title: UniTaskでのマルチスレッド処理
categories: [ Unity ]
tags:
  - C#
  - UniTask
  - 非同期
---

UniTaskでマルチスレッド処理実行する方法は，`UniTask.RunOnThreadPool()`でスレッドプール上で実行するか，非同期処理内で`UniTask.SwitchToXXX`を使ってスレッドを切り替えるかの２通りがある．

## UniTask.RunOnThreadPool

```cs

```

※もともと`UniTask.Run`という命名だったが，ThreadPool上で動くという挙動が認識されづらかったため`UniTask.RunOnThreadPool`に改名されたらしい．



## UniTask.SwitchToXXX





## 参考資料
- [qiita: UniTaskでマルチスレッド処理と例外処理](https://qiita.com/toRisouP/items/0c94002a092fcb29de22)
- [zenn: UniRx/UniTask/SynchronizationContextでメインスレッドに切替](https://zenn.dev/shiena/scraps/936798e4b62976)
- [HackMD: UniTaskを使おう！](https://hackmd.io/@-xLrSnFfROOeIeRnENCWcQ/Bke4eFcrd)


<!-- リンク -->

[1]:https://x.com/shiena/status/1368436291071709184
