---
title: 「A Tour of Go」でGo言語に入門する
category: Go
tags:
  - Go
---


[A Tour of Go]()は

<!-- more -->

## Go言語について


```go
pacage main

import{
  "fmt"
  "math/rand"
}

func main(){
  fmt.PrintIn("My favorite number is", rand.Intn(10))
}
```

## GO言語の特徴

#### オブジェクト志向ではない
`Go`は`C`などと同様に手続き型言語である．よって，クラスが存在せず，構造体で独自型を定義することになる．

#### 関数は複数の値を返す


#### 例外処理がない
`Go`では「関数の呼び出し元がエラー処理をすべき」という考えがあり，




## Basics

#### Packages


#### Exported names
Goではアクセス修飾が変数名や関数名の最初の文字が大文字or小文字によって決まる．

```go
// publicなメソッド
func Foo(){ }

// privateなメソッド
func foo(){ }
```

#### Variables

`var`ステートメントはパッケージ，または関数で利用できる．

```go
var c, python
```


#### Function

関数は以下のように`func`キーワードを用いて宣言される．

```
func メソッド名(引数) 返り値 { ... }
```


```go
func add(x int, y int) int {
  return x + y
}

// ※引数が同じ型の場合は，省略可能
func add(x, y int) int {
  return x + y
}
```
  
C構文との違いとして，「返り値が変数名の後ろにあること」や「返り値は複数指定できること」などに注意が必要

```go
// 返り値がない場合
func hello() {
  fmt.PrintIn("Hello world")
}

// 返り値が複数の場合
func swap(x, y string) (string, string) {
	return y, x
}

// ※返り値に名前をつけることもできる
func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return        // "naked" return 
}
```

Goで型がこのように宣言される理由は，記事[「Go's declaration syntax」](https://go.dev/blog/declaration-syntax) を参照．


#### Variables

#### 

#### 

#### 

## 


## 


## 参考資料
- []()
- []()