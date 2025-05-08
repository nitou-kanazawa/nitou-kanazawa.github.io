---
title: HttpClientについて
categories: [ C# ]
tags:
  - C#
  - HTTP
id: dfe102d6-0d86-4205-8f32-2388dee20941
---

普段，なんとなくで使用しているHttpClient関連について，学びなおそうと思う．


---
## HTTP

#### 概要

`Http(Hypertext Transfer Protocol)`はアプリケーション層の通信プロトコル．
- クライアントリクエスト＆サーバーレスポンス形式で通信を行う．
- ステートレスであるため，リクエスト間に状態を保持しない．

#### HTTPの構造

**リクエスト**
- メソッド（GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS など）
- ヘッダー（User-Agent, Accept, Authorization など）
- ボディ（必要に応じて送信するデータ）

**レスポンス**
- ステータスコード（200, 404, 500 などの意味）
- ヘッダー（Content-Type, Set-Cookie など）
- ボディ（HTML, JSON, バイナリデータなど）

#### Httpの動作


---
## HttpClient（C#）

#### 概要

[HttpClientクラス](https://learn.microsoft.com/ja-jp/dotnet/api/system.net.http.httpclient?view=net-9.0)



#### 基本的な使い型

```cs
using(var client = new HttpClient()){
  // 
  var response = await client.GetAsync(url);
}
```

※上記のように書くと毎回ソケットを開いてリソースを消費するため，ソケットの枯渇など問題につながる．よって実際はアプリケーションの存続期間全体に渡って`HttpClient`は使いまわすべき．


#### リクエストの送信

```cs
using (var client = new HttpClient()) {
    var result1 = await client.GetAsync(@"http://hoge.example.com"); // GET
    ...

    var result2 = await client.PostAsync(@"http://fuga.example.com"); // POST
    ...
}
```

`HttpRequestMessage`を`SendAsync()`で送る場合

```cs
var request = new HttpRequestMessage(HttpMethod.Get, @"http://hoge.example.com");

using (var client = new HttpClient()) {
    var result = await client.SendAsync(request);
    ...
}
```

#### レスポンスの処理













---
## 参考資料
- qiita: [System.Net.Http.HttpClientを使ってWeb APIとHTTP通信する方法](https://qiita.com/iwasiman/items/40775d66e2ad5a9613e3)
- qiita: [C# 今更ですが、HttpClientを使う](https://qiita.com/rawr/items/f78a3830d894042f891b)
- zenn: [HttpClientでAPIリクエストを送信する：StringContentとFormUrlEncodedContentの使い分け](https://zenn.dev/shimiyu/articles/2ba819632490a0)

- qiita: [HttpClientをusingで囲わないでください](https://qiita.com/superriver/items/91781bca04a76aec7dc0)

