# getsで標準入力とファイルから読み込む

```ruby
[ a.rb ]
while line = gets
  puts "!!!: #{line}"
end
```

```
[ b.txt ]
hello

world
```

## 標準入力から
```
cat b.txt | ruby a.rb
!!!: hello
!!!:
!!!: world
```

## 引数としてファイルを指定
```
ruby a.rb b.txt
!!!: hello
!!!:
!!!: world
```
- 引数として複数のファイルを渡せる。
  - ただし、引数としてはファイル名しか渡せない。
  - オプションは渡せない。

## 参考
http://atomic.jpn.ph/prog/io/filter.html
