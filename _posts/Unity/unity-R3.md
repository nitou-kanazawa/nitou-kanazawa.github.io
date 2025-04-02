

## R3 とは

[`R3`][R3 リポジトリ]はC#向けの新しい`Reactive Extensions(RX)`ライブラリ．

#### コアモジュールと
`R3`は実装が本体である「コアモジュール」と，各フレームワーク用の「拡張モジュール」からなる．

- Unity
- Godot
- Avalonia
- WPF
- WinForms
- Stride

#### インターフェース


#### Schedulerの廃止

- `IScheduler`の代わりに`TimeProvider`


## R3 を導入する


#### NuGetForUnity をインストールする

``` 
https://github.com/GlitchEnzo/NuGetForUnity.git?path=/src/NuGetForUnity
```


#### R3.Unity をインストールする

```
https://github.com/Cysharp/R3.git?path=src/R3.Unity/Assets/R3.Unity
```





## 参考資料
- neue cc: [R3 - C#用のReactive Extensionsの新しい現代的再実装](https://neue.cc/2024/02/27_R3.html)
- _: [R3 — A New Modern Reimplementation of Reactive Extensions for C#](https://neuecc.medium.com/r3-a-new-modern-reimplementation-of-reactive-extensions-for-c-cf29abcc5826)
- qiita: [次世代Rx「R3」解説](https://qiita.com/toRisouP/items/e7be5a5a43058556db8f)
- qiita: [【Unity】 R3とUniRxの比較まとめ](https://qiita.com/toRisouP/items/4344fbcba7b7e8d8ce16)

<!-- リンク -->
[R3 リポジトリ]: https://github.com/Cysharp/R3
[UniRx リポジトリ]: https://github.com/neuecc/UniRx