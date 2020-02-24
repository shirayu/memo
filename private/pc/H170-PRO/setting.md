# ソフトウェア

## 基本環境設定

- 基本ツール

```sh
su #rootになる
apt-get install aptitude sudo zsh screen unzip unrar unar paco htop lv vim-nox tmux
update-alternatives --config editor #vim-noxを選択
visudo
  >>yuta-h    ALL=(ALL)       ALL
vim /etc/ssh/sshd_config
  >>PermitRootLogin no
chsh -s `which zsh`
exit #rootを抜ける
```

- ビルド関連ツール

```sh
sudo aptitude install build-essential swig autoconf automake libtool tinycdb libcdb-dev libncurses-dev aptitude install git git-core git-svn dkms
```

## いろいろなもののインストール

- Dropbox
  - ダウンロードしてインストール
- 入力メソッド
  - ``fcitx``+``fcitx-mozc``が良い
  - ``sudo aptitude purge uim-mozc``しないとmozcの設定画面で落ちる
  - ``sudo aptitude install mozc-utils-gui fcitx fcitx-mozc``
- その他
  - ``sudo aptitude install dsh nkf curl mimms comix pandoc pandoc-citeproc pdfshuffler pdfk uuid-runtime``
  - ``sudo aptitude install parallel && mkdir ~/.parallel && touch ~/.parallel/will-cite``
  - ``sudo aptitude install gparted ntfs-3g ntp wdiff colordiff peco nvtop jq``
- python関連
```
sudo aptitude install python-setuptools python-dev python3-setuptools
sudo easy_install3 pip
sudo pip3 install pip-tools
sudo pip3 install watchdog
sudo pip3 install jedi
sudo pip3 install withings
sudo pip3 install requests_oauthlib`
```
  - [python-fitbit](https://github.com/orcasgit/python-fitbit)

## 追加インストール

- google-chrome

### nitrogen
- マルチディスプレイの際，壁紙を設定するアプリケーション
- 自動起動するアプリに，``nitrogen --restore``を追加する

###  mendeley
```txt
Unable to use Qt libraries in /usr/lib/x86_64-linux-gnu. Some components are missing:
        /usr/lib/x86_64-linux-gnu/libQtSvg.so.4.8.6
        /usr/lib/x86_64-linux-gnu/libQtXmlPatterns.so.4.8.6
        /usr/lib/x86_64-linux-gnu/libQtWebKit.so.4
To run Mendeley Desktop you may need to install the QtWebKit and QtSvg packages provided by your Linux distribution.
```

というエラーが出たら，必要なモジュールをインストールする．

```sh
sudo aptitude install libqt4-webkit libqt4-svg libqt4-xmlpatterns
```


### vlc

```sh
sudo vi /etc/apt/sources.list
  >> deb http://www.deb-multimedia.org jessie main non-free
  >> /etc/debian_version のバージョンと一致するか確認すること
sudo aptitude update
sudo apt-get install deb-multimedia-keyring
sudo aptitude update
sudo aptitude install vlc libdvdcss2
```

- 画面がちらつく場合[ハードウェアアクセラレーションの設定](https://wiki.archlinuxjp.org/index.php/VLC_media_player#.E3.83.8F.E3.83.BC.E3.83.89.E3.82.A6.E3.82.A7.E3.82.A2.E3.82.A2.E3.82.AF.E3.82.BB.E3.83.A9.E3.83.AC.E3.83.BC.E3.82.B7.E3.83.A7.E3.83.B3.E3.81.AE.E3.82.B5.E3.83.9D.E3.83.BC.E3.83.88)がおかしい可能性が有る
  - キャプチャが保存できなかったり
  - 別のものに変えてみて，一旦VLCを再起動してみる
- 「ビデオのサイズにインターフェースをリサイズ」をオフにする
- スクリーンショットの形式を ``$N_$ T_`` にする

### avconv

```sh
sudo aptitude install libav-tools
```


### rtmpdump

最新のレポジトリを使う
```
sudo aptitude install iptables-persistent rtmpdump
sudo vi /etc/iptables/rules.v4
sudo  apt-get install zlib1g-dev libgnutls-dev libjpeg62-dev libssl-dev
git clone git://git.ffmpeg.org/rtmpdump
cd rtmpdump
make
sudo make install
sudo ldconfig
```

純正flashじゃないとダウンロードできなかったので

```sh
sudo apt-get install flashplugin-nonfree
```

してから，
```
sudo adduser rtmpuser
sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -m owner \! --uid-owner  rtmpuser -j REDIRECT
su rtmpuser
rtmpsuck
```

- [参考](http://imoimo2010.blogspot.jp/2012/02/radikodebian60.html)

### cryptkeeper
```
sudo aptitude install cryptkeeper
sudo modprobe fuse
自動起動するアプリに追加:cryptkeeper (コマンド gnome-session-properties)
sudo addgroup yuta-h fuse
再ログイン
```

### you-get
```
sudo pip3 install you-get
vi ~/.netrc
  >>>
    machine   nicovideo
    login     xxxxxxxxxxxxxxxxxxxx
    password  xxxxxxxxxxxxxxxxxxxx
chmod 700 ~/.netrc
```

### gnucash
```
sudo aptitude install gnucash python-gnucash libdbd-sqlite3
sudo cpan
> upgrade Finance::Quote
```


### LaTeX
```
sudo apt-get install texlive texlive-lang-cjk xdvik-ja dvipsk-ja gv \
 texlive-fonts-recommended texlive-fonts-extra omake fam chktex \
 lacheck latex2rtf texlive-xetex texlive-bibtex-extra latexmk
```

acroreadもインストールしておく．
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo aptitude install acroread:i386 acroread-dictionary-en:i386 acroread-plugins:i386
```


## デスクトップ環境の設定
- 各種フォルダの名前を変更
    - ``LANG=C xdg-user-dirs-gtk-update``
- vlc
    - オーバレイを無効
    - 多重起動を有効にする
- cinamoneで[自動ログイン](http://www.linuxserve.com/2015/06/how-to-enable-automatic-login-on-debian.html)
    - ``seahorse``をインストールして，自動起動するようにする．
    - 毎回再起動あとに，鍵を手動で開放する
- スクリーンロックを無効にする


## その他
- 日付アプレットの書式: ``%Y/%m/%d(%a) %H:%M``
- crontabの設定
- 節電設定
    - ``sudo aptitude install hdparm sysv-rc-conf``
    - ``sudoedit /etc/hdparm.conf``
- VM
    - http://blog.kmckk.com/archives/4374606.html
    - 仮想マシンはhome以下に作る(場所を選べる)
    - USBタブレットでマウス接続
    - swishでホストとの間でデータをやりとりする
- dmesgにエラーが無いかチェック
    - 今のカーネルは``Linux kanna 4.3.0-1-amd64 #1 SMP Debian 4.3.3-5 (2016-01-04) x86_64 GNU/Linux``
- キーボード・ショートカットの設定
    - ``F1``を押すと``false``コマンドを実行するようにする
    - ``PrintScreen``への割当を消す
- VDPAU
    - https://wiki.archlinuxjp.org/index.php/VDPAU
- 最近使ったファイルの記録をしない
```
echo > ~/.local/share/recently-used.xbel
echo gtk-recent-files-max-age=0 >> ~/.gtkrc-2.0
echo echo -e "[Settings]\ngtk-recent-files-max-age=0" >> ~/.config/gtk-3.0/settings.ini
```
