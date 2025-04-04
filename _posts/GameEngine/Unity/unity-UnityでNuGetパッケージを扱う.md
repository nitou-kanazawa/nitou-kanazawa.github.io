---
title: UnityでNuGetパッケージを扱う
categories: [Unity]
tags:
  - Unity
  - NuGet
  - OSS
---


## 概要

Unityでは標準で[`NuGet`][NuGet]パッケージを導入する方法が用意されていない．手動であれば，`.NET Standard2.0`/`2.1`に対応したパッケージをダウンロードして（拡張子を`.nuget`から`.dll`に変更しておく）Assetsフォルダに追加すれば，プラグインとして取り込むことができる．しかし，依存関係の解決やバージョン管理，作業コストなどの面から，パッケージ管理を手動で行うのは現実的ではない．

そのため，以下のようなNuGetパッケージ導入をサポートするライブラリが公開されている．

- [NuGetForUnity][NuGetForUnity リポジトリ]
- [UnityNuGet][UnityNuGet リポジトリ]


## NuGetForUnity

PackageManagerからGitリポジトリ経由でインストールする．

``` 
https://github.com/GlitchEnzo/NuGetForUnity.git?path=/src/NuGetForUnity
```

`NuGetForUnity`を導入するとツールバーに`NuGet`の項目が追加される．



追加した`NuGet`パッケージは`Assets/Pach`

```
// デフォルトの場合
/Assets/Packages*

// Placement = "Packages folder" の場合
/Packages/nuget-packages/InstalledPackages*
```



## UnityNuGet
`UnityNuGet`は，Unityで利用可能なNuGetパッケージをUPMパッケージとしてラップした状態で提供してくれるUPMパッケージレジストリ．

インストールできるパッケージは，[リポジトリ内のJSONファイル](https://github.com/bdovaz/UnityNuGet/blob/master/registry.json)に列挙されている．


## 参考資料

- zenn: [UPM経由でNuGetパッケージを扱えるUnityNuGetについて](https://zenn.dev/drumath2237/articles/01a760cac9f4bc)
- hatena: [UnityNuGetとNuGetForUnity](https://www.nowsprinting.com/entry/2023/12/21/024620)


<!-- リンク | リポジトリ -->
[NuGetForUnity リポジトリ]: https://github.com/GlitchEnzo/NuGetForUnity
[UnityNuGet リポジトリ]: https://github.com/bdovaz/UnityNuGet

[NuGet]: https://www.nuget.org/