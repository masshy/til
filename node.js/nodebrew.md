# nodebrew

nodeのバージョン管理ツール。複数のバージョンを使い分けられる。

## 導入法

nodebrewをインストール。

```
$ brew install nodebrew
```

nodebrewが管理するバージョンを使うために.bash_profileに以下の文を追加。

```
export PATH=$HOME/.nodebrew/current/bin:$PATH
```

.bash_profile更新。

```
source .bash_profile
```

nodebrewで指定するバージョンのnodeをインストールする。
今回は安定版。
インストールする前に、ホームディレクトリに`.nodebrew/src`というディレクトリを作っておく。

```
$ mkdir ~/.nodebrew
$ mkdir ~/.nodebrew/src
$ nodebrew install-binary stable
```

このままではまだローカルのデフォルトのバージョンを指定しているので、`nodebrew use`でバージョンを指定する。

```
$ node use stable
use v6.5.0
```

これでnodebrewが管理するバージョンのnodeを使える。

```
$ node -v
v6.5.0
```
