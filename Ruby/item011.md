# メソッドの引数が、nil, [], [nil], 与えられなかった場合の判定
```ruby
def method( *args )
  if args.flatten.compact.empty?
    # nil, [], no argumentの場合のロジック
  end
end
```
