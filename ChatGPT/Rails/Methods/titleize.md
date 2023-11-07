# titleizeメソッド

titleize メソッドはRailsによるStringクラスの拡張です。各単語の最初の文字を大文字にし、アンダースコアをスペースに置き換えることで、文字列をタイトルケースに変換します。

使用例:

```ruby
"tech_blog".titleize
# => "Tech Blog"
```

keys メソッドと組み合わせることで、フォームやビューで使用するためのモデル属性のユーザーフレンドリーな名前を作成するのに便利です。