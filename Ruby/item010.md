# Mix-inしたモジュールの優先度

## 1つのMix-in命令（include、prepend、extend）で複数のモジュールをMix-inする場合

先に指定したモジュールが優先される。

```
module Moda
  def meth
    p 'Mod-A'
  end
end

module Modb
  def meth
    p 'Mod-B'
  end
end

Class Alass
  include Moda, Modb
end

Alass.new.meth
Mod-A

Class Blass
  prepend Moda, Modb
end

Blass.new.meth
Mod-A

Class Dlass
  extend Moda, Modb
end

Dlass.meth
Mod-A
```

## 2つ以上のMix-in命令でモジュールをMix-inする場合

後で指定したモジュールが優先される。

```
module Moda
  def meth
    p 'Mod-A'
  end
end

module Modb
  def meth
    p 'Mod-B'
  end
end

Class Alass
  include Moda
  include Modb
end

Alass.new.meth
Mod-B

class Blass
  prepend Moda
  prepend Modb
end

Blass.new.meth
Mod-B

class Dlass
  extend Moda
  extend Modb
end

Dlass.meth
Mod-B
```
