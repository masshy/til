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
