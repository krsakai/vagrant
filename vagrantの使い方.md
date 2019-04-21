#### 参考リンク
https://qiita.com/kazokmr/items/dda3d6f5f3d03a8caf36

### 使い方
$ vagrant box add centos/6 
=> vagrant に box centos をダウンロードして追加

$ mkdir centos; cd centos
$ vagrant init centos/6
=> vagrantfile でVMを追加する設定ファイルを追加

$ vi Vagrantfile
```
# config.vm.network "private_network", ip: "192.168.33.10"
↓
config.vm.network "private_network", ip: "192.168.33.10"
```
に変更 (NAT + ホストマシン の NICを追加)

$ vagrant up			=> 起動
$ vagrant reload		=> 再起動
$ vagrant halt			=> 終了
$ vagrant suspend	=> 一時停止
$ vagrant destroy		=> 削除

$ vagrant ssh => sshログイン

#### プロビジョン (配備時の設定)
$ vi Vagrantfile
↓ を追加
config.vm.provision :shell, :path => "provision.sh" 
provision.sh に 起動時に実行したいコマンド記載
$ vagrant provision

#### Boxの作成 (現在の環境を保存=>複製)
○ Box化
$ vagrant package
$ vagarnt box add box名 package.box (パッケージされたbox)

○ Boxから起動
$ vagrant init box名

#### プラグイン (sahara バージョン管理)
$ vagrant plugin install sahara
$ vagrant sandbox on
$ vagrant sandbox rollback
$ vagrant sandbox commit
