

# インストール

- 2015年7月現在，このmacbookは新しいハードウェアを積んでいるので，今のdebian OSでは動かないものがある
- 幸い有志がパッチを公開してくれているので，それを使うことにする
- そのうち，パッチが取り込まれて，以下のような面倒な手順を踏まずとも，普通にdebianを入れるだけで，問題なく使えるようになると思う

## 方針
- Debianのtestingをインストールする
- リカバリ領域やMacは消さない

## Macでの設定
- まずは普通にMacの初期設定を済ませる
- 以下のコマンドを複数回入力して，起動音（ジャーン）を消す
    - ``sudo nvram SystemAudioVolume=%00``
- ディスクユーティリティを開き，パーティションをリサイズする
    - Macの領域を45GBに縮小した
- [rEFInd](http://www.rodsbooks.com/refind/)をインストールする（ブートマネージャ）
    - rEFItはメンテされてなくて，最近はrEFIndの開発が主流
    - zipをダウンロード・解凍して，``./install.sh --alldrivers``

## debianのインストール
- USBでLANケーブルをつなげ，ネットワークにつなげておいた
- 普通にインストールを進めていく
- パーティションの設定に注意（MacOSの領域を消さないように）
- grubがインストールできないので，スキップした
- インストールが終われば再起動
- この段階では，debianは認識されない
- Macを起動してもう一度``./install.sh --alldrivers``
- refind.confを編集して，timeoutを設定した

## debianの設定 (wifi)
- まずはwifiを有効にしたい
- testingで入ったlinux kernelは3.16.0-4だったが，wifiはlinux kernel 3.19以降でないと使えないらしい
<!-- - 自分でkernelをコンパイルするのは面倒なので，[kernel-ppa](http://kernel.ubuntu.com/~kernel-ppa/mainline/)にあるdebを使うことにする -->
<!-- - とりあえず4.0.0-2を[ダウンロードして](https://packages.debian.org/sid/amd64/linux-image-4.0.0-2-amd64/download)インストール -->
- unstableから借りる
```
su
vi /etc/apt/apt.conf.d/99target #新規作成する
    APT::Default-Release "testing"; 
vi /etc/apt/sources.lists #追記する
    deb http://ftp.jp.debian.org/debian unstable main contrib non-free
    deb-src http://ftp.jp.debian.org/debian unstable main contrib non-free
apt-get update
apt-get install linux-image-4.0.0-2-amd/unstable linux-headers-4.0.0-2-amd/unstable
wget -O /lib/firmware/brcm/brcmfmac43602-pcie.bin https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/brcm/brcmfmac43602-pcie.bin
```

- リブートし，起動時にこのカーネルを選択したら，wifiの使えるdebian環境が手に入る
<!-- - ただしarch wikiによると，不安定なことがあるので，別のkernelの方がよいかも -->

## タッチパッドの設定
- このタッチパッド(05ac:0273)は，現在のbcm5974ドライバでは右クリックができない
- しかし，[ここ](https://bugzilla.kernel.org/show_bug.cgi?id=96771)にあるパッチを適用すれば動く
    - [パッチ](https://bugzilla.kernel.org/attachment.cgi?id=181421)をダウンロードする
        - なお[linux kernel 4.2-rc5で修正済](https://bugzilla.kernel.org/show_bug.cgi?id=96771#c62)
    - [bcm5974.c](https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/plain/drivers/input/mouse/bcm5974.c?id=refs/tags/v4.0.7)をダウンロードする
    - パッチを適用してbcm5974.cを得る
    - [Makefile](https://gist.github.com/anonymous/f414fc8ae93b7121187d)をダウンロードする
    - makeしてmake installする
    - ``rmmod bcm5974; rmmod usbhid; modprobe bcm5974; modprobe usbhid;``
    - ``updade-initramgs -u``
- 時々起動後右クリックが反応しないことがある
    - ``rmmod bcm5974; rmmod usbhid; modprobe bcm5974; modprobe usbhid;``を動かせばよい
- キーボードの「1」の隣の`````と``~``が``<``と``>``になってしまう
    - とりあえず``xmodmap -e 'keycode  94 = grave asciitilde'``で対処
```
cd
vi .xsession
    xmodmap ~/.xmodmap
chmod +x .xsession
vi .xmodmap
    keycode  94 = grave asciitilde
```

## ブートオプションの設定
- debian上で，refindのバイナリをダウンロードしてunzip
- ``sudo ./mkrlconf.sh``すると``/boot/refind_linux.conf``ができる
- ``/boot/refind_linux.conf``を編集する


# Links

- [「rEFInd」でOptionキーを押さずにブートセレクタを起動する](http://blog.mamohacy.tribrid-jp.com/article/353976413.html)

### その他
- [Installing and running Arch linux on the new MacBook 2015](https://bbs.archlinux.org/viewtopic.php?id=195924)
- [How to enable touchpad scrolling and tapping in Debian Wheezy KDE?](http://unix.stackexchange.com/questions/107532/how-to-enable-touchpad-scrolling-and-tapping-in-debian-wheezy-kde)
- [MacBookに入れたUbuntuの設定メモ その1](http://blog.goo.ne.jp/impreza98/e/abac46b4bfb5c9f91a8f71482dce956d)

- [MacbookPro12,1 (Early 2015) touchpad is not fully functional](https://bugzilla.kernel.org/show_bug.cgi?id=96771)
    - https://github.com/SicVolo/hid-apple-3.19
    - https://github.com/SicVolo/bcm5974-3.19
    - https://github.com/SicVolo/hid-apple-4.00
    - https://github.com/SicVolo/bcm5974-4.00
- [Debian Jessie and MacBookPro 13 (2015/12,1) with Kernel 4](https://blog.deimos.fr/2015/04/28/debian-jessie-and-macbookpro-13-2015121-with-kernel-4/)
- [arch wiki](https://wiki.archlinux.org/index.php/MacBook#Early_2015_13.22.2F15.22_-_Version_12.2Cx)

- [Mac OSなしでWindowsとArchLinuxをデュアルブートしてみた](http://tagussan.rdy.jp/blog/archives/542)
- [Debianでtestingやunstableからパッケージを借りる時の手順](http://kotak.hatenablog.com/entry/2014/06/19/181942)

