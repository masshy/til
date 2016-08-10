
# Docker

## なぜDockerを使うのか

* 資源を使い回すので少ないメモリやディスクを節約できる
* 資源を使い回すので起動が早い
* 同じ環境を簡単にたくさん作れる
* 複数人で同じ環境をローカルで使える
* 動作確認ができたイメージをSTGや本番にそのまま持っていける



## インストールと設定

### docker-toolboxインストール

docker-toolboxをインストール。GUIに沿うだけ。

https://www.docker.com/products/docker-toolbox

### VM環境作成

docker-toolboxのインストール完了後、一発目に打つコマンド。
```
$ docker-machine create --driver virtualbox test
```
今回はVirtualboxでtestという名の仮想環境を作成した。dockerを初めて使う現段階では環境変数が設定されてないため、次のコマンドを打つ。

```
$ eval "$(docker-machine env test)"
```

これでdockerコマンドが使えるようになる。(参考URL:http://yamitzky.hatenablog.com/entry/2015/12/24/113007)

コンテナを実行する。

```
$ docker run centos:6.6 echo hello world
```
OSはCentOS6.6を指定し、コンテナ内で`echo`を実行する。

指定されたOSイメージが無ければインストールを行いコンテナを作成。最後に

```
hello world
```

が出力される。




## コンテナでコンソール操作

```
$ docker run --rm -it centos:6.6 /bin/bash
```
でコンテナ内に入れる。

--rm をつけるとコンテナが停止したときに削除する。

-i コンテナのSTDINにアタッチメントする（ターミナルの操作をするために必要）。

-t 擬似ターミナルを割り当てる（SSHで接続するために必要）。

これでコンテナ内でコマンドが打てるようになる。

コンテナから出る場合は```exit```。

## コンテナやイメージを削除

### イメージ削除

イメージ一覧を表示する。

```
$ docker images
```

削除したいイメージのIMAGE IDを取得。

```
$ docker rmi <IMAGE ID>
```

で削除できる。

### コンテナ削除

コンテナ一覧を表示する。

```
$ docker ps -a
```
で削除したいコンテナのCONTAINER IDを取得。

```
$ docker rm <CONTAINER ID>
```
で削除できる。

## 仮想環境の停止と起動

Virtualbox上のdocker仮想環境testを停止するコマンド。

```
$ docker-machine stop test
```
stopするだけ。起動はstartするだけ。

```
$ docker-machine start test
```



## Docker hubにpushできない

Docker hubにpushしたいけどできない。`docker login`もやった、repository名も合ってる。なのに`docker push`すると`Repository does not exist:`なんて言われる時。

repository名とimageidが紐付いていないのが原因。以下のコマンドで紐付ける。

```
$ docker tag <imageid> <repository>
$ docker push <repository>
```

`<repository>`はタグ部分含め、揃えるのを忘れずに。

(参考URL:http://qiita.com/ms2sato/items/237df26895707a8192cd)

## 




