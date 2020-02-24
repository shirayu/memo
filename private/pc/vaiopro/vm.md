

# 仮想マシン

仮想マシン上でWindowsを動かす．
P2Vという技術を使えばOEMのWindowsも使えるみたいだが，面倒だったので普通に新たにインストールする．


## インストール
- Intel CPUの仮想化機能をBIOSで有効にする
- 確認する
```
grep --color vmx /proc/cpuinfo
$ lsmod | grep kvm
kvm_intel             130584  0 
kvm                   380340  1 kvm_intel
```

- まずは関連パッケージをインストール
```
sudo aptitude install qemu-kvm libvirt-bin bridge-utils virt-manager
sudo adduser $USER libvirt
```

<!-- - ``/etc/libvirt/qemu.conf``に追記 -->
<!-- ``` -->
<!-- user = "yuta-h" -->
<!-- group = "yuta-h" -->
<!-- dynamic_ownership = 0 -->
<!-- ``` -->

- 再起動
- 任意の場所にイメージファイルを作成
```
qemu-img create -f qcow2 tamako.img 40G
```

```
sudo /etc/init.d/libvirt-bin restart
```

- 仮想マシンマネジャーでVM作成
- imageの所有権がyuta-hにあることを確認
    - なければ``chown``する
- netの起動 :[参考](http://cartesianproduct.wordpress.com/2011/07/31/kvm-starting-the-default-network/)
```
sudo virsh net-start default
sudo virsh net-autostart default
```

- VNCではなくspiceで接続
```
sudo aptitude install spice-client
```
- [参考](https://sites.google.com/site/hymd3a/linux/kvm-spice)
- Guset toolsのインストール

## フォルダ共有
sambaを使う．
ホスト側(debian)で
```
sudo aptitude install samba nautilus-share
sudo adduser yuta-h sambashare
```
その後，再起動．
(sambashareグループに追加したことを反映させるため)

共有したいフォルダで右クリックして設定する．
VM起動後，ネットワークからアクセスできるようになる．


## トラブル対処

### VMが起動できない(1)
```
libvirtError: unsupported configuration: hda-duplex not supported in this QEMU binary
```
と出た時は
```
sudo service libvirt-bin restart
```
する．

最近は，
```
sudo service libvirtd restart
```
になった模様．


もしくは，サウンドデバイスの設定を``ich6``から別のデバイスに変えてみる．

- [参考](http://kernhack.hatenablog.com/entry/2013/06/01/213141)

### VMが起動できない(2)
``apt-get upgrade``したら，
```
libvirtError: internal error Cannot find suitable CPU model for given data
```
と出て起動できなくなった．

```
sudo aptitude reinstall libvirt-bin
```
したら起動した．

これでダメだった場合，[ここ](https://bbs.archlinux.org/viewtopic.php?id=182142)の記述を参考に，
「仮想マシンマネージャー」を起動して「Processor -> CPU -> 構成 -> モデル」とたどっていき，
モデル欄を空欄にして保存すれば起動した．



### VMが起動できない(3)

```
仮想マシンの開始中にエラーが発生しました: Unable to open /dev/net/tun, is tun module loaded?: そのようなファイルやディレクトリはありません

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 96, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 117, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1160, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 917, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: Unable to open /dev/net/tun, is tun module loaded?: そのようなファイルやディレクトリはありません
```
と出て起動できなくなった．

```
sudo modprobe tun
```
したら起動した．

``/etc/modules``に``tun``と書いておく．

### 時刻がUTCになっている
```
sudo virsh edit palmwn
```
として，
```
<clock offset='utc'/>
```
を
```
<clock offset='localtime'/>
```
にしてから，
```
sudo virsh define /etc/libvirt/qemu/palmwin.xml
```
する


### インストール
Windowsのインストール後，Windows Updateしてから，
その他のソフトウェアのインストール．

- MS Office
- Dropbox
- lhaz
- VLゴシック，VLゴシックP
- Adobe reader
- Acrobat
- Google IME
    - キー設定
```
直接入力 -> Ctrl+Space -> IMEを有効化
入力文字なし -> Ctrl+Space -> IMEを無効化
```

## Links
- http://inokara.hateblo.jp/entry/2013/04/06/092700
- http://tuxtor.shekalug.org/kvm-qemu-could-not-open-disk-image-disk-0-permission-denied-en-opennebula-y-debian/


