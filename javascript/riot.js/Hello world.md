## hello world
htmlから用意。

```.html
<!DOCTYPE html>
<html lang="ja">
    <head>
        <title>Riot.js入門</title>
    </head>
    <body>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/riot/2.6.2/riot+compiler.min.js"></script>
    </body>
</html>
```

## コンポーネントの作成と読み込み
以下のように .tagファイル を新たに作成し、中にHTMLの要領で <ファイル名></ファイル名> のタグから始まるコードを記述します。

```.html
<sample>
    <h1>hello world</h1>
</sample>
```
これをindex.htmlに `<script src="sample.tag" type="riot/tag"></script>` と記述して読み込ませます。

この時に気をつけるのは `type="riot/tag` と忘れず記述すること。そうすることでコンパイラーが自動的に「これはRiotのファイルだな」と識別してくれます。
