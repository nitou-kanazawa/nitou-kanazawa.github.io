---
title: 書籍 「独習 ASP.NET Core」
categories: [ 学習記録, 書籍 ]
tags:
  - Web
  - ASP.NET
  - C#
mermaid: true
---



---
## 1. イントロダクション

- [x] ASP.NET Coreの全体像
- [ ] ASP.NET Core利用のための環境設定

#### ASP.NET Core とは

`ASP.NET Core` は `.NET` 環境で動作する**サーバーサイド**のアプリケーションフレームワーク．

```mermaid
flowchart LR
    %% -------------------------------
    subgraph Client Side
        C["Browser / Front‑End"]
    end

    subgraph Server Side
        S["Web App<br/>(ASP.NET&nbsp;Core)<br/><br/><small>② 動的にページ生成</small>"]
    end
    %% -------------------------------

    C -- "① ページを要求" --> S
    S -- "③ 処理結果を応答" --> C
```


###### .NET の構造

```mermaid
block-beta
    %% 2 列レイアウト：左＝主要レイヤー群／右＝ツール列
    columns 2

    %% ─────────── .NET ───────────
    block:dotnet[".NET"]:2
        %% .NET 内も 2 列に分割
        columns 2

        %% ----- 左列：主要 3 レイヤー（高→低の順に縦並び） -----
        block:layers:1
            columns 1
            fw["フレームワーク"]
            bcl["基本クラスライブラリ<br/>(BCL)"]
            foundation["基盤技術<br/>(CLR・GC・JIT)"]
        end

        %% ----- 右列：ツールを縦に並べる -----
        block:tools["ツール"]:1
            columns 1
            cli["dotnet CLI / SDK"]
            ide["Visual Studio / VS Code"]
            nuget["NuGet Manager"]
        end
    end

    %% ─────────── OS／プラットフォーム（最下段） ───────────
    os["OS / Platform<br/>(Windows · Linux · macOS)"]:2
```

- **CLR** (共通言語ランタイム) : `.NET`アプリが共通で利用する実行エンジン．言語やプラットフォームの差異を吸収しくくれる．
- **基本ライブラリ** : .NET言語から共通して呼び出せるライブラリ．
- **フレームワーク** : 


###### .NET ASP Core の全体像

```mermaid
block-beta
```






---
## 2. ASP.NET Core MVC の基本

- [ ] コントローラの基本
- [ ] ビューの基本
- [ ] モデルの基本 

---
## 3. Scaffolding機能

- [ ] Scaffolding機能の実行



--- 
## 4. ビュー開発

- [ ] Razorの基本構文

--- 
## 5. モデル開発

- [ ] エンティティの定義
- [ ] LINQ to Entities
- [ ] CRUD

--- 
## 6. コントローラ開発 

- [ ] モデルバインド

--- 
## 7. ASP.NET Coreアプリの構造

- [ ] 依存性注入


--- 
## 8. ミドルウェア

- [ ] ルーティング
- [ ] 状態管理
- [ ] エラーページ
- [ ] 静的リソース



--- 
## 9. ASP.NET Core の主なサブフレームワーク

- [ ] Razor Pages
- [ ] ASP.NET Core Web API
- [ ] SPAプロジェクト





---



<!-- Link -->
[ASP.NET ドキュメント]: https://learn.microsoft.com/ja-jp/aspnet/core/?view=aspnetcore-9.0
