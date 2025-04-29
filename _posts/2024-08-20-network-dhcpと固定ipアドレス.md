---
title: DHCPと固定IPアドレス
description: ""
date: 2024-08-20
categories:
  - Networking
tags:
  - IP
  - DHCP
mermaid: false
---



---
## DHCPとは？
`DHCP（Dynamic Host Configuration Protocol）` はIPアドレスを自動で配る仕組み．

家庭用ルーターには、必ずDHCPサーバーが内蔵されている．

#### DHCPの仕組み

`DHCPサーバー`と`DHCPクライアント`で行われる．
(Discover → Offer → Request → Acknowledgement)

```mermaid
sequenceDiagram
    participant Client as DHCPクライアント
    participant Server as DHCPサーバー

    Client->>Server: DHCPサーバーを探す（DHCP Discover）
    Server-->>Client: IPアドレスの提案（DHCP Offer）
    Client->>Server: IPアドレスの払い出し要求（DHCP Request）
    Server-->>Client: 承認・IPアドレス払い出し（DHCP Acknowledgement）
```

例えば，「家庭用ルータでPCやスマホをネットに繋ぐ」場合は，以下のようになる．

```mermaid
sequenceDiagram
    participant PC as PCやスマホ <br>（DHCPクライアント）
    participant Router as Wi-Fiルーター<br>（DHCPサーバー）

    PC->>Router: DHCPサーバーを探す（DHCP Discover）
    Router-->>PC: 「192.168.2.108使えるよ」（DHCP Offer）
    PC->>Router: 「192.168.2.108を使いたいです」（DHCP Request）
    Router-->>PC: 「OK、192.168.2.108を割り当てたよ」（DHCP Acknowledgement）
```

この仕組みのおかげで、ユーザーは何もしなくても通信できる．

#### プロトコルの詳細

- トランスポート層は，コネクションレスの`UDP`を使用
- サーバ側のポート番号は`67番`，クライアント側のポート番号は`68番`


#### DHCPの欠点

便利な`DHCP`だが以下のような欠点もある．

| 弱点                               | 影響する場面                                                                                                               |
| :--------------------------------- | :------------------------------------------------------------------------------------------------------------------------- |
| いつも同じIPがもらえるとは限らない | - NAS、プリンタ、サーバーなど「固定でアクセスしたい機器」が困る<br>- アプリで「192.168.2.108に接続」と決め打ちするとズレる |
| リース切れでIP変更されることがある | ルーターが再起動したり、機器が電源オフしていると、違うIPが配られることがある                                               |

よって，一部の機器には固定IPを設定した方がよい．



--- 
## 固定IPアドレス







---
##
- _: [DHCPとは？しくみからわかりやすく解説！](https://www.hcnet.co.jp/column/detail47.html)
- youtube: [DHCP／フローを徹底解説【情報処理技術者試験／高校情報１／応用情報・基本情報・支援士】](https://www.youtube.com/watch?v=PNDoemWWs54)
