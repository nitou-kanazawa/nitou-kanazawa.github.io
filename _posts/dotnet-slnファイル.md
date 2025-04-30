---
title: ソリューションファイル(.sln)
categories: 
  - .NET
tags:
  - .NET
  - C#
---


`.sln`（ソリューションファイル）は，Visual Studio や `dotnet` CLI で使用される、プロジェクトの構成情報をまとめたファイル．複数の `.csproj`（C#プロジェクト）などを１つにまとめ，依存関係やビルドの順序を管理するためのもの．

---
## 基本構成

ソリューションファイルには、以下のような情報が含まれています：

- 含まれているプロジェクトのパスとGUID
- 各プロジェクトの依存関係
- ソリューションの構成（Debug/Release など）
- ソリューションフォルダ（仮想的なフォルダ構造）

Visual Studio でプロジェクトを作成すると、自動的に `.sln` ファイルも生成されが，CLIベースの操作でも管理可能．


```sln
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 17
VisualStudioVersion = 17.0.31903.59
MinimumVisualStudioVersion = 10.0.40219.1
Global
	GlobalSection(SolutionConfigurationPlatforms) = preSolution
		Debug|Any CPU = Debug|Any CPU
		Release|Any CPU = Release|Any CPU
	EndGlobalSection
	GlobalSection(SolutionProperties) = preSolution
		HideSolutionNode = FALSE
	EndGlobalSection
EndGlobal
```


---
## CLI 操作まとめ
`.sln` ファイルの作成・編集は、`dotnet sln` コマンドで可能．

```cmd
# ソリューション作成
dotnet new sln -n MySolution

# プロジェクト追加
dotnet sln add MyApp/MyApp.csproj

# プロジェクト削除
dotnet sln remove MyApp/MyApp.csproj

# プロジェクト一覧表示
dotnet sln list

# ソリューションをビルド
dotnet build MySolution.sln
```


---
## 関連資料

`.sln`ファイルの形式は複雑で，手作業で編集されることは想定されていない．また，現在ではGUIDや構成情報などを保持している必要もないことから，XMLベースの新しいファイル形式`slnx`が登場した．
今後はこちらが主流になっていくらしい．


---
## 参考記事
- zenn: [.NETの新たなソリューションファイル形式(.slnx)](https://zenn.dev/nuskey/articles/e07f70b62105d5)


<!-- Link -->
[ソリューションの概要]: https://learn.microsoft.com/ja-jp/visualstudio/extensibility/internals/solutions-overview?view=vs-2022
[ソリューションファイル]: https://learn.microsoft.com/ja-jp/visualstudio/extensibility/internals/solution-dot-sln-file?view=vs-2022
