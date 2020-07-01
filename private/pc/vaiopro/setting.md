
# その他の設定

色々と自分好みの設定をしていく．

## 最初に

- ログイン画面で「gnomeクラシック」を選択してログインする
    - 以降gdm3+gnome3

```sh
$ uname -a
Linux tamako 3.13-1-amd64 #1 SMP Debian 3.13.5-1 (2014-03-04) x86_64 GNU/Linux
```

## 初期設定

- networkの設定
- 基本設定

```sh
update-alternatives --config editor
visudo
  >>yuta-h    ALL=(ALL)       ALL
vim /etc/ssh/sshd_config
  >>PermitRootLogin no
```

### 基本環境設定

- 基本ツール

```sh
sudo aptitude install zsh screen unzip unrar paco htop lv vim-nox tmux
chsh -s `which zsh`
```

- ビルド関連ツール

```sh
sudo aptitude install build-essential swig automake libtool tinycdb libcdb-dev
sudo aptitude install git git-svn
```

### いろいろなもののインストール

```sh
sudo aptitude install ttf-vlgothic mozc-utils-gui fcitx fcitx-mozc cairo-clock dsh nkf
sudo aptitude install curl
sudo aptitude install mimms
sudo aptitude install comix
sudo aptitude install pandoc pandoc-citeproc
sudo aptitude install pdfshuffler pdfk
sudo aptitude install python-setuptools python-dev python3-setuptools
sudo easy_install pip
sudo easy_install3 pip
sudo pip install pip-tools
sudo pip2 install watchdog
sudo pip2 install jedi
sudo aptitude install uuid-runtime
sudo aptitude install parallel && mkdir ~/.parallel && touch ~/.parallel/will-cite
sudo aptitude install gparted ntfs-3g
sudo aptitude install ntp
sudo aptitude install wdiff colordiff
```

- 別マシンからDropboxをscpして，設定ファイルのsimlinkを作る
- 再ログイン

## gnome3の設定

- 各種フォルダの名前を変更

```sh
LANG=C xdg-user-dirs-gtk-update
```

### gnome-tweak-toolで設定

- gnome shell

```txt
User themes = on
show date in clock = on
タイトルバーのボタン = ALL
power button action = interactive
dynamic workspaces = off
```

- gnome shell拡張機能

```txt
Launch new instance有効
AlternateTab = on
Applications menu = on
window list = on
```

