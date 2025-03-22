---
title: TextMeshPro のインスペクタ設定
categories: [ Unity ]
tags:
  - Unity
  - TMPro
---

`TextMeshProUGUI` のインスペクタ設定に関するメモ書き．


## TextMeshPro

```mermaid
classDiagram

  class TMP_Text {

  }

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


![]({{img_root}}/TextMeshPro_インスペクタ01.png)

## 参考資料


<!-- リンク |  -->
[TextMeshPro マニュアル]: https://docs.unity3d.com/ja/Packages/com.unity.textmeshpro@3.0/manual/index.html
[TextMeshPro スクリプトAPI]: https://docs.unity3d.com/ja/Packages/com.unity.textmeshpro@3.0/api/TMPro.html



{% assign img_root = '/assets/img/Unity/TextMeshPro' %}