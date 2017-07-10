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

+ switch文に指定した値に一致するcaseが実行される。
+ どのcaseにも一致しなかった場合はdefaultが実行される。
+ カンマで区切った複数の値も指定できる。

### fallthrough
+ Goのswitchではcaseが実行されると次のcaseに実行が移ることなくswitch文が終了する。
+ caseの処理が終わった後に次のcaseに処理を進めたい場合は、case内にfallthroughを書くことで明示的に次のcaseに処理を進めることができる。