- Iceweaselでそれぞれ以下にアクセスしてインストールし，ONにする
    - [TopIcons](https://extensions.gnome.org/extension/495/topicons/)
        - バージョンの不一致で動かなくなったら，``~/.local/share/gnome-shell/extensions/``にあるファイルを編集
        - ``~/.local/share/gnome-shell/extensions/``で``git clone http://94.247.144.115/~git/topicons.git topIcons@adel.gadllah@gmail.com``としておいても良い
    - [Places Status Indicator](https://extensions.gnome.org/extension/8/places-status-indicator/)
    - [Removable Drive Menu](https://extensions.gnome.org/extension/7/removable-drive-menu/)
    - [Quit button](https://extensions.gnome.org/extension/156/quit-button/)
    - [Advanced volume mixer](https://extensions.gnome.org/extension/212/advanced-volume-mixer/)
    - [Taskbar](https://extensions.gnome.org/extension/584/taskbar/)
- Typing
    - Capsロックキーの操作 = ctrl
- テーマ
    - Enablae dark theme = on
- フォント

## 追加インストール

### はじめに

- google-chrome
- mendeley

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

- dropbox
- skype [参考](https://wiki.debian.org/skype)

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

### avconv

```sh
sudo aptitude install libav-tools
```

### rtmpdump

最新のレポジトリを使う

```sh
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

```sh
sudo adduser rtmpuser
sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -m owner \! --uid-owner  rtmpuser -j REDIRECT
su rtmpuser
rtmpsuck
```

- [参考](http://imoimo2010.blogspot.jp/2012/02/radikodebian60.html)

### cryptkeeper

```sh
sudo aptitude install cryptkeeper
sudo modprobe fuse
自動起動するアプリに追加:cryptkeeper (コマンド gnome-session-properties)
sudo addgroup yuta-h fuse
再ログイン
```

### gnome-session-properties

以下のチェックを外す

- Caribou
- Evolution
- Zeitgeist Datahub
- デスクトップの共有

### radiotray

```sh
sudo aptitude install radiotray
>  自動起動するアプリに追加 :radiotray
```

<!--
sudo  aptitude install  ruby-full rubygems
sudo  gem1.9.1 install rubygems-update
sudo gem install termtter
-->

### you-get

```sh
sudo pip3 install you-get
vi ~/.netrc
  >>>
    machine   nicovideo
    login     xxxxxxxxxxxxxxxxxxxx
    password  xxxxxxxxxxxxxxxxxxxx
chmod 700 ~/.netrc
```

### gnucash

```sh
sudo aptitude install gnucash python-gnucash
sudo cpan
> upgrade Finance::Quote
```

### LaTeX

```sh
sudo apt-get install texlive texlive-lang-cjk xdvik-ja dvipsk-ja gv \
 texlive-fonts-recommended texlive-fonts-extra omake fam chktex \
 lacheck latex2rtf texlive-xetex texlive-bibtex-extra latexmk
```

acroreadもインストールしておく．

```sh
sudo dpkg --add-architecture i386
sudo apt-get update
sudo aptitude install acroread:i386 acroread-dictionary-en:i386 acroread-plugins:i386
```

### Bluetooth

```sh
sudo apt-get install pulseaudio-module-bluetooth
sudo shutdown -r now
```

gnomeの音量設定タブからうまくbluetoothデバイスのプロファイルが選べない場合，

```sh
sudo apt-get install pavucontrol
```

で``pavucontrol``をインストールし，起動し，そこから選択する．
[参考](https://forums.ubuntulinux.jp/viewtopic.php?pid=98775)

うまく動かない時はサービスを再起動すると動いたことがあった．

```sh
sudo service bluetooth restart
sudo killall pulseaudio
```

[参考](https://wiki.debian.org/BluetoothUser/a2dp)

### GPU動画再生

```sh
sudo aptitude install libvdpau-dev
sudo aptitude install libvdpau1
sudo aptitude install vdpau-va-driver
sudo aptitude install vdpauinfo
sudo aptitude install libvdpau-va-gl1
sudo aptitude install libva-intel-driver

sudo vi /etc/profile.d/vdpau_vaapi.sh
 #!/bin/sh
 #export VDPAU_DRIVER=va_gl
 export VDPAU_DRIVER=r600
 export LIBVA_DRIVER_NAME=vdpau
sudo chmod a+x /etc/profile.d/vdpau_vaapi.sh
sudo reboot

vdpauinfo
```

### gvfs

Sambaからvlcを起動できるようにする

```sh
sudo aptitude install gvfs-fuse
sudo shutdown -r now
```

### webcam

```sh
$ cheese
libv4l2: error got 4 consecutive frame decode errors, last error: v4l-convert: libjpeg error: End Of Image

(cheese:6240): cheese-WARNING : Internal data flow error.: gstbasesrc.c(2865): gst_base_src_loop (): /GstCameraBin:camerabin/GstWrapperCameraBinSrc:camera_source/GstBin:bin27/GstV4l2Src:video_source:
streaming task paused, reason error (-5)
```

### playonlinux

```sh
sudo aptitude install playonlinux
```

### scansnap S300

```sh
sudo apt-get install sane xsane
sudo mkdir /usr/share/sane/epjitsu
sudo cp ~/300_0C00.nal /usr/share/sane/epjitsu/300_0C00.nal
sudo chmod a+r /usr/share/sane/epjitsu/300_0C00.nal
sudo service saned restart
```

### jq

```sh
wget https://github.com/stedolan/jq/releases/download/jq-1.5/jq-linux64 -O ~/local/bin/jq && chmod a+x ~/local/bin/jq
```

## その他の設定

### geditの設定

- geditを起動して，上のgeditアイコンのところで右クリックし，設定をクリック
- 以下の設定を行う
    - 行番号を表示
    - 折り返しを無効
    - 強調表示をON
    - 保存前にバックアップを無効
    - カラースキームはOblivion


### evinceの日本語フォントの設定

``KozMinPr6N-Regular.otf``と``KozGoPr6N-Medium.otf``をインストールしてから，
``~/.fonts.conf`` (または``~/.config/fontconfig/``)
に以下の記述
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="pattern">
<test qual="any" name="family">
   <string>Ryumin</string>
</test>
<edit name="family" mode="prepend" binding="strong">
  <string>Kozuka Mincho Pr6N</string>
</edit>
</match>
<match target="pattern">
  <test qual="any" name="family">
      <string>GothicBBB</string>
  </test>
  <edit name="family" mode="prepend" binding="strong">
     <string>Kozuka Gothic Pr6N</string>
  </edit>
 </match>
</fontconfig>
```

### デフォルトのフォントをVLゴシックにする

``~/.fonts.conf``に以下の記述．

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <alias>
        <family>serif</family>
        <prefer>
            <family>VL Gothic</family>
        </prefer>
    </alias>
    <alias>
        <family>sans-serif</family>
        <prefer>
            <family>VL Gothic</family>
        </prefer>
    </alias>
    <alias>
        <family>monospace</family>
        <prefer>
            <family>VL Gothic</family>
        </prefer>
    </alias>
</fontconfig>
```

その後，
```
$ fc-match
VL-Gothic-Regular.ttf: "VL ゴシック" "regular"
```
となり，再ログインすればOK.


### gtkエラーの対処
terminalからGUIアプリ起動するとエラーが出て気持ち悪い

```
Gtk-WARNING : module_path にはテーマ・エンジンがありません: "pixmap",
```
[参考](http://d.hatena.ne.jp/hoge37/20111119/1321680014)

```
Gtk-Message: Failed to load module "canberra-gtk-module"
```
[参考](http://forums.debian.net/viewtopic.php?f=10&t=81835)

```
sudo apt-get install gtk2-engines-pixbuf
sudo apt-get install libcanberra-gtk3-module
```

### IPv6を無効にする
- https://wiki.debian.org/DebianIPv6#How_to_turn_off_IPv6

### nss-myhostname
``dmesg``
で
```
[   22.693032] systemd-hostnamed[3889]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```
というエラーが出るので
```
sudo apt-get install libnss-myhostname
```

### 「電源オフ」しても電源が切れない
アップデートしたら，なぜかメニューの「電源オフ」を押しても電源が切れなくなった．
``dmesg``を見ると，
```
[ 2700.079947] systemd-logind[2931]: Removed session 1.
[ 2702.867704] systemd-logind[2931]: System is powering down.
[ 2702.885223] systemd-logind[2931]: Failed to send delayed message: Launch helper exited with unknown return code 1
```
となっている．
[フォーラムによると](http://forums.debian.net/viewtopic.php?f=10&t=109412)
```
init=/bin/systemd
```
をカーネルオプションに足せば良いらしい．
``/etc/default/grub``の``GRUB_CMDLINE_LINUX_DEFAULT``に
``init=/bin/systemd``を足して，
```
$ sudo update-grub
```
すればよい．

### ファイルマネージャのデフォルトを変えたい

```
exo-preferred-applications
```

### ディスプレイの輝度が保存する
ディスプレイの輝度が終了時に自動保存されなくなったので，自動保存するように変更([参考](http://askubuntu.com/a/434916)


```
sudo touch /etc/init.d/prev_brightness
sudo chmod a+w /etc/init.d/prev_brightness
sudo vi /etc/init.d/save_screen_brightness
  #!/bin/sh
  cat /sys/class/backlight/intel_backlight/brightness > /etc/init.d/prev_brightness
sudo chmod a+rx /etc/init.d/save_screen_brightness
sudo ln -s /etc/init.d/save_screen_brightness /etc/rc0.d/K99save_screen_brightness
sudo ln -s /etc/init.d/save_screen_brightness /etc/rc6.d/K99save_screen_brightness
sudo vi /etc/rc.local
  # exit0 の前に追記
  cat /etc/init.d/prev_brightness >/sys/class/backlight/intel_backlight/brightness
```

### USB-LANポートを刺したまま起動できない

- USB-LANポートを刺したまま起動すると，grubの画面で止まった
- いろいろ試したら起動するようになったので，解決法は不明
    - OSアップデート?
    - USBポートにマシンの電源OFF時でも給電(vaioの設定)

## Links
- http://ssig33.com/text/VAIO%20Pro%20%E3%82%92%20Linux%20%E3%81%A7
- http://pcdennokan.dip.jp/hardware/vaiopro11_debian/
- http://marigold.sakura.ne.jp/linux/vaio_pro_13/index.html
- http://tekiomo.hatenablog.com/entry/2013/01/29/230056
- http://fedorakenken.doorblog.jp/archives/51793334.html
- http://d.hatena.ne.jp/hoge37/20111119/1321680014

### 関連するがトラブル解決には寄与しなかったリンク
- http://ubuntuforums.org/showthread.php?t=2208426
- http://ubuntuforums.org/showthread.php?t=2208426
- http://paulphilippov.com/articles/how-to-fix-slow-boot-with-ata-errors
- https://bbs.archlinux.org/viewtopic.php?pid=1374549
- https://sites.google.com/site/ubuntu05070/hard-disk-repair
- https://bbs.archlinux.org/viewtopic.php?pid=1374587
- http://pastebin.com/HBQKfLKD
- https://wiki.debian.org/SSDOptimization
- http://forums.gentoo.org/viewtopic-t-883179-start-0.html
- http://wiki.gentoo.org/wiki/Apple_Macbook_Pro_Retina_2013
- http://d.hatena.ne.jp/pekeq/20070719/p2



