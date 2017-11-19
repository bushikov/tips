# DSLの作り方

```ruby
class DSL
  def initialize( path )
    File.open( path ) do | f |
      instance_eval( f.read )
    end
  end

  def meth
    puts "meth"
  end

  def meth2( arg )
    puts "meth2:#{ arg }"
  end

  def meth_alass( &block )
    @val = Alass.new
    @val.instance_eval( &block )    # これをすると渡すファイル内のmeth_allass内で
                                    # レシーバなしでAlassのインスタンスメソッドが使える。
                                    # attr_accessorだけではwriterメソッドは使えない。
  end

  def meth_alass_output
    @val.output
  end

  def meth_blass
    @val2 = Blass.new
    yield @val2
  end
end

class Alass
  def register( value )
    @value = value
  end
  def output
    @value
  end
end

class Blass
  def register( value )
    @value = value
  end
end
```
  - DSL

渡すファイル
```
meth
meth2( "HELLO" )
meth_alass do
  register( "HELLO" )
end
meth_blass do | o |
  o.register( "HELLO" )
end
```
