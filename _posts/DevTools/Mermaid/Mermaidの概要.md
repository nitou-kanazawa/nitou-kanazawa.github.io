---
title: Mermaidの概要
categories: [ Misc ]
tags:
  - Mermaid
mermaid: true
---

Mermaidはテキストから図

ブラウザ上で動作する[Live Editor](https://mermaid.live/edit#pako:eNpVTU1vgkAQ_SubObUJGhQtyKFJxdaLSXvwVPAwkZElurtkWGIt8N-70LRp32ne57RwNDlBDKeLuR4lshX7TaaFw1OaSC5rq7A-iMnksduSFcpounVifbc1opamqkpd3H_n10NIJO1uiJGwstTn_ttKxv6rpk5s0h1W1lSHv87-ajrxnJZv0s3_dySTa72kJ4xPODkiiwR5jIAHBZc5xJYb8kARKxwotIObgZWkKIPYnTnyOYNM965ToX43Rv3U2DSFBLd9qR1rqhwtbUosGNWvyqRz4sQ02kIcrFbjCMQtfDg6n_ojlrP5IphFoQc3p0bhNIwe_CgIFr4_C-a9B5_jV38ahcv-CyVMcy0)もある．

---

Mermaidでは以下の図を作成できる。

- フローチャート
- シーケンス
- クラス図
- 状態遷移
- ER図
- ガントチャート
- ユーザジャーニー
- パイチャート
- gitグラフ
  
- Flowchart
- Pie chart diagrams
- Quadrant Chart
- Mindmap
- Timeline Diagram

※以下ではドキュメントに掲載されているサンプルコードを使用している．（11.6.0）

---

## [Flowchart][Mermid - Flowchart]

```mermaid
graph LR
    A[Square Rect] -- Link text --> B((Circle))
    A --> C(Round Rect)
    B --> D{Rhombus}
    C --> D
```

- 方向を指定できる．（TB,TD,BT,LR,RL）
- サブグラフを指定できる．

---

## [Sequence diagrams][Mermid - Sequence diagrams]

プロセスが互いにどのように動作し，どのような順序で動作するかを示す相互作用図．

```mermaid
sequenceDiagram
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop HealthCheck
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts<br/>prevail...
    John-->>Alice: Great!
    John->>Bob: How about you?
    Bob-->>John: Jolly good!
```

---

## [Class diagrams][Mermid - Class diagrams]

```mermaid
---
title: Animal example
---
classDiagram
    note "From Duck till Zebra"
    Animal <|-- Duck
    note for Duck "can fly\ncan swim\ncan dive\ncan help in debugging"
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
        +String beakColor
        +swim()
        +quack()
    }
    class Fish{
        -int sizeInFeet
        -canEat()
    }
    class Zebra{
        +bool is_wild
        +run()
    }
```

---
## [State diagrams][Mermid - State diagrams]

```mermaid
---
title: Simple sample
---
stateDiagram-v2
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
```

---

## [Quadrant Chart]
```mermaid
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
```


---

## [Packet Diagram][Mermid - Packet Diagram]

```mermaid
---
title: "TCP Packet"
---
packet-beta
0-15: "Source Port"
16-31: "Destination Port"
32-63: "Sequence Number"
64-95: "Acknowledgment Number"
96-99: "Data Offset"
100-105: "Reserved"
106: "URG"
107: "ACK"
108: "PSH"
109: "RST"
110: "SYN"
111: "FIN"
112-127: "Window"
128-143: "Checksum"
144-159: "Urgent Pointer"
160-191: "(Options and Padding)"
192-255: "Data (variable length)"
```

---

## [Mindmap][Mermid - Mindmap]

```mermaid
mindmap
  root((mindmap))
    Origins
      Long history
      ::icon(fa fa-book)
      Popularisation
        British popular psychology author Tony Buzan
    Research
      On effectiveness<br/>and features
      On Automatic creation
        Uses
            Creative techniques
            Strategic planning
            Argument mapping
    Tools
      Pen and paper
      Mermaid
```

- ノードの形を変更できる（四角，円，吹き出し，...）

---

## [Timeline Diagram]

```mermaid
timeline
    title History of Social Media Platform
    2002 : LinkedIn
    2004 : Facebook
         : Google
    2005 : YouTube
    2006 : Twitter
```


---

## [Gitgraph Diagrams][Mermid - Gitgraph Diagrams]

```mermaid
---
title: Example Git diagram
---
gitGraph
   commit
   commit
   branch develop
   checkout develop
   commit
   commit
   checkout main
   merge develop
   commit
   commit
```

---

- [Github](https://github.blog/developer-skills/github/include-diagrams-markdown-files-mermaid/)
- [Zenn](https://zenn.dev/zenn/articles/markdown-guide#%E3%83%80%E3%82%A4%E3%82%A2%E3%82%B0%E3%83%A9%E3%83%A0)

## 参考資料
- qiita: [Mermaid記法に入門しよう](https://qiita.com/moikei/items/24e9e5bd8319a10f0115)
- qiita: [【Qiitaでも使える】テキストから図が生成できるMermaidについてのザックリ解説](https://qiita.com/b-mente/items/97a4296666faccd53a72)
- qiita: [テキストから図が生成できるMermaidでAWS構成図をつくる](https://qiita.com/b-mente/items/b17275090176d63d1d69)
- zenn: [mermaidでフローチャートを描く](https://zenn.dev/yuriemori/articles/e097dbd950df86)

<!-- Link -->
[Mermaid ドキュメント]: https://mermaid.js.org/intro/



<!-- Link -->
[Mermid - Flowchart]: https://mermaid.js.org/syntax/flowchart.html
[Mermid - Sequence diagrams]: https://mermaid.js.org/syntax/sequenceDiagram.html
[Mermid - Class diagrams]: https://mermaid.js.org/syntax/classDiagram.html
[Mermid - State diagrams]: https://mermaid.js.org/syntax/stateDiagram.html
[Mermid - Quadrant Chart]: https://mermaid.js.org/syntax/quadrantChart.html
[Mermid - Packet Diagram]: https://mermaid.js.org/syntax/packet.html
[Mermid - Mindmap]: https://mermaid.js.org/syntax/mindmap.html
[Mermid - Gitgraph Diagrams]: https://mermaid.js.org/syntax/gitgraph.html
[Mermid - ]
[Mermid - ]
[Mermid - ]
[Mermid - ]
[Mermid - ]
