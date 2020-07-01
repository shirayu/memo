
# ディスプレイをUSB接続する

[Logitec ディスプレイアダプタ USB Full HD対応 LDE-WX015U](http://www.amazon.co.jp/gp/product/B002MH8ZVK/ref=as_li_ss_tl?ie=UTF8&camp=247&creative=7399&creativeASIN=B002MH8ZVK&linkCode=as2&tag=7-1-3-22)
という商品を買った．

[公式FAQ](http://www.displaylink.com/for-business/common_questions.php)にあるが，
Linuxでは，2014年4月現在，
DL-1x5シリーズのもののみが動き，
DL-3x00やDL-41xxシリーズは動かないので注意．

## 初期設定

``udlfb``を読み込まないようにしておく．

```sh
$ sudo vi /etc/modprobe.d/usb-display.conf
>>> blacklist udlfb を追記
```

そして，``udl``を起動時に読み込むようにしておく．

```sh
$ sudo vi /etc/modules
>>> udl を追記
```

初回は，手動でロードとアンロードする．

```sh
sudo modprobe -r udlfb
sudo modprobe udl
```

次に，USBにDisplaylinkを刺す．

```sh
$ xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x44 cap: 0xb, Source Output, Sink Output, Sink Offload crtcs: 3 outputs: 2 associated providers: 0 name:Intel
Provider 1: id: 0x126 cap: 0x2, Sink Output crtcs: 1 outputs: 1 associated providers: 0 name:modesetting
```

となる．

## 毎回やる作業

```sh
sudo xrandr --setprovideroutputsource 1 0
gnome-control-center display
```

そして，USBディスプレイをONにする
