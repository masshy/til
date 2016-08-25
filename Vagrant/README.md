# Vagrant

こいつだけでVirtualBoxに仮想環境を構築し、また環境設定や起動・停止・削除といった操作をコマンドで行える。

## インストールと設定

### VirtualBox
 https://www.virtualbox.org/wiki/Downloads からインストール。2016/07/25現在、使用するバージョンは5.0.16。インストールウィザードに従うだけ。

### Vagrant
http://www.vagrantup.com/downloads.html からインストール。2016/07/25現在、使用するバージョンは1.8.5。インストールウィザードに従い、完了したらターミナルで
```
$ vagrant box add bento/centos-6.7
```
と入力。Boxファイルを取得。
```
1) parallels
2) virtualbox
3) vmware_desktop
```
とエミュレータを指定される。VirtualBoxなので2を入力。

Boxファイルが取得したら、Vagrantの設定ファイル等を入れるフォルダを作成し、そこでvagrantの初期化コマンドを実行。
```
$ mkdir centos67VM
$ cd centos67VM
$ vagrant init bento/centos-6.7
```
以下のコマンドで起動。
```
$ vagrant up
```

起動が確認できたら、Vagrantfile内の以下の行の#を消す。
```
# config.vm.network "private_network", ip: "192.168.33.10"
```
これでホストOSからのssh接続が可能になる。設定を反映するため
```
$ vagrant reload
```
でVagrantを再起動。

## トラブルシューティング

### default: Warning: Authentication failure. Retrying...が止まらない

正常な場合でも10回くらいは表示されるっぽいが、延々と終わらない場合。

公開鍵のパーミッションがおかしいと発生する。sshで仮想環境に接続し
```
$ chmod 600 /home/vagrant/.ssh/authorized_keys
```
のコマンドを実行した後、Vagrantを再起動。


### 割り振ったIPアドレスが反映されないとき

```
$ vagrant reload
==> default: You assigned a static IP ending in ".1" to this machine.
==> default: This is very often used by the router and can cause the
==> default: network to not work properly. If the network doesn't work
==> default: properly, try changing this IP.
```
末尾1のIPアドレスが割り振られた場合に起こるそう。末尾1のIPアドレスは仮想環境から見たホストOSとして決まっているそう。
