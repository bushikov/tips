# メソッドが定義されているソースを調べる

```
'123'.method( :to_i ).source_location
```

pryで、?や$を使う
```
[1] pry(main)> ? ''.blank?

From: /Users/me/.rbenv/versions/1.9.3-p194/lib/ruby/gems/1.9.1/gems/activesupport-3.2.6/lib/active_support/core_ext/object/blank.rb @ line 102:
Number of lines: 7
Owner: String
Visibility: public
Signature: blank?()

A string is blank if it's empty or contains whitespaces only:

  "".blank?                 # => true
  "   ".blank?              # => true
  "　".blank?               # => true
  " something here ".blank? # => false

[2] pry(main)> $ ''.blank?

From: /Users/me/.rbenv/versions/1.9.3-p194/lib/ruby/gems/1.9.1/gems/activesupport-3.2.6/lib/active_support/core_ext/object/blank.rb @ line 102:
Number of lines: 8
Owner: String
Visibility: public

def blank?
  # 1.8 does not takes [:space:] properly
  if encoding_aware?
    self !~ /[^[:space:]]/
  else
    self !~ NON_WHITESPACE_REGEXP
  end
end
```

## 参考
http://qiita.com/jnchito/items/fc8a61b421d026a23ffe
