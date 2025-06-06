---
title: VSCodeでNET開発環境を構築する
date: 2025-03-08
categories:
  - Tool
  - VSCode
tags:
  - VSCode
  - .NET
---

`VS Code`で`.NET`開発環境を整える手順についてのメモ．

--- 

## .NET のインストール手順

#### ダウンロード

[公式ページ](https://dotnet.microsoft.com/ja-jp/download/dotnet)から `.NET` をダウンロードする．

#### インストール


#### 確認

以下のコマンドで正常にインストールできているか確認できる．

```
dotnet --info
```

---

## コマンド

#### ソリューションファイルの作成

[dotnet sln](https://learn.microsoft.com/ja-jp/dotnet/core/tools/dotnet-sln)


フォルダ名と同じ名前の.slnファイルを作成する

```
dotnet new sln  
```

`--name`オプションでファイル名を指定できる．

```
dotnet new sln --name {YourSolutionName}
dotnet new sln -n {YourSolutionName}
```

`--output`でフォルダを作りその中に.slnファイルを作成するともできる．

```
dotnet new sln --output {MySolution}

// 以下と同じ
mkdir MySolution
cd MySolution
dotnet new sln
```

---


## プラグイン導入

---
#### [C#][拡張機能 C#]

<img src ="https://ms-dotnettools.gallerycdn.vsassets.io/extensions/ms-dotnettools/csharp/2.70.15/1742419226880/Microsoft.VisualStudio.Services.Icons.Default" alt="C# icon" width=100>


- [リファクタリング](https://code.visualstudio.com/docs/csharp/refactoring) : 
- [ナビゲーション](https://code.visualstudio.com/docs/csharp/navigate-edit) :
- インテリセンス:
- フォーマット: 


---
#### [C# Dev Kit][拡張機能 C# Dev Kit]

`C# Dev Kit`をインストールすると，必須の依存関係として `C#` も自動的にインストールされる．

<img src="https://ms-dotnettools.gallerycdn.vsassets.io/extensions/ms-dotnettools/csdevkit/1.17.64/1743017880322/Microsoft.VisualStudio.Services.Icons.Default" alt="C# DevKit icon" width=100>


- [プロジェクト管理](https://code.visualstudio.com/docs/csharp/project-management) : 

※Visual Studio と同様のライセンス体系


---
#### [IntelliCode for C# Dev Kit][拡張機能 IntelliCode for C# Dev Kit]

`C# Dev Kit` 用のAIコード補間機能．残念ながら現状は使い物にならないレベル（2025.04）．

<img src="https://ms-dotnettools.gallerycdn.vsassets.io/extensions/ms-dotnettools/vscodeintellicode-csharp/2.2.3/1731477548450/Microsoft.VisualStudio.Services.Icons.Default" alt="IntelliCode for C# Dev Kit icon" width=100>

※Visual Studio と同様のライセンス体系


---
#### [.NET Core Test Explorer][拡張機能 .NET Core Test Explorer]

Unitテスト用の拡張機能．

<img src="https://formulahendry.gallerycdn.vsassets.io/extensions/formulahendry/dotnet-test-explorer/0.7.8/1663946684868/Microsoft.VisualStudio.Services.Icons.Default" alt=".NET Core Test Explorer icon" width=100>

設定からテスト対象プロジェクトのパスを指定する必要がある．例えば`Test Project Path`に以下を設定する．

```
**/*Tests.csproj
```

![alt text](assets/img/VSCode/image.png)


--- 
#### [ASP.NET Core Snippets]

<img src="https://rahulsahay.gallerycdn.vsassets.io/extensions/rahulsahay/csharp-aspnetcore/1.11.0/1559414167977/Microsoft.VisualStudio.Services.Icons.Default" alt=".NET Core Test Explorer icon" width=100>


---
#### [ASP.NET Core Switcher]


<img src="https://adrianwilczynski.gallerycdn.vsassets.io/extensions/adrianwilczynski/asp-net-core-switcher/2.0.2/1577043327534/Microsoft.VisualStudio.Services.Icons.Default" alt="ASP.NET Core Switcher icon" width=100>


--- 
#### C# XML Documentation Comments






---




---


## 公式資料
- [Using .NET in Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet)
- MS Learn: [dotnet コマンド](https://learn.microsoft.com/ja-jp/dotnet/core/tools/dotnet)

## 参考記事
- qiita: [Windows 11 の VSCode の .NET 8 開発環境の構築方法](https://qiita.com/mmake/items/6748ad531ca7bd44a8ce)
- zenn: [VSCodeでC#開発をする方法](https://zenn.dev/midoliy/articles/9e3cff958ff89ba151de)
- zenn: [VSCodeでC#のUnit Testを書けるようにするためのセットアップ](https://zenn.dev/yuriemori/articles/f6a73b326a3f0f)
- qiita: [VSCodeとdotnet-cliでC#のソースコードをテスト出来るようにするまで](https://qiita.com/jnuank/items/e9aeb2d8c99d1e6f1081)



[^C# Dev Kit] : https://forest.watch.impress.co.jp/docs/news/1537627.html

<!-- Link | VSCode拡張機能 -->
[拡張機能 C#]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
[拡張機能 C# Dev Kit]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit
[拡張機能 IntelliCode for C# Dev Kit]: https://marketplace.visualstudio.com/items/?itemName=ms-dotnettools.vscodeintellicode-csharp
[拡張機能 .NET Core Test Explorer]: https://marketplace.visualstudio.com/items?itemName=formulahendry.dotnet-test-explorer
[拡張機能]
[拡張機能]
[拡張機能]
