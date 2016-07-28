#Dockerfile まとめ

任意のディレクトリに作成。

```
$ docker build -t <REPOSITORY:TAG> <Dockerfile PATH>
```
でビルド。


## FROM命令

ベース・イメージに何を使うべきか指定。Dockerfileの最初に記述。

```
FROM ubuntu:14.04
```

## RUN命令

ベースイメージで実行するコマンドを記述。キャッシュをうまく活用する観点から扱いには注意が必要？

```
RUN apt-get install vim
RUN apt-get install curl
```

以前と順番が異なるだけで新たにコミットされるらしい。その場合キャッシュが使われない。新しいコマンドを追加する場合は一番下に記述する。
コマンドを`&&`でつなげれば余計なイメージ層を作らないですむ。

```
RUN apt-get install vim &&  apt-get install curl
```

## CMD命令

ビルド時（コンテナ作成時）に実行するコマンドを記述。

```
CMD ping 127.0.0.1 –c 30
CMD [“ping”, “127.0.0.1”, “-c”, “30”]
```

## ENTRYPOINT命令

コンテナを実行に実行されるコマンドを記述。

## EXPOSE命令

起動時にコンテナ側でリッスンするポートを指定する。
コンテナの実行時、ポートが割り当てられる。

```
EXPOSE 80 443
```

この場合、コンテナ側の80番と443番のポートが割り当てられる。

## VOLUME命令

ボリュームのマウント・ポイントを作成する。

```
VOLUME /myvol
```

複数ボリュームの場合。

```
VOLUME /www/website1.com /www/website2.com

```

JSON 形式での場合。

```
VOLUME [“myvol”, “myvol2”]
```

ホスト側ディレクトリをボリューム割り当てできない。