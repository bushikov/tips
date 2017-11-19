# 定数の定義位置を調べる

定数に再代入し、その際のワーニングメッセージで確認する。

```
irb -r rake

Rake::Task = Rake::Task
(irb):1: warning: already initialized constant Rake::Task
/Users/ksss/.rbenv/versions/2.5.0-dev/lib/ruby/gems/2.5.0/gems/rake-12.0.0/lib/rake/task.rb:14: warning: previous definition of Task was here
=> Rake::Task
```

## 参照
https://qiita.com/ksss/items/377eef080909564e4a25
