---
title: DataTime型の変換
category: C#
tags:
  - C#
id: ec0dda1c-2ffe-46e7-819e-0d5af6bb9dfb
---

## DateTime型 → String型

文字列への変換は`dateTime.ToString(string format)`を使用する．

```cs
DateTime dt = DateTime.Now

var date1 = dt.ToString("yyyy/MM/dd"); // "2025/02/21"
vae date2 = dt.ToString("yyyy/MM/dd HH:mm:ss"); // "2025/02/21 16:04:32"
```

formatに指定できる文字とその結果は`VisualStudio`のインテリセンスで確認できる．
`Month`と`Minite`など先頭文字が被っている場合では**大文字/小文字**や**文字数**で分岐しているため、注意が必要（`d`と`dd`も前者は`Date`、後者は`Day`になる）

また、`DateTime`の`ToString(string format)`内部では`DateTimeFormat`クラスのメソッドを叩いているので詳細は以下のコードを確認すればよい．

[DateTimeFormat.cs](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Private.CoreLib/src/System/Globalization/DateTimeFormat.cs#L125)



#### フォーマット指定（日付）

```
 Patterns   Format      Description                           Example
 =========  ==========  ===================================== ========
"d"     "0"         day w/o leading zero                  1
  "dd"    "00"        day with leading zero                 01
  "ddd"               short weekday name (abbreviation)     Mon
  "dddd"              full weekday name                     Monday
  "dddd*"             full weekday name                     Monday


  "M"     "0"         month w/o leading zero                2
  "MM"    "00"        month with leading zero               02
  "MMM"               short month name (abbreviation)       Feb
  "MMMM"              full month name                       February
  "MMMM*"             full month name                       February

  "y"     "0"         two digit year (year % 100) w/o leading zero           0
  "yy"    "00"        two digit year (year % 100) with leading zero          00
  "yyy"   "D3"        year with leading zeroes              2000
  "yyyy"  "D4"        year with leading zeroes              2000
  "yyyyy" "D5"        year with leading zeroes              02000
```

#### フォーマット指定（時間）
```
Patterns   Format      Description                           Example
=========  ==========  ===================================== ========
  "h"     "0"         hour (12-hour clock)w/o leading zero  3
  "hh"    "00"        hour (12-hour clock)with leading zero 03
  "hh*"   "00"        hour (12-hour clock)with leading zero 03

  "H"     "0"         hour (24-hour clock)w/o leading zero  8
  "HH"    "00"        hour (24-hour clock)with leading zero 08
  "HH*"   "00"        hour (24-hour clock)                  08

  "m"     "0"         minute w/o leading zero
  "mm"    "00"        minute with leading zero
  "mm*"   "00"        minute with leading zero

  "s"     "0"         second w/o leading zero
  "ss"    "00"        second with leading zero
  "ss*"   "00"        second with leading zero
```

#### フォーマット指定（その他）
```
```



## DateTime型 → String型（和暦）
```cs
DateTime dt = DateTime.Now; // → 2022/08/27 16:04:32

string sDate = "";
System.Globalization.CultureInfo Info = new System.Globalization.CultureInfo("ja-JP");
Info.DateTimeFormat.Calendar = new System.Globalization.JapaneseCalendar();
sDate = dt.ToString("ggyy年M月d日"); // → 令和4年8月27日
```

## DateTime型 → 数値型（int, long）
```cs
DateTime dt = DateTime.Now; // → 2022/08/27 16:04:32

int iDate = 0;
iDate = int.Parse(dt.ToString("yyyyMMdd")); // → 20220817

long lDate = 0;
lDate = long.Parse(dt.ToString("yyyyMMddHHmmss")); // → 20220817160432
```


## int型 → DateTime型

```cs
DateTime dDate;

dDate = new DateTime(2022, 12, 31); // 2022/12/31 0:00:00
dDate = new DateTime(2022, 12, 31, 1, 2, 3); // 2022/12/31 1:02:03
```

文字形式
```cs
iDate = 20220831;

string s = iDate.ToString();
int iYear = iDate / 10000;
int iMonth = (iDate / 100) % 100;
int iDay = (iDate % 100);

DateTime dDate = new DateTime(iYear, iMonth, iDay); // 2022/08/31
```




## 参考資料

- [MS: DateTime 構造体](https://learn.microsoft.com/ja-jp/dotnet/api/system.datetime?view=net-8.0)
- [qiita: DateTime型の変換　まとめ](https://qiita.com/t_hane/items/c418e5b531156afeb2f9)
- [_: DateTimeの使い方とフォーマットの種類を紹介！](https://marunaka-blog.com/csharp-datetime/)
- [_: DateTime.ToString() で日付の書式設定をするには？](https://marunaka-blog.com/csharp-datetime-tostring/4514/)