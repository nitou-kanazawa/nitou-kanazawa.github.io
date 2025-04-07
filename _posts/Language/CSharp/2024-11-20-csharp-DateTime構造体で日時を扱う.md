---
title: DateTime構造体で日時を扱う
category: C#
tags:
  - C#
id: 88d3120f-1210-48f6-9e6c-a4c3b6543f4f
---

## DateTime構造体

##

#### 関連する型
`DateTime`の他に.NETで日付や時刻を扱う型には、以下のものがある．

- DateTimeOffset: タイムゾーンに依存しない日時情報
- TimeSpan: 時間間隔
- DateOnly: 特定の日付
- TimeOnly: 特定の時刻
- TimeZoneInfo
- Calender

※`DateOnly`、`TimeOnly`は`.NET6`で導入されたため、Unity(.NET Standard2.1)では使用できない

[MS: DateOnly 構造体と TimeOnly 構造体を使用する方法](https://learn.microsoft.com/ja-jp/dotnet/standard/datetime/how-to-use-dateonly-timeonly)

## 

## 参考資料

- [MS: DateTime 構造体](https://learn.microsoft.com/ja-jp/dotnet/api/system.datetime?view=net-8.0)
- [MS: DateTimeOffset 構造体](https://learn.microsoft.com/ja-jp/dotnet/api/system.datetimeoffset?view=net-8.0)
- [MS: DateTime、DateOnly、DateTimeOffset、TimeSpan、TimeOnly、TimeZoneInfo の使い分け](https://learn.microsoft.com/ja-jp/dotnet/standard/datetime/choosing-between-datetime)

