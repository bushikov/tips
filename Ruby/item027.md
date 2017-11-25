# クラス変数と継承

継承先クラスとそのオブジェクトとも共有できる（されてしまう）
```ruby
class Alass
  @@val = "HELLO"
  def self.change( a )
    @@val = a
  end
end

class Blass < Alass
  def out_in_method
    @@val
  end
  def self.out_in_classmethod
    @@val
  end
end

class Dlass < Alass
  def out_in_method
    @@val
  end
  def self.out_in_classmethod
    @@val
  end
end

b = Blass.new
d = Dlass.new

b.out_in_method
HELLO
d.out_in_method
HELLO
Blass.out_in_classmethod
HELLO
Dlass.out_in_classmethod
HELLO

Alass.change( "GOOD BYE" )
b.out_in_method
GOOD BYE
d.out_in_method
GOOD BYE
Blass.out_in_classmethod
GOOD BYE
Dlass.out_in_classmethod
GOOD BYE
```
