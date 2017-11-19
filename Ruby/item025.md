# ruby.exeにスクリプトファイルとして渡された場合のみ実行する

```ruby
if $0 == __FILE__
  ...
end
```
