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
