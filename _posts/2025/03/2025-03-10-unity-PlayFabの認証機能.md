---
title: PlayFabの認証機能
categories: [Unity]
tags:
  - Unity
  - PlayFab
---

`PlayFab`でのユーザ認証には「匿名ログイン」と「復旧可能ログイン」の2種類がある．


## プレイヤーのログイン

#### 匿名ログイン
匿名ログインは、プレイヤーがアカウント登録をせずにゲームをプレイできる方法．一時的なセッションを提供し、ユーザーが継続的にデータを保持できるようにする．ただし、デバイス変更時にデータが失われる可能性がある．

- [`LoginWithIOSDeviceID`][LoginWithIOSDeviceID]
- [`LoginWithAndroidDeviceID`][LoginWithAndroidDeviceID]
- [`LoginWithCustomID`][LoginWithCustomID]

これらはデバイスを一意に識別することができるが、匿名であるためプレイヤーに関して回復可能な情報はない．よって，プレイヤーがデバイスを紛失または破壊した場合、アカウントは失われることになる．

> Tips
> これらの方法はプレイヤーに何の操作も要求しないため，障壁が低いというメリットがある．実際，プレイヤーによっては，メールアドレスやID情報を尋ねると，ゲームを断念することがある．したがって，最初は匿名ログインで開始して，ログイン完了後に回復可能なログイン資格情報を追加できる仕組みが好ましい．

#### 復旧可能なログイン
プレイヤーが異なるデバイス間でデータを引き継ぐために使用するログイン方法．

**純粋なPlayFabオプション**
最も簡単なオプションには、以下がある．

- [`LoginWithPlayFab`][LoginWithPlayFab]
- [`LoginWithEmailAddress`][LoginWithEmailAddress]

**サードパーティのAPIオプション**
以下は、他のサービスへの個別の API 呼び出しが必要だが，追加の SDK をインストールする必要はない．

- [`LoginWithKongregate`][LoginWithKongregate]
- [`LoginWithSteam`][LoginWithSteam]
- [`LoginWithTwitch`][LoginWithTwitch]
- [`LoginWithGameCenter`][LoginWithGameCenter] (iOSのみ．セキュリティで保護された認証が必要な場合)

**サードパーティのSDKオプション**
これらは，個別のSDKがゲームにインストールされている必要がある． セキュリティで保護された認証は，サードパーティーの SDK 内で行われる．

- `LoginwithFacebook`
- `LoginWithGoogleAccount`


## ログイン

以上のことから，ユーザログインのベストプラクティスは以下のワークフロー図の通りである．

<img src="https://learn.microsoft.com/ja-jp/gaming/playfab/features/authentication/media/tutorials/playfab-anonymous-login-and-recoverable-login.png" width=600>


## 参考資料
- [MS: ログインの基本とベストプラクティス](https://learn.microsoft.com/ja-jp/gaming/playfab/features/authentication/login/login-basics-best-practices)
- [MS: アカウント リンクのクイックスタート](https://learn.microsoft.com/ja-jp/gaming/playfab/features/authentication/login/quickstart)
- [ねこじょーかー: 何も考えずにログイン処理を実装する](https://playfab-master.com/playfab-login)
- [ねこじょーかー: ログイン処理のベストプラクティスとは](https://playfab-master.com/playfab-login-best-practices)


<!-- リンク -->
[LoginWithIOSDeviceID]: https://learn.microsoft.com/ja-jp/rest/api/playfab/client/authentication/login-with-ios-device-id?view=playfab-rest
[LoginWithAndroidDeviceID]: https://learn.microsoft.com/ja-jp/rest/api/playfab/client/authentication/login-with-android-device-id?view=playfab-rest
[LoginWithCustomID]: https://learn.microsoft.com/ja-jp/rest/api/playfab/client/authentication/login-with-custom-id?view=playfab-rest

[LoginWithPlayFab]: https://learn.microsoft.com/ja-jp/rest/api/playfab/client/authentication/login-with-playfab?view=playfab-rest
[LoginWithEmailAddress]: https://learn.microsoft.com/ja-jp/rest/api/playfab/client/authentication/login-with-email-address?view=playfab-rest

[LoginWithKongregate]: https://learn.microsoft.com/ja-jp/rest/api/playfab/client/authentication/login-with-kongregate?view=playfab-rest
[LoginWithSteam]: https://learn.microsoft.com/ja-jp/rest/api/playfab/client/authentication/login-with-steam?view=playfab-rest
[LoginWithTwitch]: https://learn.microsoft.com/ja-jp/rest/api/playfab/client/authentication/login-with-twitch?view=playfab-rest
[LoginWithGameCenter]: https://learn.microsoft.com/ja-jp/rest/api/playfab/client/authentication/login-with-game-center?view=playfab-rest