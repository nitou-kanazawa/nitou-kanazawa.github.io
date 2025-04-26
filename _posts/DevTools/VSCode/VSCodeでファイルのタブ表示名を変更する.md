---
title: VSCodeでファイルのタブ表示名を変更する
categories: [ Tool, VSCode ]
tags:
  - VSCode
---

VSCode`1.88`以降で追加された `Custom Editor Labels` 機能を使えばタブ表示名をカスタムできる．`index.xxx`など，同名ファイルが複数ある場合の対処に使用されている．

今回は `jekyll` でホスティングしている技術記事のファイル名が ``

---
## 設定方法

`settings.json` の `workbench.editor.customLabels.patterns` に設定を追加する．

```json
"workbench.editor.customLabels.patterns": {
    "**/index.md": "${dirname}/${filename}.${extname}",
    "**/*": "${dirname}/${filename}.${extname}",
}
```


---
## 使用できる変数
 
- `${dirname}` : ファイルが配置されているフォルダーの名前．
- `${dirname(N)}` : ファイルが配置されている n 番目の親フォルダーの名前．
- `${filename}` : ファイル拡張子のないファイル名．
- `${extname}` : ファイル拡張子．
- `${extname(N)}` : `.` で区切られたファイルの n 番目の拡張子．


--- 
## 参考資料
- zenn: [【index.ts】そのVSCodeタブ名、わかりづらくない？【page.tsx】](https://zenn.dev/bmth/articles/vscode-tab-display-name-alias)
- sure TIL: [【VSCode】同じファイル名のタブの表示をカスタマイズして見やすくする](https://atsum.in/vscode/editor-custom-label/)

- github issue: [[Feature Request] Capture / replace for Custom Label patterns #212827](https://github.com/microsoft/vscode/issues/212827?utm_source=chatgpt.com)
