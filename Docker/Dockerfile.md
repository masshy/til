#Dockerfile まとめ

Dockerfileの書き方まとめ


## Volume
記述例

```
$ VOLUME /myvol
```

複数ボリュームの例

```
$ VOLUME /www/website1.com /www/website2.com

```

JSON 形式での記述例
VOLUME [“myvol”, “myvol2”]