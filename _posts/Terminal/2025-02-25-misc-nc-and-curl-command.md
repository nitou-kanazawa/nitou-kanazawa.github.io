---
title: curlとncコマンドでHTTP通信をテストする
category: Misc
tags:
  - HTTP
  - Linux
---

HTTP通信を

<!-- more -->


## curlコマンド

`curl(カール）`は様々なプロトコルを使用してデータ転送を行うことができるコマンド．APIの動作確認でHTTPリクエストしたい、サーバーのレスポンスを確認したい時などに使われる．

**基本構文**

```
curl [オプション] URL
```

**よく使用するオプション**

```
# GET
curl https://xxx...

# POST
curl -X POST https://xxx... 

# PUT
curl -X PUT https://xxx...

# DELETE
curl -X DELETE https://xxx...
```


## ncコマンド

`nc`は`NetCat`の略．Netcatは、Unix系OSコマンドラインアプリケーションの一つ。TCPやUDPのパケットを読み書きするバックエンドとして機能するツール．

**基本構文**
```
nc [オプション] ホスト名 ポート番号
```




```
```


## 参考資料

- [qiita: curlコマンド完全ガイド](https://qiita.com/kojiro30/items/5ead563c44ad6086ad41)
- [qiita: nc(netcat)コマンドの説明と使い方について](https://qiita.com/boccham/items/536bf9201eec81c617d5)
- []()
- []()
- []()
- []()