#Docker コマンド　まとめ

## inspect

コンテナやイメージの情報を取得。

```
$ docker inspect <container id | image id>
```

keyで情報を絞り込む。

``` 
$ docker inspect <id> -f '{{json .<key>}}''
```


## Volume


新しいコンテナ上で、そのファイルシステムに`/myvolume`ディレクトリをマウント。

```
$ docker run -d -P -v /myvolume nginx:1.7 
```

複数のボリュームをマウントする場合、都度`-v`を付ける。

```
$ docker run -d -P -v /data/www -v /data/images nginx
```

ホスト上ディレクトリをマウントする。
```
$ docker run -v [ホスト側パス]:[コンテナ側パス]:[rw|ro]
```
`rw`または`ro`でボリュームの書き込み設定を制御。

ボリュームの削除。

```
docker rm -v <container id>
```
コンテナを削除してもボリュームは削除されない。

## コンテナ名

mynginx という名前のコンテナを作成。

```
$ docker run -d -P --name mynginx nginx
```

コンテナ名を `happy_einstein` から `mycontainer` に変更。

```
$ docker rename happy_einstein mycontainer
```
