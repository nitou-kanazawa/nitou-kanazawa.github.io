---
title: タイピングゲーム関連のメモ
categories: [Unity]
tags:
  - Unity
---

## 概要

タイピングゲーム開発に関するメモ書き．

AssetStoreでタイピングゲームに使えるアセットを探していたところ[「Typing Game in Japanese」][AssetStoreリンク]というアセットを見つけた．UnityRoomでよく上位に表示されているタイピングゲームの作者の方がつくられたアセットらしく，内容もシンプルで扱い易そうだったため試してみることにした．

<!-- more -->

また，[こちらの記事][記事リンク]で簡単に紹介もされている．

## 

#### ディレクトリ構成

```
├─Core
│      RomajiData.cs
│      TypingEngine.cs
└─Utils
        AudioManager.cs
        OneShotEffect.cs
```


#### シーケンス

- 文章(日本語，ひらがな，ローマ字)を表示する
- キーボード入力を受け付けて正誤判定を行う
  - 複数の入力パターン対応

#### 入力




## 参考に

#### リポジトリ

- [WhiteFox-Lugh/RomanTypeParser](https://github.com/WhiteFox-Lugh/RomanTypeParser)
  - オートマトンで
  - Jsonで仮名・ローマ字の対応テーブルを定義

#### アセット
- [Typing Game in Japanese](https://assetstore.unity.com/packages/templates/systems/typing-game-in-japanese-258301)
  - 簡単な演出込み
  - メイン処理は2ファイルのシンプルな実装

#### 記事

- [hatena:Unityで作るローマ字入力とかな入力に両対応した多機能なタイピングゲームの制作講座 1回目](https://happynetwork2019.hatenablog.com/entry/2024/04/18/153132)
  - ローマ字と仮名入力の両方に対応
  - 

## 参考資料 
- [wiki: ローマ字入力](https://ja.wikipedia.org/wiki/%E3%83%AD%E3%83%BC%E3%83%9E%E5%AD%97%E5%85%A5%E5%8A%9B)



<!-- リンク -->
[AssetStoreリンク]: https://assetstore.unity.com/packages/templates/systems/typing-game-in-japanese-258301
[記事リンク]: https://eiki.hatenablog.jp/entry/2023/08/14/203318 