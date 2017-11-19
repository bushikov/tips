# 継承階層のどこでメソッドが定義されているかを調べる

```ruby
class Module
  def ancestores_that_implement_instance_method( method )
    ancestors.find_all do | ancestor |
      ( ancestor.instance_methods( false ) + ancestore.private_instance_methods( false ) ).include?( method )
    end
  end
end

HomeController.ancestores_that_implement_instance_method( :method_a )
=> [ FooController::Rendering, BarController::Rendering ]
```

## 参照

http://qiita.com/ngtk/items/cd406961cf62531a81c5
