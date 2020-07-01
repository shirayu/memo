
# Debianのインストール

## 方針

- Debianのtestingをインストールする
- リカバリ領域やwindowsは消さない

## 手順

### 前準備

- debian/testingのインストール用USBを用意しておく
- 無線LAN関係のdebパッケージをダンロードしてきてUSBメモリに入れる
    - ``firmware-iwlwifi``
    - ``firmware-linux``

### BIOSの設定

- secure boot無効
- intel vt有効

### windowsの初期設定

- ライセンスに同意し，必要事項を入力して，普通に起動できるようにする
- デスクトップを表示する
- 「ディスク管理」を起動してCドライブを縮小する
    - 40GBにした．
    - 処理はすぐに終わる
- シャットダウンする

### debianのインストール

- インストール用USBを挿入
- 普通にインストールを進めていく
    - ネットワークカードは無し
    - パーティションの設定に注意
- インストールが終われば再起動

### EFIの設定

- 起動後windowsが立ち上がる
- コマンドラインを管理者権限で開いて

```sh
Bcdedit /set {bootmgr} path \EFI\debian\grubx64.efi
```

と打つ

- 再起動するとgrub2の画面が出てくる

### grub2の設定

- そのまま起動すると異常に起動に時間がかかる
- 「ncq」の問題
- [ここ](http://marigold.sakura.ne.jp/linux/vaio_pro_13/index.html)にあるように，``linux``行に

```txt
libata.force=noncq
```

を追記する

```txt
noquiet
```

も書いておくと吉．

- ログインして，``/etc/default/grub``の編集

```sh
$ sudo vi /etc/default/grub
    (before) GRUB_CMDLINE_LINUX_DEFAULT="quiet"
    (after) GRUB_CMDLINE_LINUX_DEFAULT="noquiet libata.force=noncq"
$ sudo update-grub
```

- debianが起動する
- 日本語フォントが文字化けして読めない
- インターネットに接続する
    - USB等で有線LANに接続する
    - または以下の「無線LANの有効化」を行う
- 「ctrl+Alt+F3」でコマンドラインを表示
- rootでログイン

```sh
aptitude install gdm3 gnome3-session gnome
   (gdm3を選択する)
aptitude install fonts-takao fonts-vlgothic task-japanese-gnome-desktop
```

- 再起動
- 無事に文字化けしないログイン画面が出てくる

### 無線LANの有効化

- ログインする
- ターミナルを起動し，``export LANG=C``する
- debパッケージをインストールする

```sh
sudo dpkg -i firmware-iwlwifi_0.41_all.deb
sudo dpkg -i firmware-linux-free_3.3_all.deb
sudo mdprobe firmware-iwlwifi_0.41_all.deb
sudo modprobe firmware-iwlwifi_0.41_all.deb
```

- ``nm-connection-editor``で無線LANの設定を行う
- 再起動

### その他のインストール

- 無線LANを有効にして，接続できたらその他のインストール

```sh
# vi /etc/apt/sources.list
# cat /etc/apt/sources.list (編集後の内容)
    #deb cdrom:[Debian GNU/Linux testing _Jessie_ - Official Snapshot amd64 CD Binary-1 20140317-06:12]/ jessie main
    #deb cdrom:[Debian GNU/Linux testing _Jessie_ - Official Snapshot amd64 CD Binary-1 20140317-06:12]/ jessie main
    deb http://ftp.nara.wide.ad.jp/debian/ jessie main contrib non-free
    deb-src http://ftp.nara.wide.ad.jp/debian/ jessie main contrib non-free
    deb http://security.debian.org/ jessie/updates main contrib non-free
    deb-src http://security.debian.org/ jessie/updates main contrib non-free
    # jessie-updates, previously known as 'volatile'
    deb http://ftp.nara.wide.ad.jp/debian/ jessie-updates main contrib non-free
    deb-src http://ftp.nara.wide.ad.jp/debian/ jessie-updates main contrib non-free
    # jessie-backports, previously on backports.debian.org
    deb http://ftp.nara.wide.ad.jp/debian/ jessie-backports main contrib non-free
    deb-src http://ftp.nara.wide.ad.jp/debian/ jessie-backports main contrib non-free
# aptitude update
# aptitude safe-upgrade
# aptitude install fonts-takao
# aptitude install gnome task-japanese-gnome-desktop
```

## レスキューモード

何らかの原因でefiがdebianのものじゃなくなってしまったとき，USBのdebianのレスキューモードを使って復旧する

(例)

- USBを刺す
- アシストボタンを押して起動し，USBから起動させる
- debian
    - advanced options -> rescue modeに移動
    - eボタンでlinux行に``libata.force=noncq``を追記
    - F10でブート
    - しばらく待ち，言語やキーボードの選択を(グラフィカルに)行う
    - ルートをマウンド(例: sda7)

```sh
mount /dev/sda3 /boot/efi
cd /boot/efi/EFI/Microsoft/Boot
cp bootmgfw.efi bootmgfw.efi.orig
cp ../../debian/grubx64.efi bootmgfw.efi
```

```sh
grub-install
update-grub
```

[参考](http://pcdennokan.dip.jp/site/hardware/vaiopro11_debian/)
