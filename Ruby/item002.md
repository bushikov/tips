# defとdefine_methodの違い（フラットスコープ以外）

## 違い

defは、カレントクラス（カレントオブジェクト（=self）ではない）に対してメソッドを追加する。
  - 追加したメソッドは、そのクラスのインスタンスで使えるメソッド（インスタンスメソッド）となる。

define_methodは、カレントオブジェクトに対してメソッドを追加する。

- Moduleのプライベートメソッドなので、ModuleかClassの中でしか使えない。

## 例

メソッド：def
対象    ：レシーバの特異クラス

```
class Klass; end
Klass.instance_eval do
  def meth
    puts 'HELLO'
  end
end
Klass.meth
HELLO
Klass.new.meth
=> NoMethodError
```

メソッド：def
対象    ：レシーバ

```
class Klass; end
Klass.class_eval do
  def meth
    puts 'HELLO'
  end
end
Klass.meth
=> NoMethodError
Klass.new.meth
HELLO
```

メソッド：define_method
対象    ：レシーバ

```
class Klass; end
Klass.instance_eval do
  define_method :meth do
    puts 'HELLO'
  end
end
Klass.meth
=> NoMethodError
Klass.new.meth
HELLO
```

メソッド：define_method
対象    ：レシーバ

```
class Klass; end
Klass.class_eval do
  define_method :meth do
    puts 'HELLO'
  end
end
Klass.meth
--> NoMethodError
Klass.new.meth
HELLO
```
