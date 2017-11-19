# 動的にRegexpオブジェクトを作る

```ruby
ABC = { "A" => 1, "B" => 2, "C" => 3 }

Regexp.new( "#{ ABC.keys.join }" )       # <= 動的に作成する文字列を渡す！
regexp = /#{ ABC }/                      # <= //では式展開もできる！
```
