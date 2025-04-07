---
title: XCodeの基本知識
category: XCode
tags:
  - XCode
id: 3b1f586d-f813-4f8e-aa89-242467580d95
---

XCodeを使用する上での基本知識やTipsをメモしておく．

****
## ショートカット

#### ファイル操作
- `Command` + `Option` + `n` 新規フォルダ
- `Command` + `n` 新規ファイル


####
- `Command` + `B` ビルド

#### 

- `Command` + `a` 全選択

- `Command` + `/` 選択行のコメントアウト
- `Command` + `Delete` 選択行の削除

- `Cntrol` + `i` インデント整形

**コードの折り畳み**
- `Command` + `Option` + `←` 選択セクションの折り畳み
- `Command` + `Option` + `←` 選択セクションの展開
- `Command` + `Shift` + `Option` + `←` 全セクションの折り畳み
- `Command` + `Shift` + `Option` + `→` 全セクションの展開

**選択位置の移動**
- `Command` + `Option` + `[` コード1行移動（上）
- `Command` + `Option` + `[` コード1行移動（下）


#### 表示切り替え
**ウインドウ**
- `Command` + `0` サイドバー(左)
- `Command` + `Option` + `0` サイドバー(右) 
- `Command` + `Shift` + `y` コンソール
**プレビュー**
- `Command` + `Enter` 非表示
- `Command` + `Option` + `Enter` 表示


****
## アノテーションコメント
XCodeがタグとして認識するコメント．

`MARK`コメントを使用すると，コード内にセクションを定義することができる．セクションはXCodeのナビゲータから確認できる．
`MARK`，`TODO`，`FIXME`が使用できる．XCode11以降はエディタ右側のミニマップにも反映される．

```swift
// MARK: 見出しのみ
// TODO: 
// FIXME:
```

`-`を付与するとセクションに区切り線を表示できる．
```swift
// MARK: - 区切り線の下に見出し
// MARK: 区切り線の上に見出し -
```

## 参考資料

- [_: Xcodeのちょっとしたテクニックや裏技、設定を33個紹介！](https://ios-docs.dev/xcode-technic/)
- [_: コードコメントの書き方｜ショートカットの利用、Markを活用したコメントアウト](https://blog.code-candy.com/xcode_comment_improvement/)
- []()

