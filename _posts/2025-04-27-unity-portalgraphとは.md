---
title: Portalgraphとは
description: ""
date: 2025-04-27
categories:
  - Unity
tags:
  - Unity
  - VR
  - VIVEトラッカー
preview: ""
mermaid: false
---

XでUnityちゃんライブステージを複数のモニタに投影している動画がまわってきて，`Portalgraph`について知った．

---
## Portalgraphとは

> Portalgraphは、プロジェクターでVR空間を楽しむUnity用ソフトウェア開発環境です。プロジェクタースクリーンの中に本当に空間が存在し、好きな角度で3Dでその空間を覗き込むことが出来る体験ができます。

<img src="https://portalgraphvr.gitbook.io/~gitbook/image?url=https%3A%2F%2F2416823498-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FaJCTlOkQcgkhVMLcuHBm%252Fuploads%252FMRCQKiz0BrjgU6Kbf2x8%252FIMG_6869_.jpg%3Falt%3Dmedia%26token%3D2039b65e-38c2-432f-a2c0-25996f1d90f7&width=768&dpr=4&quality=100&sign=12970a2a&sv=2" alt="" width=400>

[公式サイト][Portalgraph 公式サイト] / [ドキュメント][Portalgraph ドキュメント] / [BOOTHストア][Portalgraph BOOTHストア]

#### 視点の検出

> Portalgraphはユーザーの視点を検出し、その視点に合わせた映像を3Dで生成し表示します。視点の検出はWebカメラによる顔認識か、VIVEトラッカーを頭部に装着することで行います。3D映像装置は3Dプロジェクター、3Dテレビ、アナグリフ等に対応します。

- Webカメラによる顔認証
- [VIVEトラッカー][VIVEトラッカー]（頭部装着）による検出

#### 必要なもの
- Webカメラ付きでUnityが動くPC
- Portalgraphランタイムのインストール
- Unity 2019.4以上
- 赤青3Dメガネ


--- 
## SDK

#### SDK 
BOOTHで販売されている[Portalgraph SDK (個人利用向け)](https://portalgraph.booth.pm/items/3213218) を入手する．
※2025/05 現在，`Unity2023` / `Unity6` の**URP**には対応していない．


> ※出来ること
・Portalgraphを使ったアプリケーションの開発、無料配布、1タイトルあたり総額200万円未満の有料販売
・作成したソフトの無料イベント、プライベート空間での展示
・商業利用の検証目的での利用


#### 依存ライブラリ

- uOSC : Unity用の軽量OSC実装．


---
#### キャリブレーション

画面のキャリブレーション方法は，Youtube動画で解説されている．

[1画面](https://www.youtube.com/watch?v=qchLXv79f1A)
[2画面以上](https://www.youtube.com/watch?v=uTJq9aFyWgA)

--- 
## 






<!-- Link -->
[VIVEトラッカー]: https://www.vive.com/jp/accessory/tracker3/



[Portalgraph 公式サイト]: https://www.portalgraph.com/ja
[Portalgraph ドキュメント]: https://portalgraphvr.gitbook.io/portalgraphdokyumento
[Portalgraph BOOTHストア]: https://portalgraph.booth.pm/
