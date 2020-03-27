# Debianのインストール


## 初期設定

- 電源管理->ディスプレイの電源を切るまでの時間: なし
- スクリーンセーバー無効

```sh
# rootになる
su

# sudo 追加
gpasswd -a yuta-h sudo

# mozc設定:  再起動必要
apt-get -y install fcitx-mozc aptitude
#GUIで変更
ptitude purge uim-mozc

# オートログインの設定
# https://yuji.noizumi.org/blog/2016/09/08/ubuntu-16-04%E3%81%AE%E8%87%AA%E5%8B%95%E3%83%AD%E3%82%B0%E3%82%A4%E3%83%B3%E3%81%8C%E5%8A%B9%E3%81%8B%E3%81%AA%E3%81%8F%E3%81%AA%E3%81%A3%E3%81%9F%E3%80%82/
groupadd -r autologin
gpasswd -a yuta-h autologin
```
- 再起動
- mozc設定
- 固定IP設定


## apt編集

```txt
deb http://www.deb-multimedia.org buster main non-free
```

```sh
sudo apt-get update
...
エラー:12 http://www.deb-multimedia.org buster InRelease
  公開鍵を利用できないため、以下の署名は検証できませんでした: NO_PUBKEY 5C808C2B65558117
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5C808C2B65558117
sudo apt-get dist-upgrade

# nonfreeインストール
sudo apt-get install amd64-microcode firmware-linux-nonfree firmware-realtek nvidia-driver
sudo reboot

# 最低限のソフトインストール
sudo apt install net-tools ssh rsync gnome-terminal dsh nkf curl mcomix pandoc \
    pandoc-citeproc pdfshuffler pdftk uuid-runtime gparted ntfs-3g ntp wdiff colordiff \
    peco nvtop jq zsh unzip unrar unar paco htop lv vim-nox tmux build-essential swig \
    autoconf automake libtool tinycdb libcdb-dev libncurses-dev aptitude git git-core \
    git-svn dkms vlc libdvdcss2 ffmpeg python3-pip seahorse wget cmake encfs \
    sqlite3 python3-gpg gnucash cpanminus libdbd-sqlite3 strace libusb-dev libusb-1.0-0-dev \
    virt-manager easytag android-tools-adb qrencode krita krita-l10n rtmpdump golang audacity asunder
sudo adduser $USER libvirt
sudo aptitude install parallel && mkdir ~/.parallel && touch ~/.parallel/will-cite
sudo update-alternatives --config editor #vim-noxを選択
pip3 install lxml tqdm selenium you-get youtube-dl gallery-dl gevent gevent-websocket websocket-client flake8 mypy isort autopep8

go get github.com/mattn/jvgrep
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

curl -sL https://deb.nodesource.com/setup_12.x | bash -
sudo apt-get install -y nodejs
npm install -g eslint esformatter typescript typescript-language-server
```

## 追加インストール
- google-chrome
- mendeley
- dropbox
    - 一度``rsync``してから実行
    - 競合を作らないように．完全に前のマシンのdropbox同期は止めておく


## その他の設定
### VLCの設定

- ``最近再生された項目を保存``を外す
- 「ビデオのサイズにインターフェースをリサイズ」をオフにする
- 「ビデオ」の設定で「スクリーンショットの形式」を``$N_$T_``にする
- スクリーンショットの保存先を変更
- オーバレイを無効
- 「ファイルマネージャーから起動された場合、単一インスタンスを実行」のチェックを外し，多重起動を有効にする
- ``ツール→インタフェースのカスタマイズ``で必要なボタンを配置

### GnuCash

```sh
sudo cpanm Finance::Quote
cd  /usr/share/perl5/Finance/
sudo wget https://raw.github.com/LiosK/Finance--Quote--YahooJapan/master/lib/Finance/Quote/YahooJapan.pm
```

### ほか
- [ターミナルの設定](https://zv-louis.hatenablog.com/entry/2018/05/28/120000)
```sh
 gsettings set org.gnome.Terminal.Legacy.Profile:/:0/ font "VL Gothic 14"
```
- 各種フォルダの名前を変更
    - ``LANG=C xdg-user-dirs-gtk-update``
- seahorseをインストールして，自動起動するようにする．
- 日付アプレットの書式: `%Y/%m/%d(%a) %H:%M`
- キーボード・ショートカットの設定
    - F1を押すとfalseコマンドを実行するようにする
    - PrintScreenへの割当を消す
    - 最近使ったファイルの記録をしない
- キーボード->レイアウト->オプションで CapsLockをCtrl扱いにする
- 最近使ったファイルの記録をしない
    - ``設定 -> 個人情報``

```
echo > ~/.local/share/recently-used.xbel
echo gtk-recent-files-max-age=0 >> ~/.gtkrc-2.0
echo echo -e "[Settings]\ngtk-recent-files-max-age=0" >> ~/.config/gtk-3.0/settings.ini
```
- mcomix
    - メニューの表示で「小さな画像を引き伸ばす」を有効に
    - 挙動->最近開いたファイルの情報を保存しない
    - 自動的に次のディレクトリを開くをオフ


### データ移行

```sh
rsync -avP ~/.dot_files kotonoha:~
rsync -avP ~/.zsh_history \
    ~/.asunder ~/.ssh   \
    kotonoha:~

# ファイル整理後
rsync -avP ~/Documents Downloads kotonoha:~

# chromeデータの移動

# 鍵の移動
```

### VMデータの移動

- [参考](https://oplern.hatenablog.com/entry/2016/11/06/212257)
    - CPUの変更
    - [トポロジーを適当に設定](https://www.alprovs.com/wordpress/?p=605)
    - [CPUごとの使用率を確認する方法](https://piyokabe.net/pc/win10/taskmanager-cpu-thread/)
    - ネットワークの起動
    - [固定IPアドレス](https://kana-linux.info/linux/kvm%E3%81%ABdhcp%E3%81%A7%E5%9B%BA%E5%AE%9Aip%E3%82%92%E8%A8%AD%E5%AE%9A%E3%81%99%E3%82%8B)
```
sudo virsh net-autostart default                                            
sudo virsh net-start default                                  
```


## その他

- ルーターのポート変換の変更
- fstabの設定
- fstabの設定
    - ``sudoedit /etc/hdparm.conf``

