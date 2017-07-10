## 配列

+ Goの配列は固定長。
+ 可変長配列は後述するスライスがそれにあたる。

```.go
var arr [4]string
```

配列は、他の言語と同じように添字でアクセスする

```.go
var arr [4]string
arr[0] = "a"
arr[1] = "b"
arr[2] = "c"
arr[3] = "d"
```

宣言と同時に初期化することも可能。

その場合は[...]を用いることで必要な配列の長さを暗黙的に指定できます。

```.go
arr := [4]string{"a","b","c","d"}
arr := [...]string{"a","b","c","d"}
```

配列の型は長さも情報として含む。

例）関数fnは[4]string型を引数にとる。

型の異なる[5]string型を渡すとコンパイルエラーとなる。

## スライス
スライスは可変長配列として扱うことができる


### スライスの宣言

```.go
var s []string
```

スライスには配列のような長さの情報はない。

初期化を同時に行う場合は配列と同じように書くことができる。

```.go
s := []string{"a","b","c","d"}
fmt.Println(s[0]) // "a"
```

### append()

* スライスの末尾に値を追加する場合はappend()を使用する。
* append()はスライスの末尾に値を追加し、その結果を返す組込み関数。

```.go
var s []string
s = append(s, "a") //追加した結果を返す
s = append(s, "b")
s = append(s, "c")
fmt.Println(s) // [a b c d]
```


次のように指定すれば，スライスに別のスライスの中身を展開して追加することもできます。

```.go
s1 := []string{"a", "b"}
s2 := []string{"c", "d"}
s1 = append(s1, s2...) // s1にs2を追加
fmt.Println(s1)        // [a b c d]
```

### range
先頭から順番に処理するような場合は添字によるアクセスの代わりにrangeを使用できる。

```.go
var arr [4]string

arr[0] = "a"
arr[1] = "b"
arr[2] = "c"
arr[3] = "d"

for i, s := range arr {
    // i = 添字, s = 値
    fmt.Println(i, s)
}
```

実行結果
```.sh
$ go run range.go
0 a
1 b
2 c
3 d
```
