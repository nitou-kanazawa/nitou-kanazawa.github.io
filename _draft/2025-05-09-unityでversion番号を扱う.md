---
title: UnityでVersion番号を扱う
date: 2025-05-09
categories: 
  - Unity
tags: 
  - C#
mermaid: false
---

Unityでアプリのバージョン番号（例: 1.2.3 や 2.0）などを扱う際、単なる文字列比較では思わぬバグを生むことがあります。


---
## 1. 標準のVersion型を使う 

.NETには [`System.Version`][MSDN: Version クラス] という便利な型が用意されている．Unityでも使用可能で、以下のようにバージョン比較を安全かつ簡潔に行える．


#### 使用例

```cs
var v1 = new Version("1.2.3");
var v2 = new Version(1, 2, 4);

// 比較
if (v1 < v2) {
    Debug.Log("v1はv2より古いバージョンです。");
}
```



```cs
// 数値で生成
new Version(major, minor);                 // 例: new Version(1, 0)
new Version(major, minor, build);          // 例: new Version(1, 0, 5)
new Version(major, minor, build, revision);// 例: new Version(1, 0, 5, 2)
// 文字列で生成
new Version("1.0.2");
```

#### その他
JSONにシリアライズすると，多少煩雑になるのがちょっと気になる．各ファイルにバージョンを記録する場合，一行に収まっていてほしい．


#### 参考記事
- kanのメモ帳: [バージョンの文字列(1.1や1.0.1など)のどちらが新しいかを判別する簡単な方法【C#】](https://kan-kikuchi.hatenablog.com/entry/System_Version)


---
## 2. 自前で実装する


#### 2.1 文字列 + 大小比較メソッド


#### 2.2 独自型を定義

```cs
public class SimpleVersion : IComparable<SimpleVersion> {
    public int[] Parts { get; }

    public SimpleVersion(string versionString) {
        Parts = versionString.Split('.')
                             .Select(s => int.Parse(s))
                             .ToArray();
    }

    public int CompareTo(SimpleVersion other) {
        for (int i = 0; i < Math.Max(this.Parts.Length, other.Parts.Length); i++) {
            int a = i < this.Parts.Length ? this.Parts[i] : 0;
            int b = i < other.Parts.Length ? other.Parts[i] : 0;

            if (a != b) return a.CompareTo(b);
        }
        return 0;
    }
}
```

#### 参考記事
- qiita: [バージョン番号(string)の比較 (C#)](https://qiita.com/tetr4lab/items/ae274554e2c13df85499)
- コガネブログ: [【C#】バージョン番号を管理する構造体の例](https://baba-s.hatenablog.com/entry/2023/10/13/095547)


--- 
## まとめ
- 基本的には `System.Version` の使用がおすすめ。安全で、比較も明快。



<!-- Link -->
[MSDN: Version クラス]: https://learn.microsoft.com/ja-jp/dotnet/api/system.version?view=net-8.0
