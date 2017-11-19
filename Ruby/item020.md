# do ... end、{}、&Procオブジェクトのメソッドとの結合度

{}の方がより近くのメソッドに結合する。

```ruby
def meth1( a )
  puts "a:#{a}"
  yield if block_given?
end
def meth2
  1
end

meth1 meth2 { puts "outer" }          # ブロックはmeth2に渡される。
a:1

meth1 meth2 do puts "outer"; end      # ブロックはmeth1に渡される。
a:1                                   # meth2は引数とみなされる。
outer

meth1( meth2 ){ puts "outer" }        # ブロックはmeth1に渡される。
a:1
outer

bl = Proc.new{ puts "outer" }
meth1 meth2 &bl                       # ブロックはmeth2に渡される。
a:1

meth1( meth2 ) &bl                    # meth1が通常の引数を受け取るメソッドの場合、
a:1                                   # ブロックは無視される、かつ、block_given?はfalseになる。
=> false

meth1 meth2(), &bl                    # ブロックはmeth1に渡される。
a:1
outer
```
