# 概要

xxx

Java/Antを使ったCIのデモ

GitHubへのpush時に、 `.github/workflows/ant.yml` で定義したCIが実行される

より具体的には `$ ant run` を実行

この延長上で、`test` や `build` などのタスクを定義すれば、push や merge 時にそれらタスクを実行できる

フォーマッターを実行し、ステータスコードによって、コーディング規約を満たさない場合に、エラーとすることも可能

## デモ1

`.github/workflows/ant.yml` の `java-version:` のバージョンを11や17や21などにかえる。

CIは成功(グリーン)し、テスト結果のJavaのバージョンが適宜変わる

## デモ2

`src/com/example/HelloWorld.java` をコンパイルが失敗するようにわざと書き換える

CIは失敗する(レッド)

# 参考

- https://docs.github.com/ja/actions/use-cases-and-examples/building-and-testing/building-and-testing-java-with-ant
# java-maven-ci
