---
title: SwiftUIの基本知識
category: Swift
tags:
  - Swift
  - SwiftUI
id: 5da6af1e7e25e8629d62
---

## 概要


## キーワード

おそらくC#の属性やJavaのアノテーションのようなもの．

#### main


#### state

プロパティラッパー
データバインディング

## Viewクラス

#### モディファイヤ


## extensionでbody内を整理する

```swift
struct CardView : View{
  var body : some View {
     ZStack{
      imageLayer
      informationLayer
     }
  }
}

extension CardView {
  // Image
  private var imageLayer : some View{
    Image("avatar")
      .fram(width: 100, height: 100)
  }

  private var informationLayer : some View{
    HStack{
      ...
    }
  }
}

```

## SF symbols




## 参考資料

- [Apple: ](https://developer.apple.com/videos/play/wwdc2019/226)
- [github: mixigroup/ios-swiftui-training](https://github.com/mixigroup/ios-swiftui-training/blob/session-3.1/README.md)


## その他

- [_: アニメーションAPIのすべて by 岸川克己](https://fortee.jp/iosdc-japan-2022/proposal/517cb156-3905-4dd7-b666-d2200049d822)