---
title: .NET CLI 逆引き
categories: [ .NET ]
tags:
  - .NET
  - CLI
---


--- 
## 1. 基本情報の確認

| コマンド                                 | 目的                           |
| ---------------------------------------- | ------------------------------ |
| `dotnet --version` / `--info`            | SDK・ランタイムの詳細を表示    |
| `dotnet --list-sdks` / `--list-runtimes` | インストール済みバージョン一覧 |



--- 
## 2. プロジェクト & ソリューション操作

| コマンド                | 目的                 |
| ----------------------- | -------------------- |
| `dotnet new <Template>` | Templateから新規生成 |

---
#### ソリューションを作成する
`.sln`(ソリューション)ファイルを新規作成する：

```bash
dotnet new sln -n {MySolution}
```

- `MySolution.sln` が作成される
- １つ以上の `.csproj` を管理するためのファイル

---

#### プロジェクトを作成する

[`dotnet new <TEMPLATE>`][dotnet new]はテンプレートからプロジェクトを作成できるコマンド：

```bash
dotnet new console -n {MyConsoleApp}
dotnet new classlib -n {MyLib}
```

- ディレクトリ `MyConsoleApp` と `MyLib` が作成され、その中に `.csproj` を含む構成となる

- 主なテンプレート
  - sln
  - console
  - blazor
  - classlib
  - nunit
  - gitignore
  
詳細は[こちら](https://learn.microsoft.com/ja-jp/dotnet/core/tools/dotnet-new#arguments)を確認．

---

#### プロジェクトをソリューションに追加する

`dotnet sln add` でプロジェクトを追加できる：

```bash
dotnet sln MySolution add MyConsoleApp/MyConsoleApp.csproj
dotnet sln MyLib add MyLib/MyLib.csproj
```

---

#### プロジェクトの参照を追加する

`dotnet add` でプロジェクトに対して参照を追加できる．

```bash
dotnet add MyConsoleApp/MyConsoleApp.csproj reference MyLib/MyLib.csproj
```

---

#### 動作確認

```bash
dotnet run --project MyConsoleApp
```

- `--project`の省略形`-p`は推奨されてない


## テスト


--- 
## 参考資料
