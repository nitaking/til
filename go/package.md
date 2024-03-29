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
