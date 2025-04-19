---
title: .NET CLI でタブ補間を有効化する
categories: [ .NET ]
tags:
  - .NET
  - CLI
---





[プロファイルを作成方法](https://learn.microsoft.com/ja-jp/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.5#how-to-create-a-profile)
[プロファイルと実行ポリシー](https://learn.microsoft.com/ja-jp/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.5#profiles-and-execution-policy)

1. PowerShell プロファイルの場所を確認する

```bash
echo $PROFILE
```

プロファイルが存在しない場合は作成する

```bash

```

2. プロファイルを編集エディタで開く

```bash
notepad $PROFILE
```

```bash
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition "$commandAst" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
```



## 参考資料
- MS Learn: [.NET CLI のタブ補完を有効にする方法](https://learn.microsoft.com/ja-jp/dotnet/core/tools/enable-tab-autocomplete)
- qiita: [.NET CLI でタブ補完をする](https://qiita.com/Lemon73/items/39cf1c683bcbcd952afe)
- qiita: [コマンドラインから.Netアプリを発行する](https://qiita.com/i-tanaka730/items/d46fdfb5c2f601e512c2)
- qiita: [自作の.NET製CLIツールにタブ補完機能を付ける(PowerShell編)](https://qiita.com/pierusan2010/items/0885a78d5616601d013a)
