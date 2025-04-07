---
title: Windows NtCreateFile関数
category: Misc
tags:
  - Windows
  - WinAPI
id: 3c4a7d99-cb3b-4487-bb2c-61ec581f605a
---

C#で`SMBファイル共有`関連のライブラリを利用する際に、`CreateFile()`でファイルハンドルを取得する必要があった．このとき、操作に応じたパラメータ設定が上手くできずに結構ハマってしまったため、改めて調べてみる．

## Win32API

> Microsoft Windows のシステムコール用 API のこと。特に 32 ビットプロセッサで動作する Windows 95 以降や Windows NT で利用できるものは Win32 API と呼ばれる。
> 64 ビットプロセッサ向けの Win64 API も含める場合は「Windows API」という包括的な名称が正確だが、慣習的に Win32 と言えば Win64 も含んでいることがある

- [wiki: Windows API](https://ja.wikipedia.org/wiki/Windows_API)
- [qiita: C# Win32API 完全入門](https://qiita.com/nekotadon/items/f376d17de85dfb84fbd5)
- [qiita: 今更聞けない(かもしれない)Win32API 概要](https://qiita.com/kamikawa_m/items/061dc6d7fbcf95cf7ed0)

C#から呼び出す場合は`P/Invoke`を使用するか、公式の C#ライブラリを用いる．

[nuget: Microsoft.Windows.CsWin32](https://www.nuget.org/packages/Microsoft.Windows.CsWin32)

## CreateFile 関数

- NTCreateFile

##

## 参考資料

- []()
- []()
- []()
