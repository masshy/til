# Apache

Webサーバ。

## インストールと設定

テキストではソースコードから入れるが、ここではyumからの導入方法を記述する。

```
$ sudo yum update
$ sudo yum install -y httpd
```

自動起動設定。

```
$ sudo chkconfig httpd on
```

確認。


## Apach導入時に発生したエラーとか


Apach 2.4で　./configure --prefix=/usr/local/apache --enable-so --enable-ssl --enable-rewrite　するとエラーが発生する

```
$ sudo ./configure --prefix=/usr/local/apache --enable-so --enable-ssl --enable-rewrite
checking for chosen layout... Apache
checking for working mkdir -p... yes
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
configure:
configure: Configuring Apache Portable Runtime library...
configure:
checking for APR... no
configure: error: APR not found.  Please read the documentation.

```

APRが無いということなので、http://apr.apache.org/download.cgiより`apr`と`apr-util`を入れる。



改めて`./configure`すると

```
checking for pcre-config... false
configure: error: pcre-config for libpcre not found. PCRE is required and available from http://pcre.org/
```
というエラーが。

```
$ sudo yum install pcre-devel
```
をして、再度./configureすると成功した。

