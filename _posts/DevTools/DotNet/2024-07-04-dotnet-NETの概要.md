---
title: .NETの概要
categories: [C#]
tags:
  - C#
  - .NET
  - CLR
---


## .NETの内部構造

<img src ="/assets/img/CSharp/NETの構成.png" alt = ".NETの構造" width =500>


#### 共通ランタイム

共通ランタイム（`CLR`）は，.NETアプリが共通で利用する実行エンジン．.NETをはじめ，Visual Basic，F#といった言語を利用できるが，すべて`CLR`上で動作する．
.NET以前には言語ごとに異なる実行エンジンをもっていた．そのため，使用する言語によってパフォーマンスが異なるといったことも起こりえた．一方，`CLR`ではどの言語でも，コンパイルされた結果は共通中間言語に変換される．これによって，開発者がどのいずれの言語を選択しても，同様の結果とパフォーマンスを得られる．


## 参考資料



<!-- リンク -->


[.NET クラスライブラリの概要 MSLearn]: https://learn.microsoft.com/ja-jp/dotnet/standard/class-library-overview?WT.mc_id=dotnet-35129-website