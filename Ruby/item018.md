# return, break, nextとProc, lambda, block

## 1. Proc
### 1.1 return
```ruby
def meth
  Proc.new{ return 1; puts 2 }.call
  'bbb'
end
meth
=> 1
```
  - メソッドを抜ける。
    - トップレベルだとエラー(LocalJumpError)となる。
  - returnへ渡した値は、メソッドの戻り値となる。

### 1.2 break
```ruby
def meth
  Proc.new{ break 1; puts 2 }.call
  'bbb'
end
meth
=> LocalJumpError ...
```
  - エラー(LocalJumpError)となる。

### 1.3 next
```ruby
Proc.new{ next 1; puts 2 }.call
=> 1

def meth
  Proc.new{ next 1; puts 2 }.call
  'bbb'
end
meth
=> 'bbb'
```
  - Procオブジェクトのcallを抜ける。
  - nextへ渡した値は、Procのcallの戻り値となる。

---

## 2. lambda
### 2.1 return
```ruby
lambda{ return 1; puts 2 }.call
=> 1

def meth
  lambda{ return 1; puts 2 }.call
  'b'
end
meth
=> 'b'
```
  - lambdaオブジェクトのcallを抜ける。
  - returnへ渡した値は、lambdaのcallの戻り値となる。

### 2.2 break
```ruby
lambda{ break 1; puts 2 }.call
=> 1

def meth
  lambda{ break 1; puts 2 }.call
  'b'
end
meth
=> 'b'
```
  - lambdaオブジェクトのcallを抜ける。
  - breakへ渡した値は、lambdaのcallの戻り値となる。

### 2.3 next
```ruby
lambda{ next 1; puts 2 }.call
=> 1

def meth
  lambda{ next 1; puts 2 }.call
  'b'
end
meth
=> 'b'
```
  - lambdaオブジェクトのcallを抜ける。
  - nextへ渡した値は、lambdaのcallの戻り値となる。

---

## 3. block
### 3.1 return
- エラー(LocalJumpError)となる。

### 3.2 break
```ruby
def meth
  a = yield
  puts a
  'b'
end
meth{ break 1; puts 'c' }
=> 1
```
  - メソッドを抜ける。
    - block単独だとエラー(SyntaxError)となる。
  - breakへ渡した値が、メソッドの戻り値となる。

### 3.3 next
```ruby
def meth
  a = yield
  puts a
  'b'
end
meth{ next 1; puts 'c' }
1
=> 'b'
```
  - blockを抜ける。
  - nextへ渡した値がyieldに返される。
