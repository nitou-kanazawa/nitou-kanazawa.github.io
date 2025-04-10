---
title: PowerShellプロファイルとは
categories: [ Misc ]
tags:
  - PowerShell
  - CLI
---


## プロファイルとは

プロファイルはPowerShellを起動したときに自動で読み込まれるスクリプトのこと．

> PowerShell プロファイルを作成して、環境をカスタマイズし、開始するすべての PowerShell セッションにセッション固有の要素を追加できます。 PowerShell プロファイルは、PowerShell の開始時に実行されるスクリプトです。 プロファイルをログオン スクリプトとして使用して、環境をカスタマイズできます。 コマンド、エイリアス、関数、変数、スナップイン、モジュール、PowerShell ドライブを追加できます。 また、プロファイルに他のセッション固有の要素を追加して、インポートまたは再作成することなく、すべてのセッションで使用することもできます。
> 
> Microsoft Docs: [about Profiles][about_Profiles MS Learn] 


#### $PROFILE 変数

`$PROFILE`自動変数には，現在のセッションで使用できるPowerShellプロファイルのパスが格納されている．（プロファイルが存在しない場合でも，`$PROFILE`にはいずれかの値が入っている）

```powershell
echo $PROFILE
```
```
C:\Users\<ユーザー名>\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```



## プロファイルの作成



プロファイルファイルは，手動で作成しないと存在しないことが多いので，以下のコマンドで存在チェックをして作成する．作成後は`. $PROFILE`で再度読み込む．

```powershell
if (!(Test-Path -Path $PROFILE)) { New-Item -Type File -Path $PROFILE -Force }
```


#### スクリプト実行の権限

PowerShell では、セキュリティの観点から既定で「スクリプトは実行禁止」になっている．プロファイルも`.ps1`のスクリプト扱いになるため，次のエラーが発生する可能性がある．

```
このシステムではスクリプトの実行が無効になっているため、ファイル {YourFilePass} を読み込むことができません。
```

この場合は，`Set-ExecutionPolicy`で実行権限を付与する．

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned -Force
```
- `-Scope CurrentUser` : ログイン中のユーザーにのみ適用

現在の設定は`Get-ExecutionPolicy`で確認できる．

```powershell
Get-ExecutionPolicy -List
```

```
        Scope ExecutionPolicy
        ----- ----------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       Undefined
```

## 参考資料
- _: [PowerShellのプロファイルをカスタマイズしてCLIの操作を快適にする](https://sheepla.github.io/sheepla-note/posts/powershell-customization/)
- zenn: [私のPowerShellプロファイルを紹介する](https://zenn.dev/yuta28/articles/powershell-profile)

[about_Profiles MS Learn]: https://learn.microsoft.com/ja-jp/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.5#how-to-create-a-profile