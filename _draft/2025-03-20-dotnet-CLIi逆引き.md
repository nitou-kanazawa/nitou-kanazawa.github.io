---
title: .NET CLI 逆引き
date: 2025-03-08
categories:
  - Tool
tags:
  - .NET
  - CLI
mermaid: false
---

`.NET CLI` は、C# や .NET アプリケーションをコマンドラインから操作できる強力なツール．
本記事では、用途別にコマンドを逆引き形式でまとめる．


---
### ソリューション関連

| 操作内容                               | コマンド例                                         |
| -------------------------------------- | -------------------------------------------------- |
| ソリューションを作成する               | `dotnet new sln -n MySolution`                     |
| プロジェクトをソリューションに追加する | `dotnet sln MySolution.sln add MyApp/MyApp.csproj` |


---
### プロジェクト作成

テンプレートからプロジェクトを作成する．

| 種別                       | コマンド例                             |
| -------------------------- | -------------------------------------- |
| コンソールアプリ           | `dotnet new console -n MyApp`          |
| クラスライブラリ           | `dotnet new classlib -n MyLib`         |
| Web API                    | `dotnet new webapi -n MyApi`           |
| MVC アプリケーション       | `dotnet new mvc -n MyMvcApp`           |
| Blazor WebAssembly         | `dotnet new blazorwasm -n MyBlazorApp` |
| テストプロジェクト (xUnit) | `dotnet new xunit -n MyTests`          |


---
### プロジェクトの参照・依存関係

| 操作内容                     | コマンド例                                         |
| ---------------------------- | -------------------------------------------------- |
| プロジェクトに参照を追加する | `dotnet add MyApp reference ../MyLib/MyLib.csproj` |
| NuGet パッケージを追加する   | `dotnet add package Newtonsoft.Json`               |





---
## 参考資料

- Microsoft Docs: [.NET CLI Documentation](https://learn.microsoft.com/ja-jp/dotnet/core/tools/)
- zenn: [dotnet CLI の使い方まとめ](https://zenn.dev/)

