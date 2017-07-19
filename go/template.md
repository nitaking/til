## template

Go言語にはデフォルトのパッケージにテンプレート処理が含まれている。
- text/template
- html/template

## ソースコード中のテンプレート定義
`template.New`メソッドでテンプレート名を指定し、`template.Parse`メソッドでテンプレートの内容を読み込ませる。

`template.Must`メソッドで指定するテンプレートの正当性チェック。不正な場合はpanicとなる。

`template.Execute`メソッドに出力先と値を指定する

```.go
package main

import (
    "fmt"
    "os"
    "text/template"
)

type Member struct {
    Id   int
    Name string
    Tech string
}

func main() {
    const template_text = `初めてのテンプレート。名前は {{.Name}} です。`
    tpl := template.Must(template.New("mytemplate").Parse(template_text))
    member := Member{1, "ほげほげ", "Go"}

    if err := tpl.Execute(os.Stdout, member); err != nil {
        fmt.Println(err)
    }
}
```

実行結果
```.sh
初めてのテンプレート。名前は ほげほげ です。
```
