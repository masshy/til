#Dockerfile まとめ

Dockerfileの書き方まとめ

## EXPOSE命令

起動時にコンテナ側でリッスンするポートを指定する。
コンテナの実行時、ポートが割り当てられる。
```
EXPOSE 80 443
```

## VOLUME命令

ボリュームのマウント・ポイントを作成する。

```
$ VOLUME /myvol
```

複数ボリュームの場合。

```
$ VOLUME /www/website1.com /www/website2.com

```

JSON 形式での場合。

```
$ VOLUME [“myvol”, “myvol2”]
```

ホスト側ディレクトリをボリューム割り当てできない。