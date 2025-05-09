---
title: VSCodeの設定
categories: 
  - Tool
tags:
  - VSCode
---



---

#### 空行にもインデントを残す

🛠 方法1：editor.trimAutoWhitespace を無効化
settings.json に以下を追加：

```json
"editor.trimAutoWhitespace": false
```
これで，空行のインデントが削除されるのを防げる．

🛠 方法2：.editorconfig にも明示的に設定（補足）
```ini
[*.cs]
trim_trailing_whitespace = false
```
※ ただし，これはファイル保存時に効く設定であり，リアルタイムではない．


--- 



--- 




---
