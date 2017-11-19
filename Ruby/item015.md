# Csv.tableの使い方

```
[ data.csv ]
a,b,c
A,B,C
1,2,3
```
```
csv_data = CSV.table( "data.csv" )
headers  = csv_data.headers          # => [ "a", "b", "c" ]
csv_data.each do | row |
  headers.eash do | header |
    print row[ header ]              # <= ヘッダでアクセスできる
  end
  puts
end
=> A, B, C
=> 1, 2, 3
```

## 参考
http://melborne.github.io/2013/01/24/csv-table-method-is-awesome/
