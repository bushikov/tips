# 配列の展開
```ruby
a, b = [ 1, 2, 3 ]
a                       # => 1
b                       # => 2
```

```ruby
a, b = 1, 2, 3
a                # => 1
b                # => 2
```

```ruby
a, *b = [ 1, 2, 3, 4, 5 ]
a                          # => 1
b                          # => [ 2, 3, 4, 5 ]
```

```ruby
a, *b = 1, 2, 3, 4, 5
a                      # => 1
b                      # => [ 2, 3, 4, 5 ]
```

```ruby
a, b = *[ 1, 2, 3, 4, 5]
a                         # => 1
b                         # => 2
```

```ruby
def method( a, b, c )
  "#{ a }:#{ b }: #{ c }"
end
ar = [ 1, 2, 3 ]
method( *ar )                # => "1:2:3"
method( *[ 1, 2, 3 ] )       # => "1:2:3"
```

```ruby
def method( a, b )
  [ a, b ]
end
z, y = *method( 1, 2 )
z                       # => 1
y                       # => 2
e, f = method( 3, 4 )
e                       # => 3
f                       # => 4
```
