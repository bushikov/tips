# 定数参照

```ruby
module Mod
  ABC = 1
end

module Mod
  class Alass
    def self.meth
      puts ABC
    end
  end
end

class Mod::Blass
  def self.meth
    puts ABC
  end
end

class Mod::Dlass
  def self.meth
    puts Mod::ABC
  end
end

Mod::Alass.meth
1

Mod::Blass.meth
NameError

Mod::Dlass.meth
1
```
