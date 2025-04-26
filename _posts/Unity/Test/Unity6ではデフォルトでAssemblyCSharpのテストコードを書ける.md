---
title: Unity6ではデフォルトでAssemblyCSharpのテストコードを書ける
categories: [Unity]
tags:
  - Unity
  - TestRunner
  - NUnit
  - AssemblyDefinition
---


## テストの作成手順

`Test Runner`でテストを行う場合，一般的に以下のような作業手順だとなる

1. `Assembly Definition File(.asmdef)`が配置された**テストディレクトリ**を作成
2. **テストスクリプト**を作成
3. `TestRunner`のエディタウインドウから該当テストを実行 

`1`，`2`のディレクトリやスクリプトのファイル作成自体はコンテキストメニューから行えるので，特に手間がかかる作業はない．

#### 問題点
上記のようにテストスクリプトは`.asmdef`に入れる必要があり，参照にテスト対象のコードが含まれるアセンブリを指定することになる．


## 


## 

## 参考資料
- qiita: [【令和最新版】実はUnityの単体テストは割と手軽に書ける【2024年版】](https://qiita.com/SAM_tak/items/9ae59824f02383958216)
- qiita: [UnityでTest書こうとしたけど、簡単に書かせてもらえなかった話](https://qiita.com/nir_takemi/items/bca2094431afe882394f)