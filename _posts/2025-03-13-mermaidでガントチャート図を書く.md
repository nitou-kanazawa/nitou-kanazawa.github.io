---
title: Mermaidでガントチャート図を書く
description: ""
date: 2025-04-28T15:00:00.000Z
categories: [Misc]
tags:
  - Mermaid
preview: ""
mermaid: true
---




```mermaid
gantt
    title プロジェクトスケジュール
    dateFormat  YYYY-MM-DD
    section 企画フェーズ
    要件定義           :a1, 2023-01-01, 30d
    設計               :after a1, 20d
    section 開発フェーズ
    コーディング       :2023-02-20, 45d
    テスト             :2023-04-05, 20d
    section リリースフェーズ
    最終確認           :2023-04-25, 5d
    リリース           :2023-04-30, 1d
```






---
## 参考資料
