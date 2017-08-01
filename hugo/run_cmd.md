# hugoコマンド

## server
serverモードで起動することでブラウザでテストすることができる。

```.sh
$ hugo server
```

### -w or -watch=true
-wをつける事でライブリロードが有効に。
```
hugo server -w
```

### -t または –theme=テーマ名

git cloneしたテーマを反映するためのオプション。
```
hugo server -t
```

### -D または –buildDrafts=true

知っていないとハマる。
draft=trueの場合、下書き設定が有効になってしまい、ブラウザで確認することができない。

```
hugo server -w -D
```
