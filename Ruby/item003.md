# 循環参照

```ruby
# a.rb
require "b"
require "c"
puts "a"
```

```ruby
# b.rb
require "a"
require "c"
puts "b"
```

```ruby
# c.rb
puts "c"
```

```
ruby a.rb
c
a
b
a
```

requireされたファイルは、ファイル内容を読み込む前に、読み込み済みとされるっぽい。
