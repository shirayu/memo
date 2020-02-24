
# debian on H170-PRO

## BIOSの設定

- 時刻の設定
- secure bootを無効にする
  - ``secure boot: enable``となっている
  - 鍵をすべて消すと``secure boot: disable``となる
- intel vtを有効にする

## インストール

- debian testingを[入手](http://cdimage.debian.org/cdimage/weekly-builds/amd64/)してインストールを進める
- 普通にインストールを進めていく
- デスクトップ環境はgnomeではなくcinamoneを選ぶ
- インストールが終われば再起動

## レポジトリの設定

- ``sudoedit /etc/apt/sources.list``
- 以下のように編集

```apt
deb http://debian-mirror.sakura.ne.jp/debian/ stretch main  contrib non-free
deb-src http://debian-mirror.sakura.ne.jp/debian/ stretch main  contrib non-free

deb http://security.debian.org/debian-security stretch/updates main  contrib non-free
deb-src http://security.debian.org/debian-security stretch/updates main  contrib non-free

deb http://www.deb-multimedia.org stretch main non-free

#deb http://ftp.jp.debian.org/debian unstable main contrib non-free
#deb-src http://ftp.jp.debian.org/debian unstable main contrib non-free
```

- ``sudo aptitude update``
- ``sudo apt-get install deb-multimedia-keyring``
- ``sudo aptitude safe-upgrade``

## ファームウェア

- Debian 8では以下のように入れる

```sh
sudo aptitude install firmware firmware-linux-nonfree firmware-realtek
```

## その他設定

- 固定IPにする
- fstabの設定
- rsyncで古いディスクから色々コピー
- 節電設定
  - ``sudoedit /etc/hdparm.conf``
