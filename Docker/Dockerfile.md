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

ベースイメージで実行するコマンドを記述。貧弱なベース・イメージを強化したい時とか。

```
RUN apt-get install vim
RUN apt-get install curl
```

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