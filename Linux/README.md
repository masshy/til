## OSの種類を調べる
`docker run java`とかしたらベースに何が入るかわからないから。

```
$ cat /proc/version
```

または

```
$ uname -a
```
でカーネルのバージョンがわかる。

## バージョンを調べる

### Debian系
```
$ cat /etc/debian_version
```

### RedHat系
```
$ cat /etc/redhat-release
```

### Fedora
```
$ cat /etc/fedora-release
```

参考URL:http://qiita.com/ritukiii/items/60a3ac4734fc52748cee
