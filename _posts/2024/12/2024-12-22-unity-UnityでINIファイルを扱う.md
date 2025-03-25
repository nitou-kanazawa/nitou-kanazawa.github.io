---
title: C#でINIファイルを扱う
category: C#
tags:
  - C#
  - INI
  - OSS
---

Unityで`INI`ファイルを取り扱う場合，主に以下の方法が考えられる．

1. 独自実装する．
2. Windows APIで操作する．
3. 外部ライブラリを利用する．

`INI`ファイルは１行に1要素が記述される形式で，独自実装も比較的容易であるが車輪の再発名は避けたい．また，Unityで使用する上でWindowsに依存するのもまずいので必然的に


## INIライブラリ

C#で使えるINIファイル用ライブラリを以下に示す．



## まとめ

最近のアプリ開発で`INI`ファイルを扱うことはほとんどないですが，レガシーなプロジェクトではまだまだ扱う機会があると思う．その時に，どういった選択肢があるかは把握しておきたい．


## 参考資料
- PG日誌: [【C#】INIファイルを読み書きする(DllImportなし)](https://takap-tech.com/entry/2022/04/22/230043)
- _: [Windows APIを使わずにiniファイルを読む方法](https://coneta.jp/article/95698e40-ab92-4a31-bb1d-6eb73955dbf9/)
- ざこノート: [[C#] iniファイルを読み込む方法たち](https://note.dokeep.jp/post/csharp-inifile-read/)

<!-- リンク | repository -->