
# KUINS
京大ネットワークKUINSに接続するには設定が必要

## システム全体のプロキシ設定

(注) 2015年1月に[透過型プロキシサーバが導入された](http://www.iimc.kyoto-u.ac.jp/ja/whatsnew/information/detail/150224052768.html)ので現在，この設定は不要．
電子ジャーナルを見る場合は，別の[設定](http://www.iimc.kyoto-u.ac.jp/ja/services/kuins/external/use/proxy.html)が必要

デスクトップマシン等，常にKUINSに接続するマシンは，この設定をしておくと楽．
``/etc/profile.d/proxy.sh``を作り，システム全体に効く環境変数を設定する．

```
#!/bin/sh
PROXY="proxy.kuins.net:8080"
export http_proxy="$PROXY"
export https_proxy="$PROXY"
export ftp_proxy="$PROXY"
export HTTP_PROXY="$PROXY"
export HTTPS_PROXY="$PROXY"
export FTP_PROXY="$PROXY"
export no_proxy="127.0.0.1,localhost"
export NO_PROXY="$no_proxy"
```


## MIAKO NET
VPN(PPTP)で接続する必要がある．
PPPTじゃなくてPPTPであることに注意．

```
sudo aptitude install network-manager-pptp-gnome
```

その後
```
nm-connection-editor
```
で設定画面を起動し，VPNの中のPPTPを選択して，設定する．


## Windowsでの設定
IEの設定を読み込む
```
netsh winhttp import proxy source=ie
```

リセットする
```
netsh winhttp reset proxy
```

- [参考](https://www.upken.jp/kb/proxy-for-windowsupdate.html)


## Links
- [プロキシ下でLinuxを使う際のメモ](http://lambdalisue.hatenablog.com/entry/2013/06/25/140630)
- [Ubuntuを利用している場合のPPTP接続設定例](http://www.kuins.kyoto-u.ac.jp/ja/index.php?Ubuntu%A4%C7PPTP%C0%DC%C2%B3)


