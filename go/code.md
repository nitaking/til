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

+ 任意の名前（上記 f）を指定した場合は、プログラム内のパッケージ名を変えることができる。
+ _をつけた場合は、インポートしたパッケージを使用しないことをコンパイラに伝えます。
Goではインポートしたパッケージを使用しないとコンパイルエラーになるため、_をつけることでエラーから回避できます。
