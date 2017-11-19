# 特異クラスはClassクラスのインスタンス

```ruby
class Klass; end

Klass.new.singleton_class.class
--> Class
```
