---
title: SwiftでSMBファイル共有を行う
category: Swift
tags:
  - SMB
---


<!-- more -->


## SwiftでSMB

#### SMBとは？

- Server Mesage Blockの略．
- LAN内のファイル共有やプリンタ共有に利用される**通信プロトコル**
- MacやWindowsのファイル共有にはSMBプロトコルが使われている．
- バイナリプロトコルのため，データはバイナリ形式で送受信する．
- ステートフルなプロトコル．


#### SMBファイル共有を実装する
SMBプロトコルを実装するために，重要な項目は以下の３つ．

- [プロトコルの仕様書][SMBプロトコル仕様書]: WebサービスにおけるAPI
- TCP Soket Connection: WebサービスにおけるURLSession
    - Network.framwork
    - NSStream
    - SwiftNIO
- Binary Serialize/Deserialize: WebサービスにおけるJson/Codable


#### SwiftのSMBライブラリ

Swiftで利用できるSMBクライアントライブラリ

1. [kishikawakatsumi/SMBClient](https://github.com/kishikawakatsumi/SMBClient)
2. [amosavian/AMSMB2](https://github.com/amosavian/AMSMB2)
3. [filmicpro/SMBClient](https://github.com/filmicpro/SMBClient)

今回は，`kishikawakatsumi/SMBClient`を利用する．2024年リリースと新しく，開発者が`iOSDC Japan 2024`でライブラリ実装に関する[講演][SMBファイル共有をSwiftで実装する by 岸川克己]を行っていることもあり，とっつきやすいと考えた．



## SMBClientを利用する

基本的な使い方はリポジトリの[README.md](https://github.com/kishikawakatsumi/SMBClient)で紹介されている．

#### リモートファイル一覧の取得 

```swift
import SMBClient

let client = SMBClient(host: "198.51.100.50")

try await client.login(username: "alice", password: "secret")
try await client.connectShare("Public")

let files = try await client.listDirectory("")
print(files.map { $0.fileName })

try await client.disconnectShare()
try await client.logoff()
```


#### 


#### 


## SMBClientの実装を眺める


#### TCP Soket Connection
TCPソケット通信には標準ライブラリの`Network.framwork`が利用されている．

```swift
let endpoint = NWEndpoint.hostPort(
    host: NWEndpoint.Host("198.51.100.50"),
    host: NWEndpoint.Port(intergerLiteral: 445)   // SMBのポート番号は一般的に445が利用される
)

let connection = NWConnection(to: endpoint, using: .tcp)  // TCPプロトコルを指定

// コネクション確立の確認用クロージャ
connection.stateUpdateHandler = {(state) in
    switch state {
        case .setup, .preparing, .failed, .cancelled:
          break
        case .ready:
          // TCP接続が確立されたら，データ送受信を行う
          let data = ...
          connection.send(content: data, completion: .contentProcessed(){(error) in
            ...
          })
          
        @unknown default:
          break
    }
}

connection.start(queue: .global(qos: .userInitiated))
```

#### タイムアウト処理の追加

TCPソケット通信を担っている`NWConnection`のインスタンスにタイムアウト設定を行う必要がある．


#### SMBプロトコルのリクエスト

リクエストの種類は18種類．

- NEGOTIATE
- SESSION_SETUP
- LOGOFF
- TREE_CONNECT
- TREE_DISCONNECT
- CREATE
- CLOSE
- FLUSH
- READ
- WRITE
- LOCK
- ECHO
- CANCEL
- IOCTL
- QUERY_DIRECTORY
- CHANGE_NOTIFY
- QUERY_INFO
- SET_INFO


## 参考資料
- [_: SMBファイル共有をSwiftで実装する by 岸川克己](https://fortee.jp/iosdc-japan-2024/proposal/1b5e79c6-b5e2-4388-85f2-d0820c3174b4)
- [note: M1登場以降 macOSのSMB実装がずっとやらかしている件](https://www.note.lespace.co.jp/n/n53b8d7135039)


<!-- リンク -->

[SMBファイル共有をSwiftで実装する by 岸川克己]: https://fortee.jp/iosdc-japan-2024/proposal/1b5e79c6-b5e2-4388-85f2-d0820c3174b4

[SMBプロトコル仕様書]: https://learn.microsoft.com/ja-jp/openspecs/windows_protocols/ms-smb2/5606ad47-5ee0-437a-817e-70c366052962