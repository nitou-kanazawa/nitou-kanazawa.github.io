---
title: Quarto
categories: [ Misc ]
tags:
  - Quarto
mermaid: true
---


## インストール

1. `Quarto CLI` をインストールする．
2. VSCodeに [Quarto拡張機能][Quarto VSCode拡張機能]を追加する．
3. `Python`+`jupyter`の環境構築

```bash
pip install jupyter matplotlib numpy
```

公式の使用例()


## 

```mermaid
flowchart LR
    qmd --> jupyter --> md --> Pandoc
    Pandoc --> Doquments

    subgraph Doquments
        Word
        PDF
        HTML

    end
```


---

## 


---

## 参考資料
- quarto: [Tutorial: Hello, Quarto](https://quarto.org/docs/get-started/hello/vscode.html)
- zenn: [Quartoを使ってJupyterより綺麗なPythonコード入りドキュメントを作る](https://zenn.dev/mosamosa/articles/3e57cb1fe0f1a5)

<!-- Link -->
[Quarto Gallery]: https://quarto.org/docs/gallery/
[Quarto VSCode拡張機能]: https://marketplace.visualstudio.com/items?itemName=quarto.quarto
[Quarto VSCode チュートリアル]: 