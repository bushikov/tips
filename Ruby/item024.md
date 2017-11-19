# スクリプトと読み込むファイルのエンコーディングが違う場合

Eオプション
- -E<external>:<internal>
  - external：読み込むファイルのエンコーディングを指定。
  - internal：スクリプトファイルのエンコーディングを指定。
    - 省略できるっぽい。

```
ruby -Eutf-8 abc.rb
```
- 読み込むファイルのエンコーディングがutf-8でabc.rbがshift-JISなどの場合、有効となる。

File.openのオプション
  - 第２引数にエンコーディングを指定する

```
File.open('hoge.txt', 'r:utf-8')
```
