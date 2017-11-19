# （定義中ではなく）処理中にオブジェクトにメソッドを追加する
その１、その２ともに、追加メソッド（make_method）を呼んだレシーバのみ追加される。

その３は、追加メソッドを呼んだレシーバのクラスに追加するので、同じクラスのオブジェクト全体で追加される。

## その１
```ruby
Mod = Module.new do
  define_method( :meth ) do | *args, &blk |
    ...
  end
end

obj.extend( Mod )
```

### 使用例
メソッドを動的に追加するメソッドをもつクラス。
```ruby
class Alass
  def make_method( name )
    mod = Module.new{
      define_method( name ) do | *args, &blk |
        ...
      end
    }
    extend( mod )
  end
end
```

### 理由
define_methodはオブジェクトのインスタンスメソッド中では使えない。

## その２
```ruby
class Alass
  def make_method( a )
    define_singleton_method( a ) do | *args, &blk |
      ...
    end
  end
end
```

## その３
```ruby
class Alass
  def make_method( a )
    mode = Module.new{
          define_method( a ) do | *args, &blk |
            ...
          end
        }
    self.class.include( mod )
  end
end
```
