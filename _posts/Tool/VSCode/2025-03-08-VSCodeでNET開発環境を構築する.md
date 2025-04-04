---
title: VSCodeでNET開発環境を構築する
categories: [ Tool, VSCode]
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

#### [C# Dev Kit][拡張機能 C# Dev Kit]

<img src="https://ms-dotnettools.gallerycdn.vsassets.io/extensions/ms-dotnettools/csdevkit/1.17.64/1743017880322/Microsoft.VisualStudio.Services.Icons.Default" alt="C# DevKit icon" width=100>


- [プロジェクト管理](https://code.visualstudio.com/docs/csharp/project-management) : 

#### [C#][拡張機能 C#]

<img src ="https://ms-dotnettools.gallerycdn.vsassets.io/extensions/ms-dotnettools/csharp/2.70.15/1742419226880/Microsoft.VisualStudio.Services.Icons.Default" alt="C# icon" width=100>

`C# Dev Kit`をインストールすると，必須の依存関係として自動的にインストールされる．

- [リファクタリング](https://code.visualstudio.com/docs/csharp/refactoring) : 
- [ナビゲーション](https://code.visualstudio.com/docs/csharp/navigate-edit) :
- インテリセンス:
- フォーマット: 


#### [.NET Core Test Explorer][拡張機能 .NET Core Test Explorer]

<img src="https://formulahendry.gallerycdn.vsassets.io/extensions/formulahendry/dotnet-test-explorer/0.7.8/1663946684868/Microsoft.VisualStudio.Services.Icons.Default" alt=".NET Core Test Explorer icon" width=100>

Unitテスト用の拡張機能．設定からテスト対象プロジェクトのパスを指定する必要がある．

```
**/*Tests.csproj
```

![alt text](assets/img/VSCode/image.png)

---

## ソリューションの作成



```
cd YourProjectName
code .
```

以下のような構成でソリューションとプロジェクトが生成される
```
MySolution/
├── MySolution.sln
└── MyProject/
```




## 公式資料
- [Using .NET in Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet)
- MS Learn: [dotnet コマンド](https://learn.microsoft.com/ja-jp/dotnet/core/tools/dotnet)

## 参考記事
- qiita: [Windows 11 の VSCode の .NET 8 開発環境の構築方法](https://qiita.com/mmake/items/6748ad531ca7bd44a8ce)
- zenn: [VSCodeでC#開発をする方法](https://zenn.dev/midoliy/articles/9e3cff958ff89ba151de)
- zenn: [VSCodeでC#のUnit Testを書けるようにするためのセットアップ](https://zenn.dev/yuriemori/articles/f6a73b326a3f0f)



<!-- Link | VSCode拡張機能 -->
[拡張機能 C# Dev Kit]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit
[拡張機能 C#]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
[拡張機能 .NET Core Test Explorer]: https://marketplace.visualstudio.com/items?itemName=formulahendry.dotnet-test-explorer
[拡張機能]
[拡張機能]
[拡張機能]
[拡張機能]