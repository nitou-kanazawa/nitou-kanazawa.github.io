---
title: OSCとは
description: Open Sound Control (OSC) は、ネットワーク経由でリアルタイムにマルチメディア機器を制御するための軽量なメッセージ指向プロトコル．
date: 2025-04-27
categories:
  - Networking
tags:
  - OSC
preview: ""
mermaid: false
draft: true
---


OSCプロトコルについてのメモ書き．

---
## OSC (Open Sound Control) 

Wikipediaでは以下のように説明されている．

> OpenSound Control（OSC）とは、電子楽器（特にシンセサイザー）やコンピュータなどの機器において音楽演奏データをネットワーク経由でリアルタイムに共有するための通信プロトコルである。
> 引用: [wikipedia](https://ja.wikipedia.org/wiki/OpenSound_Control)


OSCは当初、リアルタイムの音楽演奏に使用するための、高精度、低遅延、軽量、かつ柔軟な通信手段として設計された．現在では音楽分野のみならず、幅広い分野で活用されている．


#### 特徴
OSCは `UDP` / `TCP` / `シリアル` など様々な輸送層で動作する．

- ネットワーク・プロトコル非依存：主に UDP を使うが TCP / SLIP / WebSocket なども実装可能
- 階層型アドレス空間：UNIX 風パス表記で自由に名前設計でき、ワイルドカードにも対応
- 多様なデータ型：32/64bit 整数・浮動小数点、文字列、バイナリ、T / F などを同梱可
- 1 µs 精度のタイムタグ：複数パケットをまとめて未来の時刻に実行する“バンドル”を標準装備

- 可搬性の高いバイト列：ビッグエンディアン固定でプラットフォーム間の差異を吸収


#### OSCメッセージの構造

`OSC`メッセージは**アドレス**と**データ**で構成される．

アドレス : "/fader/1"，"/note/41" など
データ : 123(int)，3.14(float)，"Hello!(string)" など


| フィールド       | 役割                      | 例                     |
| ---------------- | ------------------------- | ---------------------- |
| アドレスパターン | 階層パス<br>(ルートは`/`) | "/synth/filter/freq"   |
| 型タグ文字列     | データ型列<br>(先頭に`,`) | ,fii (= float,int,int) |
| 引数列           | 型タグに対応する値        | 440.0, 2, 0            |

単一メッセージ．

```
/oscillator/1/freq ,f 440.0
```

**バンドル**として複数メッセージを `64 bit NTP 時刻付き`で束ねることもできるらしい．遅延実行や同時トリガーに利用．

```
#bundle 3826489123  /light/1 ,i 255  /light/2 ,i 128
```



#### 対応ソフト

- [TouchOSC](https://hexler.net/touchosc)


---
## 参考資料
- qiita: [OSCとは？OSC通信についてまとめてみた](https://qiita.com/generosity_honda/items/904aaeb382f6496ab920)
- qiita: [【OSC何も分からん人向け】OSCでVRChatを操作してみよう！](https://qiita.com/mofurune/items/eab78dee10ace5735a9a)
- youtube: [OSCって何？UnityビジュアルスクリプティングでOSC通信してみよう！](https://www.youtube.com/watch?v=aGwpV28EF94)
- zenn: [VRChatがOSCに対応したので、まずはNode.jsでアバターをジャンプさせてみた](https://zenn.dev/tkyko13/articles/0c16ea15530e6e)




---
## UnityでOSCを利用する

- [jorgegarcia / UnityOSC](https://github.com/jorgegarcia/UnityOSC)
- [Iam1337 / extOSC](https://github.com/Iam1337/extOSC)
- [stella3d / OscCore](https://github.com/stella3d/OscCore)
- [hecomi / uOSC](https://github.com/hecomi/uOSC)
- [keijiro / OscJack](https://github.com/keijiro/OscJack)
  

| 観点           | uOSC                                       | extOSC                                      |
| -------------- | ------------------------------------------ | ------------------------------------------- |
| 導入           | Git URL (UPM) / unitypackage               | UPM ／ Asset Store                          |
| 実装規模       | **約 100 KB**・スクリプトのみ              | 700 KB 超・Editor 拡張多数                  |
| 受信方法       | C# イベント (`onDataReceived`) で一括      | インスペクター GUI でアドレスごとにバインド |
| 送信スレッド   | バックグラウンド送信用キューあり           | メインスレッド直送信                        |
| 依存ライブラリ | なし（純 C#）                              | Newtonsoft.Json ほか                        |
| 向く用途       | **軽量・スクリプト派**／ビルドサイズ最小化 | GUI で可視的にルーティングしたい時          |




---
## uOSC

Unity向けのOSC実装．


#### 参考記事
- 凹みTips: [Unity 向けの OSC 実装を作ってみた](https://tips.hecomi.com/entry/2017/08/20/193823)


<!-- Link -->
[CNMAT OSC 公式]: https://opensoundcontrol.stanford.edu/index.html
