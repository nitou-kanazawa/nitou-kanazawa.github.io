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
- [x] ASP.NET Core利用のための環境設定

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
  columns 6 
    
  %% Sub Framwork
  block: framwork ["Framwork (UI)"] :3
    columns 3
    MVC ["ASP.NET<br>Core<br>MVC"]
    RazorPages ["ASP.NET<br>Core<br>Razor Pages"]
    Blazor
  end
  
  block: service ["Framwork (Service)"] :3
    WebAPI
    SignalR
    gRPC 
  end
  
  %% Common 
  block: lib :6
    columns 5
    r ["ルーティング"]
    m ["モデルバインド"]
    t ["テンプレート<br>エンジン"]
    f ["フィルター"]
    e ["etc."]
  end
  
```





---
## 2. ASP.NET Core MVC の基本

- [x] コントローラの基本
- [ ] ビューの基本
- [ ] モデルの基本 



#### アプリの実行

プロジェクトディレクトリで以下のコマンドを実行すると，アプリを起動することができる．
停止する際は `Ctrl` + `C` でシャットダウンする．

```bash
dotnet watch
```

#### コントローラ

コントローラクラスは以下をいずれかを満たす必要がある．
- `System.AspNet.Mvc.Controller` クラスする．
- クラス名の接尾辞として「Contoller」が付く
- クラスに `Controller` 属性が適用されている．


コントローラにはクライアントからのリクエストを処理するための**アクションメソッド**を定義する．アクションメソッドは以下の特徴がある．
  - アクセス修飾子はpublicにする．
  - 返り値は`IActionResult` を返す． 


基本的に`System.AspNet.Mvc.Controller`クラスのヘルパーメソッドを利用する．
| メソッド | 概要                                 |
| -------- | ------------------------------------ |
| Content  | 指定のテキストを出力                 |
| View     | テンプレートによる結果を出力         |
| File     | 指定のバイト配列をファイルとして出力 |
| Redirect | 指定アドレスにリダイレクト           |
| NotFound | 404 NotFound ステータスを生成        |


###### ルーティング

`program.cs` で最低限の設定を行える．以下のコードでは，`default`という名前で `{controller}/{action}/{id}`のURLパターンを登録している．

```cs
var builder = WebApplication.CreateBuilder(args);
builder.Services.AddControllersWithViews();
var app = builder.Build();
  
  :

// ルーティング
app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

- パラメータの名前・数は自由
- 既定値と省略可能なパラメータ


#### ビュー

`Razor` はHTMLにC#コードを埋め込むための仕組み（ビューエンジン）．`Razor Pages`や`Blazor`デモ共通して利用される仕組みであり，以下の特徴を持つ

```cs

```

- C#の標準的な構文で，条件分岐・ループなどを表現できる．
- ビュー共通の機能，テンプレートを再利用するための仕組みを備える．
- タグヘルパー（ビュー生成のための仕組み）を利用することで，フォーム・リンクなどをよりシンプルに開発できる．



###### Razorテンプレート

Razorを利用する場合のコントローラアクションとRazorテンプレートの役割
  - アクション側 : 表示に必要な値を**ビュー変数**に設定する．
  - テンプレート側 : データを埋め込む場所や表示方法などを指定する． 

```cs
public class HelloController : Controller{
  
  public IActionResult Show(){
    ViewBag.Message = "こんにちは，世界！";   // (1) ビュー変数の準備
    return View();                            // (2) Razorテンプレートの呼び出し
  } 
}
```

`ViewBag`はdynamic型で定義されており，**ビュー変数**は`ViewBag`のプロパティとして設定できる．また，ディクショナリの`ViewData`で設定することも可能．

```cs
ViewBag.変数名 = 値;
```
```cs
ViewData["変数名"] = 値;    // こちらは文字キーなので，変数名に"-"を含めることもできる
```


テンプレート側では以下のようにビュー変数を参照する． 値の取得には`@...`，処理の実行には `@{}` を使用する． 

```cshtml
@{
    ViewData["Title"] = "Show";
}
<p>@ViewBag.Message</p>     @* ビュー変数を表示 *@
```


#### モデル




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

## その他

#### VSCode

VSCodeの拡張機能 `ASP.NET Core Snippets` を導入していれば，`mvc-...`でスニペットを利用できる．

主なスニペット
| キーワード             | 概要                                 |
| ---------------------- | ------------------------------------ |
| HomeController         | コントローラクラス                   |
| mvc-core-xxxxx         | CRUDアクション (get,post,put,delete) |
| mvc-core-async-action  | 非同期アクション                     |
| mvc-core-xxxx-async    | CRUDアクション (非同期)              |
| app-map                | ルーティング                         |
| dbContext-UseSqlServer | SQL Server利用の宣言                 |
| appsettings            | アプリ設定                           |





---



<!-- Link -->
[ASP.NET ドキュメント]: https://learn.microsoft.com/ja-jp/aspnet/core/?view=aspnetcore-9.0
