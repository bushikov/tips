# インストール

## 必要なパッケージのインストール

### Ubuntu
git
```
sudo apt-get update
sudo apt-get install git
```

Rubyのインストールに必要なパッケージ
```
sudo apt-get update
sudo apt-get install -y libssl-dev libreadline-dev alib1g-dev
```

### CentOS
git
```
sudo yum install -y curl-devel expat-devel gettext-devel openssl-devel zlib-devel
sudo yum install -y perl-ExtUtils-MakeMaker

curl -L -O https://www.kernel.org/pub/software/scm/git/git-2.9.5.tar.gz
tar -zxf git-2.9.5.tar.gz
cd git-2.9.5
make prefix=/usr/local all
make prefix=/usr/local install
```

Rubyのインストールに必要なパッケージ
```
sudo yum install -y openssl-devel readline-devel zlib-devel
```

## rbenvのインストール
```
git clone https://github.com/rbenv/rbenv.git /home/<user>/.rbenv
git clone https://github.com/rbenv/ruby-build.git /home/<user>/.rbenv/plugins/ruby-build
echo 'export PATH="/home/<user>/.rbenv/bin:$PATH"' >> /home/<user>/.bashrc
chown -R <group>:<user> /home/<user>/.rbenv
echo 'eval "$(rbenv init -)"' >> /home/<user>/.bashrc
source /home/<user>/.bashrc
```

## Rubyインストール
```
rbenv install 2.4.3
```
