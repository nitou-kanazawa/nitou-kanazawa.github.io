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

`.vsconfig` ファイルは，Visual Studio の[ワークロードや個別コンポーネント][VisualStudioのワークロードIDとコンポーネントID]のインストール設定を記述したJSON形式の構成ファイル．
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



---


<!-- Link -->
[VisualStudioのワークロードIDとコンポーネントID]: https://learn.microsoft.com/ja-jp/visualstudio/install/workload-and-component-ids?view=vs-2022