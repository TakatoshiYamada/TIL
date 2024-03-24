# uniqメソッド

uniq メソッドは、Rubyの配列に対して使用されます。
このメソッドは配列から重複する要素を取り除き、各要素がユニーク（一意）になるように新しい配列を返します。
元の配列は変更されません（破壊的ではありません）。

例えば：

```ruby
arr = [1, 2, 2, 3]
unique_arr = arr.uniq
puts unique_arr.inspect  # 出力: [1, 2, 3]
```

uniq! メソッドもあり、これは uniq の破壊的なバージョンです。
このメソッドは元の配列を変更し、重複がない状態にします。
もし元の配列に重複がない場合、nil を返します。

```ruby
arr = [1, 2, 2, 3]
arr.uniq!
puts arr.inspect  # 出力: [1, 2, 3]
```