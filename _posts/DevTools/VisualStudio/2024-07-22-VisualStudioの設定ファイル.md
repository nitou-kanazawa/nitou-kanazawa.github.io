---
title: Visual Studio の設定ファイル
categories: [ Tool, VisualStudio ]
tags:
  - VisualStuio
  - VSCode
---

Visual Studio の設定ファイル

- `.vsconfig` : インストール構成 
- `.editorconfig` : エディタ設定


---

## vsconfigファイル

`.vsconfig` ファイルは，Visual Studio の[ワークロードや個別コンポーネント][VisualStudioのワークロードIDとコンポーネントID]のインストール設定を記述した構成ファイル．

特徴
- **JSON形式**
- チームメンバで同じ開発環境を再現できる．
- CI/CDなどでも**必要なコンポーネントだけ**を指定して環境を整えられる．
- プロジェクトルートに配置しておくと，VS起動時にインストールを促してくれる．


ソリューションのルートに配置する．

```
MySolution/
├── MySolution.sln
├── .vsconfig    ← ここに置く！
└── MyProject/
```

#### .vsconfig の例

```json
{
  "version": "1.0",
  "components": [
    "Microsoft.VisualStudio.Workload.ManagedDesktop",   // .NETデスクトップ開発
    "Microsoft.VisualStudio.Workload.NetWeb",           // ASP.NETとWeb開発
    "Microsoft.NetCore.Component.SDK",                  // .NET Core SDK
    "Microsoft.VisualStudio.Component.VC.Tools.x86.x64" // C++のビルドツール
  ]
}
```

各 components の要素は、Visual Studioの内部的なコンポーネントIDを示している．

#### インポート・エクスポート

`.vsconfig` は `Visual Studio Installer` のGUIからインポート・エクスポートを行える．


#### 参考資料
- [インストール構成をインポートまたはエクスポートする](https://learn.microsoft.com/ja-jp/visualstudio/install/import-export-installation-configurations?view=vs-2022)
- [ヒントとテクニック: .vsconfig を使用して Visual Studio を構成する方法](https://learn.microsoft.com/ja-jp/shows/visual-studio-2022-launch-event/tips-and-tricks-how-to-configure-visual-studio-with-dotvsconfig)
- hatena: [Visual Studioの設定の移行 : インストール構成, Visual Studioの設定](https://shuhelohelo.hatenablog.com/entry/2020/07/17/140631)

---

## editorconfig

`.editorconfig` はコードエディタ間でファイルのフォーマットを一貫させるための設定ファイル．

特徴
- **INIファイル形式**
- C#, JavaScript, HTML, CSS など複数言語に対応
- Git 管理できるのでチーム開発にも有用
- Visual Studio / VSCode / Rider など主要IDEが対応
- `.editorconfig` によって手動整形や自動整形 (Ctrl+K Ctrl+D) の動作が統一される


#### .editorconfig の例

```ini
root = true

[*.cs]
indent_style = space
indent_size = 4
insert_final_newline = true

# 中括弧は改行しない
csharp_new_line_before_open_brace = none

# var 使用スタイル
csharp_style_var_elsewhere = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_for_built_in_types = true:suggestion

# using の並び順
dotnet_sort_system_directives_first = true

# 命名規則
dotnet_naming_rule.private_fields_should_be_camel_case.severity = suggestion
```

#### 使用できるプロパティ

| プロパティ                 | 説明                                                                                                                                                             |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `indent_style`             | ハードタブまたはソフトタブを使用するために `tab` または `space` を設定する                                                                                       |
| `indent_size`              | 各インデントレベルに使用される列数とソフトタブの幅を定義する整数．`tab` に設定すると、`tab_width`（指定されている場合）の値が使用される．                        |
| `tab_width`                | タブ文字を表すために使用される列数を定義する整数．これはデフォルトで `indent_size` の値となり、通常は指定する必要はない．                                        |
| `end_of_line`              | 改行の表現方法を制御するために `lf`、`cr`、または `crlf` を設定する                                                                                              |
| `charset`                  | 文字セットを制御するために `latin1`、`utf-8`、`utf-8-bom`、`utf-16be`、または `utf-16le` を設定する．                                                            |
| `trim_trailing_whitespace` | 改行文字の前にある空白文字を削除するために `true` を設定し、削除しないようにするために `false` を設定する．                                                      |
| `insert_final_newline`     | ファイルを保存する際に末尾に改行を追加するために `true` を設定し、追加しないようにするために `false` を設定する．                                                |
| `root`                     | 特別なプロパティ．ファイルの最上部にセクション外で指定する必要がある．親ディレクトリの `.editorconfig` ファイルの検索を停止するために `root = true` を設定する． |


#### 公式プロジェクトでの利用例

[使用例](https://github-com.translate.goog/editorconfig/editorconfig/wiki/Projects-Using-EditorConfig?_x_tr_sl=auto&_x_tr_tl=ja&_x_tr_hl=ja)

---

#### 参考資料
- 公式サイト [EditorConfig](https://editorconfig.org/)
- MS Learn: [コード スタイル ルールのオプション](https://learn.microsoft.com/ja-jp/dotnet/fundamentals/code-analysis/code-style-rule-options)
- zenn: [今さら聞けないEditorConfig](https://zenn.dev/sashimi/articles/7f2c6f29e8a065)
- qiita: [EditorConfig公式サイトの解説を日本語に訳しました](https://qiita.com/yama-github/items/f4af3b3a0c00306bbb17)



<!-- Link -->
[VisualStudioのワークロードIDとコンポーネントID]: https://learn.microsoft.com/ja-jp/visualstudio/install/workload-and-component-ids?view=vs-2022
