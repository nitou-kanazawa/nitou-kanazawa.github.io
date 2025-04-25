---
title: PlantUMLでアクティビティ図（シーケンス）を書く
categories: [ Tool ]
tags:
  - UML
  - PlantUML
---

PlantUMLのアクティビティ図には，[古い構文][Document アクティビティ図（レガシー版）]と[新しい構文][Document アクティビティ図（新しい構文）]が存在するので，注意が必要．新しい構文の方は `Graphiviz` に依存せずに可視化できる．

---
## 基本


#### ラベル

ラベルは `:` で始まり，`;` または `]` で終わる．
- `;` : Round node
- `]` : Rect node

```puml
  : Hello world;
  : Hello world]
```

#### 開始・終了

`start` で開始 ，`stop` または `end` で終了の記号．

```puml
start
  : 処理;
stop
```

```puml
start
  : 処理;
end
```

---
## 制御構文

#### ループ処理 (repeat)

```puml
start
  :i = 0;
  repeat
    :処理;
    :i = i + 1;
  repeat while (i > 10?)
stop
```

#### ループ処理 (while)

```puml
start
  :処理１;
  while (i < 10)
      :処理２;
  endwhile
  :処理３;
stop
```


#### 分岐 (if)

```puml
start
  :[データ入力];

  if (入力値 > 0?) then (Yes)
    :[正の処理];
  else (No)
    :[負の処理];
  endif

  :[結果出力];
stop
```

```puml
start
  if (test==A) then (yes)
    :処理A]
  else if(test == B) then(yes)
    :処理B]
  else (no)
    :処理C]
  endif
stop
```

#### 分岐 (switch)

```puml
start
  switch (test?)
  case ( A )
    :条件 1です;
  case ( B ) 
    :条件 2です;
  case ( C )
    :条件 3です;
  case ( D )
    :条件 4です;
  case ( E )
    :条件 5です;
  endswitch
stop
```


---
## その他

#### サブルーチン

```puml
start
  :メイン処理開始;

  partition サブルーチン1 {
    :サブルーチン処理1;
    :サブルーチン処理2;
  }

  :メイン処理続行;
stop
```

#### スイムレーン

```puml
|Swimlane1|
start
:foo1;
|#AntiqueWhite|Swimlane2|
:foo2;
:foo3;
|Swimlane1|
:foo4;
|Swimlane2|
:foo5;
```


---
## 参考資料
- _: [よく使うPlantUMLのフローチャートやシーケンス図の記述パターンをまとめてみた](https://coralnet.co.jp/wordpress/?p=902)




<!-- Link -->
[Document アクティビティ図（レガシー版）]: https://plantuml.com/ja/activity-diagram-legacy
[Document アクティビティ図（新しい構文）]: https://plantuml.com/ja/activity-diagram-beta
