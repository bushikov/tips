# instance_eval( instance_exec )のコンテキスト
レシーバを指定せずにinstance_evalを呼び出すと、渡されたブロック（や文字列）は、instance_evalが呼び出されたコンテキストで実行される。

```ruby
class Klass
  def meth( &block )
    instance_eval &block
  end
  def meth2
    meth do
      puts self
    end
  end
end

Klass.new.meth2
#<Klass:...>
```

レシーバを指定してinstance_evalを呼び出すと、渡されたブロック（や文字列）は、instance_evalのレシーバのコンテキストで実行される。

```ruby
class Klass2
  def meth( &block )
    Klass.new.instance_eval &block
  end
  def meth2
    meth do
      puts self
    end
  end
end

Klass2.new.meth2
#<Klass2:...>
```
