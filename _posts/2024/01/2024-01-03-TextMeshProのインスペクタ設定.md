---
title: TextMeshPro のインスペクタ設定
categories: [ Unity ]
tags:
  - Unity
  - TMPro
mermaid: true
---

`TextMeshProUGUI` のインスペクタ設定に関するメモ書き．


## TextMeshPro

```mermaid
classDiagram

  Graphic <|-- MaskableGraphic
  MaskableGraphic <|-- TMP_Text
  MaskableGraphic <|-- TMP_SubMeshUI

  TMP_Text <|-- TextMeshPro
  TMP_Text <|-- TextMeshProUGUI
```

## TextMeshProの設定値

`TextMeshProUGUI`のインスペクタでは下記の項目を設定できる

- **Text Input**
- Main Settings
  - Font Asset
  - Material Preset
  - Font Size
  - Vertex Color
  - Color Gradient
  - Override Tags
  - Spacing Options
  - Alignment
  - Text Wrapping Mode
  - Horizontal Mapping
  - Vertival Mapping
- Extra Settings


## 1. Text Input

![](/assets/img/Unity/TextMeshPro/TextMeshPro_インスペクタ01.png)


## 2. Main Settings
![](/assets/img/Unity/TextMeshPro/TextMeshPro_インスペクタ02.png)


## 3. Extra Settings
![](/assets/img/Unity/TextMeshPro/TextMeshPro_インスペクタ03.png)


## 参考資料

- hatena: [【Unity】TextMesh Proをアニメーションさせる～プログラマ編～](https://coposuke.hateblo.jp/entry/2020/06/07/020330)


<!-- リンク |  -->
[TextMeshPro マニュアル]: https://docs.unity3d.com/ja/Packages/com.unity.textmeshpro@3.0/manual/index.html
[TextMeshPro スクリプトAPI]: https://docs.unity3d.com/ja/Packages/com.unity.textmeshpro@3.0/api/TMPro.html
