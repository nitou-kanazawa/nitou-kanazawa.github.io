---
title: UnityでPlayFabを利用する
categories: [Unity]
tags:
  - Unity
  - PlayFab
---

[`PlayFab`](https://azure.microsoft.com/ja-jp/products/playfab)は，ゲーム開発に特化された`BasS (Backend as a Service)`の1つ．


## PlayFabの機能

`PlayFab`は様々な機能を備えており，ドキュメントには`Multiplayer Services`，`LiveOps Services`，`Data & Analytices`のカテゴリに分けて以下のように示されている．

- Multiplayer Services
  - クロスネットワークのIDとデータ
  - マルチプレイヤーサーバー
  - チャット
  - ランキングと統計

- LiveOps Services
  - エンゲージメントとリテンション
  - コンテンツ管理
  - A/Bテスト
  - 収益化
  - 自動化

- Data & Analytics
  - リアルタイム分析
  - データ管理
  - コンプライアンス
  - SDK
  - サポート
  

## PlyaFabを始める

Unityで利用するために，サーバー／クライアント側でそれぞれ以下の対応が必要である．
1. `ゲームマネージャー`でタイトルを作成
2. Unityへ`Unity3d PlayFab SDK` を導入

また，手順は「[クイックスタート: UnityのC#用のPlayFabクライアントライブラリ](https://learn.microsoft.com/ja-jp/gaming/playfab/sdks/unity3d/quickstart)」を参照している．


## 1. ゲームマネージャーでの作業

#### PlayFabアカウント

Microsoftアカウントを使用してサインインする必要がある．

<img src="https://learn.microsoft.com/ja-jp/gaming/playfab/gamemanager/media/quickstart/create-account.png" alt="アカウントの作成" width =400>

> [!CAUTION]
> PlayFab固有アカウントを用いたサインインも可能だが，こちらは2025年4月30日にゲームマネージャーでのサポートが廃止されるため、Microsoftアカウントを利用する必要がある．

#### ゲームタイトルの作成

`PlayFab`には「スタジオ」と「タイトル」という重要な概念がある．
  - タイトル：１つのゲーム
  - スタジオ：複数のゲームが入る箱

<img src="https://learn.microsoft.com/ja-jp/gaming/playfab/gamemanager/media/quickstart/my-studios-titles.png" alt="スタジオとタイトル" width="600">

ゲームマネージャーでUnityアプリに対応するタイトルを作成する必要がある．
タイトル作成時には多くの設定項目が表示されるが，最低限タイトル名を設定すればよい．作成したタイトルの右下に表示されているタイトルIDを後ほど，Unity側で参照することになる．

<img src="https://learn.microsoft.com/ja-jp/gaming/playfab/gamemanager/media/quickstart/create-first-game.png" alt="ゲームの作成" width =400>

#### スタジオとタイトル



## 2. Unityでの作業

#### PlayFab SDK 
`Unity3d PlayFab SDK` には、モデル、メソッド、Web 要求を送受信するための HTTP ラッパー、JSON シリアル化など、PlayFab API にアクセスするために必要なすべてのものが用意されている．

[Unity PlayFab SDK GitHub リポジトリ](https://github.com/PlayFab/UnitySDK)

このSDKはマイクロソフトの`SDKGenerator`によって自動生成されている．最新のAPIを反映するために通常2週間ごとにビルドされている．

#### SDKのインストール

SDKパッケージを[こちらのリンク](https://aka.ms/playfabunitysdkdownload)からダウンロードし，Unity内にインストールする．

<img src="" width=300>

#### タイトル設定

スクリプタブルオブジェクト`PlayFab Shared Settings`に設定値を入力する．アセットはメニューの`PlayFab > MakePlayFabSharedSettings`から新規作成でき，Project Windowの`PlayFab > Shared > Public > Resources`内に作成される．

アセットの`Title Id`にゲームマネージャーで作成したタイトルのIDを入力する．

<img src="https://learn.microsoft.com/ja-jp/gaming/playfab/sdks/unity3d/media/playfab-shared-settings-title-id.png" alt="" width=500>

また，以下のようにスクリプトから設定することもできる．

```cs
PlayFabSettings.staticSettings.TitleId = "@title_id";
```

#### 動作確認

実際に接続ができるか，以下のスクリプトを実行して確認する．

```cs
using PlayFab;
using PlayFab.ClientModels;
using UnityEngine;

public class PlayFabLogin : MonoBehaviour {

    public void Start() {
        var request = new LoginWithCustomIDRequest { 
          CustomId = "GettingStartedGuide", 
          CreateAccount = true
        };
        PlayFabClientAPI.LoginWithCustomID(request, OnLoginSuccess, OnLoginFailure);
    }

    private void OnLoginSuccess(LoginResult result) {
        Debug.Log("Congratulations, you made your first successful API call!");
    }

    private void OnLoginFailure(PlayFabError error) {
        Debug.LogWarning("Something went wrong with your first API call.  :(");
        Debug.LogError("Here's some debug information:");
        Debug.LogError(error.GenerateErrorReport());
    }
}
```

Successのコールバックが実行されれば，PlayFabに正常にログインできている．

>![]
> 上記の`CustomID`を使用するログイン方法はモバイルでは利用できない．モバイルタイトルのログインを実装するには、`LoginWithAndroidDeviceID`，`LoginWithIOSDeviceID`，または`LoginWithFacebook`などのソーシャル ログイン形式のいずれかを使用する必要がある．



## PlayFab API

| 名称              | 用途                                                          |
| ----------------- | ------------------------------------------------------------- |
| PlayFabClient API | クライアント権限で実行するAPI．                               |
| PlayFabServer API | サーバー権限で実行するAPI．一部はクライアントからも実行可能． |
| PlayFabAdmin API  | 管理者権限で実行するAPI．ほぼ使わない．                       |



## 参考資料

- [MS: PlayFabとは？](https://learn.microsoft.com/ja-jp/gaming/playfab/what-is-playfab)
- [MS: UnityのC#用のPlayFabクライアントライブラリ](https://learn.microsoft.com/ja-jp/gaming/playfab/sdks/unity3d/quickstart)
- [zenn: ゲーム開発が10倍ラクになる「PlayFab」の始め方](https://zenn.dev/nekojoker/articles/38f1654ee254f482dfce)