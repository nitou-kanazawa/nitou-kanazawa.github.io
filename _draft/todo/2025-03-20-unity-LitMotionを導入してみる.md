---
title: LiMotionを導入してみる
description: >-
  SharpLabはWeb上でC#の実行や使用メモリの確認などが行えるサイト．
categories: [Unity]
tags:
  - Unity
  - Tween
  - OSS
image:
  path: /assets/thumbnails/logo_unity.png
---

## 概要

これまでTweenライブラリにはネット上の情報が多い`DoTween`を用いていたが，以下の点で多少不満を感じる部分があった．

- アセットストアで配布されているため，他のUPMパッケージと比べて管理が少し面倒．
- `TextMeshPro`関連の機能は，有料版の`DoTween Pro`の方でしか使えない．
- DLL形式で配布されているので実装を確認できない．

そこでデータ指向設計によるハイパフォーマンスなTweenライブラリの「**LitMotion**」を試してみた．他にも候補は幾つかあったが，上記の条件を満たしていること，`UniTask`/`R3`との連携が可能なことから，こちらのOSSを選定した．


## LitMotion とは

実装方針などが[作者のブログ][LitMotion 解説記事]で解説されている．他のTweenライブラリの実装におけるパフォーマンス面の問題を言及し，それに対してDOTSを活用した実装について順を追って解説されている．大変勉強になった．

（DOTS関連は全く知識がないので，ここも年内には触ってみたい．）

#### 実装面に関して

Tweenインスタンスでのアロケーションをなくし，かつパフォーマンスを

- Object-PoolでのTweenインスタンス管理
- 外部からはインスタンスをラップした構造体で操作

#### API設計

TweenライブラリのAPIはコンポーネントに対する拡張メソッドがあるものと，そうでないものがある．`DOTween`や`Magic Tween`は前者，`LitTween`は後者である．

```cs
// MagicTween
transform.TweenPosition(Vector3.zero, Vector3.one, 2f);

// LitMotion
LMotion.Create(Vector3.zero, Vector3.one, 2f).BindToPosition(transform);
```

Easingなどの設定項目は他のTweenライブラリと同様にメソッドチェーンで行う．このとき，`Create-With-Bind`の流れになる設計により，可読性を向上している．

```cs
LMotion.Create(Vector3.zero, Vector3.one, 2f)
    .WithEase(Ease.OutQuad)
    .WithScheduler(MotionScheduler.LateUpdate)
    .BindToPosition(transform);
```

#### Observable, async/await

`LitMotion`では他の多くライブラリで実装されているSwquenceの機能を持たない．その代わりに`UniRx`/`UniTask`と連携して非同期なアニメーションを行う機能が提供されている．

```cs
// モーションをObservableとして作成する
var observable = LMotion.Create(-5f, 5f, 2f)
    .ToObservable();

// モーションをawaitで待機する
await LMotion.Create(-5f, 5f, 2f).BindToUnityLogger();
```

これは現在のUnityでは`async/await`が使えることや`UniTask`などの有用なライブラリが揃っていることから，わざわざSequenceを使う理由はないという思想によるもの．


## LitMotion の導入

PackageManager の"Add package from git URL."で以下を指定してインストール．
```
// 基本モジュール
https://github.com/annulusgames/LitMotion.git?path=src/LitMotion/Assets/LitMotion
// 
https://github.com/annulusgames/LitMotion.git?path=src/LitMotion/Assets/LitMotion.Animation
```

または`Packages/manifest.json`に以下を追加する．
```
{
    "dependencies": {
        "com.annulusgames.lit-motion": "https://github.com/annulusgames/LitMotion.git?path=src/LitMotion/Assets/LitMotion",
        "com.annulusgames.lit-motion.animation": "https://github.com/annulusgames/LitMotion.git?path=src/LitMotion/Assets/LitMotion.Animation"
    }
}
```


## 基本的な使い方




## 参考資料
- Annulus Games: [【Unity】LitMotion – データ指向設計による最速のトゥイーン実装](https://annulusgames.com/blog/lit-motion/)
- zenn: [LitMotion Guidebook](https://github.com/nitou-kanazawa/demo-unity-LitMotion.git)
- hatena: [LitMotion Animation を拡張する](https://yotiky.hatenablog.com/entry/litmotion_animationex)


<!-- リンク | リポジトリ -->
[LitMotion リポジトリ]: https://github.com/nuskey8/LitMotion
[UGUIAnimationSamples]: https://github.com/nuskey8/UGUIAnimationSamples

<!-- リンク | Unity Discussions -->
[LitMotion UnityDiscussion]: https://discussions.unity.com/t/litmotion-lightning-fast-and-zero-allocation-tween-library/936361/11

<!-- リンク | Assest Store -->

<!-- リンク | 記事 -->
[LitMotion 解説記事]: https://annulusgames.com/blog/lit-motion/