---
title: 講座「Udemy SQLServer文法1」
date: 2025-04-26
categories:
  - 学習記録
  - 講義
tags:
  - SQL
  - SQLServer
mermaid: true
draft: true
---

[Udemy](https://www.udemy.com/course/anderson_sqlinit/?couponCode=KEEPLEARNING)


--- 
## 講座概要

- [x] 1. インストール 
- [x] 2. テーブルの作成
- [x] 3. 基本的なSQL
- [x] 4. テーブル設計と正規化
- [x] 5. 結合＆並び替え


--- 
## 1. インストール 

`SQL Server 2022` をインストールする．
[ダウンロードサイト](https://www.microsoft.com/ja-jp/sql-server/sql-server-downloads)

<img src="/assets/img/SQLServer/SqlServer2022ダウンロード.png" alt="SqlServer ダウンロード" width="500">

`SSMS`をインストールする．
[ダウンロードサイト](https://learn.microsoft.com/ja-jp/ssms/download-sql-server-management-studio-ssms?redirectedfrom=MSDN)


※日本語版は以下のリンク部から取得する．

<img src="/assets/img/SQLServer/SSMSダウンロード_日本語.png" alt="SqlServer ダウンロード" width="400">

SSMSダウンロード_日本語
--- 
## 2. テーブルの作成

--- 
## 3. 基本的なSQL

- `select`
- `where`

--- 
## 4. テーブル設計と正規化


```mermaid
erDiagram
    Customers {
        int     CustomerId PK
        varchar CustomerName
        varchar Address
    }

    Orders {
        int      OrderId    PK
        int      CustomerId FK
        datetime OrderDate
    }

    OrderItems {
        int  OrderId     PK, FK
        int  OrderItemId PK
        int  ProductId   FK
        int Price
    }

    Products {
        int     ProductId  PK
        varchar ProductName
        int   Price
    }

    %% ── relations ─────────────────────────────────────────
    Customers ||--o{ Orders      : places
    Orders    ||--o{ OrderItems  : contains
    Products  ||--o{ OrderItems  : listed
```


--- 
## 5. 結合＆並び替え

`Order`と`OrderItems`の結合

```sql
select * from Orders A
inner join OrderItems B
on a.OrderId = b.OrderId
```

`inner join` `left outter join`

