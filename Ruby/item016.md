# HTTP経由でバイナリファイルをダウンロードする

その１
```ruby
require "open-uri"

open( "a.png", "wb" ){ | saved_file |
  open( "http://www.sample.com/x.png", "rb" ){ | read_file |
    saved_file.write( read_file.read )
  }
}
```
その２
```ruby
require "open-uri"

fetched_file = open( "http://www.sample.com/a.mp3", "rb" ).read
File.open( "a.mp3", "wb" ) do | file |
  file.write fetched_file
end
```

## 参考
https://www.xmisao.com/2014/03/29/how-to-download-a-binary-file-over-http-in-ruby.html
