---
title: HTTPを理解する -HTTPとは？-
category: Web
tags:
  - HTTP
id: 94a2dfac-8ffe-40af-973e-9158b1ee13c1
---

## HTTPとは

`HTTP(Hypertext Transfer Protocol)`はアプリケーション層の通信プロトコル．


- クライアントリクエスト＆サーバーレスポンス形式で通信を行う．
- ステートレスであるため，リクエスト間に状態を保持しない．

## Httpの基本構成

`HTTP`の主な構成要素は以下の通りです。

1. リクエストメッセージ
   - クライアントから送り出される記号串のメッセージ。
   - 突出メソッド(GET、POST等)、リクエストURI、ヘッダ、ボディなどが含まれる。

2. レスポンスメッセージ
   - サーバーがクライアントのリクエストに対して返す記号串。
   - ステータスコード(200 OK、404 Not Found等)や、実際のコンテンツが含まれる。

##

## Httpの変遷

Httpは定期的に改善が行われている．主な変遷は以下の通り．

- **Http/0.9**: 最初期の版。一文字列のリクエストみを送ることが可能。
- **Http/1.0**: ヘッダとステータスコードが追加。
- **Http/1.1**: スティッキな提供のために、パイプラインの実装やキャッシュの使用が可能に。
- **Http/2**: ヘッダラインの乱序送信やサーバー上での事前追加が可能に。
- **Http/3**: 

※Unity(.NET Standard2.1)では`Http/2`は使用できない．（`YetAnotherHttpHandler`を導入すれば使える）


## 参考資料
- [wiki: Hypertext Transfer Protocol](https://ja.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
- []()
- []()
- []()
