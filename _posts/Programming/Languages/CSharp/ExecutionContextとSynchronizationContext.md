---
title: ExecutionContextとSyncronizationContext
categories: [C#]
tags:
  - 非同期
---

## 概要

#### ExecutionContext


#### SyncronizationContext



#### UniTaskの場合

`UnitySynchronizationContext`

UniTaskは`SynchronizationContext`には依存せず，UnityのPlayerLoop上で動作している．


```cs
// PlayerLoop.Updateで実行する(yield return nullに等しい)
await UniTask.Yield();
 
// yield return new WaitForEndOfFrameに等しい
await UniTask.Yield(PlayerLoopTiming.LastPostLateUpdate);
 
// ここより下の処理をThreadPool上で処理
await UniTask.SwitchToThreadPool();
 
// PreUpdateで指定時間待つ(WaitForSecondsに近いが、呼び出し箇所が指定できる)
await UniTask.Delay(TimeSpan.FromSeconds(1), delayTiming: PlayerLoopTiming.PreUpdate);
 
// 30フレーム毎にUpdateを呼び出し
await UniTaskAsyncEnumerable.IntervalFrame(30, PlayerLoopTiming.Update).ForEachAsync(_ => { });
```


## 参考資料
