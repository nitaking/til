## mainパッケージ
Goのコードはパッケージの宣言から始まる。

```.go
package main
```

プログラムをコンパイルして実行すると、mainパッケージの中にあるmain()関数が実行される。

```main.go
func main(){
}
```


### 複数パッケージ
複数のパッケージを取り組む場合は次のように縦に並べて記述する。
```.go
import (
    "fmt"
    "github.com/wdpress/gosample"
    "strings"
)
```
Goの標準パッケージはインストールしたGoの中に含まれているため、自動でパスが解決される。
それ以外のパッケージはGOPATH環境変数からパスを解決する。

### オプションの指定
インポートするパッケージ名の前に、オプションを使用することができる。
```.go
package main

import (
    f "fmt"
    _ "github.com/wdpress/gosample"
    . "strings"
)

func main() {
    // fmt.Println()がf.Println()になり
    // strings.ToUpper()がToUpper()なっている
    f.Println(ToUpper("hello world"))
}
```
+ 任意の名前:`f`

任意の名前（上記 f）を指定した場合は、プログラム内のパッケージ名を変えることができる。

+ 使用しないパッケージ:`_`

`_`をつけた場合は、インポートしたパッケージを使用しないことをコンパイラに伝えます。
Goではインポートしたパッケージを使用しないとコンパイルエラーになるため、`_`をつけることでエラーから回避できます。

+ パッケージ名の省略:`.`

.をつけた場合、使用するときにパッケージ名が省略可能になります

## 組込み型
Goの文字列はstringという組込み型として扱われる

|  型 | 説明 |
|  :------ | :------ |
|  uint8 | 8ビット符号なし整数 |
|  uint16 | 16ビット符号なし整数 |
|  uint32 | 32ビット符号なし整数 |
|  uint64 | 64ビット符号なし整数 |
|  int8 | 8ビット符号あり整数 |
|  int16 | 16ビット符号あり整数 |
|  int32 | 32ビット符号あり整数 |
|  int64 | 64ビット符号あり整数 |
|  float32 | 32ビット浮動小数 |
|  float64 | 64ビット浮動小数 |
|  complex64 | 64ビット複素数 |
|  complex128 | 128ビット複素数 |
|  byte | uint8のエイリアス |
|  rune | Unicodeのコードポイント |
|  uint | 32か64ビットの符号なし整数 |
|  int | 32か64ビットの符号あり整数 |
|  uintptr | ポインタ値用符号なし整数 |
|  error | エラーを表わすインタフェース |

## 変数
変数の宣言は、varで始まり、次に変数名、最後に型となる。
```.go
var message string = "hello world"

func main() {
    fmt.Println(message)
}
```
型と変数名の順番が少し変。

### 複数の変数宣言と初期化
```.go
var foo, bar, buz string = "foo", "bar", "buz"
```

var宣言と2つめ以降の型を省略する書き方もできる
```.go
var (
a string = "aaa"
b = "bbb"
c = "ccc"
d = "ddd"
e = "eee"
)
```

### 関数内での宣言と初期化
変数宣言・初期化を関数内で行う場合、varと型宣言を省略する代わりに`:=`という記号を使うことができる。
```.go
func main() {
    // どちらの書き方も同じ意味
    // var message string = "hello world"
    message := "hello world"
    fmt.Println(message)
}
```
（変数の型は代入する値からコンパイラによって推論される）

### 定数
変数宣言のvarをconstに変えると定数になります。
```.go
func main() {
    const Hello string = "hello"
    Hello = "bye" // cannot assign to Hello
}
```
定数宣言は、組込型のerror以外の型で使用することができる。
定数に対する再代入はコンパイルエラーになる。

### ゼロ値

変数宣言時、値を明示的に初期化しなかった場合、変数はゼロ値というデフォルト値で初期化される。（nullではない。要注意。）
ゼロ値は型ごとに決まっている。
```.go
func main() {
    var i int // iはゼロ値で初期化
    fmt.Println(i) // 0
}
```
ゼロ値の一覧

|  型 | ゼロ値 |
|  :------ | :------ |
|  整数型 |  |
|  浮動小数点型 |  |
|  bool |  |
|  string | "" |
|  配列 | 各要素がゼロ値の配列 |
|  構造体 | 各フィールドがゼロ値の構造体 |
|  そのほかの型 | nil（※） |

## switch
Goのswitch文は、値の比較だけでなく条件分岐にも使用可能。

### 値での分岐
値を用いたswitch文

```.go
func main(){
  n := 10
  switch n {
    case 15:
      fmt.Println("FizzBuzz")
    case 5,10:
      fmt.Println("Buzz")
    case 3,6,9:
      fmt.Println("Fizz")
    default:
        fmt.Println(n)
  }
}
```

swith文に指定した値に一致するcaseが実行される。
どのcaseにも一致しなかった場合はdefaultが実行される。
カンマで区切った複数値も指定できる。

### fallthrough
Goのswitchではcaseが実行されると次のcaseに実行が映ることなくswitch文が終了する。
caseの処理が終わった後に、次のcaseに処理を進めたい場合は、case内にfallthroughを書くことで名おじ的に次のcaseに処理を進めることができる。
