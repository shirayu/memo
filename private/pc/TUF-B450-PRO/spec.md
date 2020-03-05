
#a 仕様

| 項目  | 型番 | 購入先 | 価格 | 備考 |
| -- | -- | -- | -- | -- |
| マザーボード | [Asus TUF B450-PRO GAMING](https://www.asus.com/jp/Motherboards/TUF-B450-PRO-GAMING/specifications/) | ビックカメラ | 12,980 (約5900pt付き) | |
| CPU  | Ryzen 5 3600 | Amazon |  26,644 (1066pt付) | 65W.第3世代, 6コア12スレッド.グラフィックスなし|
| CPUファン | 虎徹 Mark II | Amazon | 4,106 (164pt付)| サイドフロー |
| CPUグリス | Thermal Grizzly Kryonaut 1g | Amazon | 767 (31pt付) |  |
| メモリ | CFD Crucial (Micron製) W4U3200CM-16G | DDR4-3200, 16GBx2 | amazon | 16,200 (162pt付) | |
| ビデオカード | [GT1030-SL-2G-BRK](http://kakaku.com/item/K0000969293/) | amazon | 10326 (流用) | |
| サウンドカード | オンボ | - | - | |
| M.2 SSD | [ADATA XPG SX8200 Pro ASX8200PNP-512GT-C](https://www.amazon.co.jp/dp/B07SZ81FPM) | amazon |  7,599 | 500GB.PCIe3.0×4 NVMe1.3.エレコムOEM |
| M.2 ヒートシンク | 長尾製作所 SS-M2S-HS01 | Amazon | 1,055 (11pt付) | |
| 外付け光学ドライブ | BRXL-PC6VU2-BKC | buffalo | 4,882 (流用) | |
| OS | なし | - | - | debian-testingを入れる|
| ケース | [Define R5 FD-CA-DEF-R5](http://kakaku.com/item/J0000014266/) | TSUKUMO | 10,360  | 並行作業用に追加購入 |
| 電源 | [NeoECO GOLD NE750 GOLD](https://kakaku.com/item/K0001019734/spec/#tab) | 10,580 (10%pt) | 6,535 | ATX12V 2.4 |

一部は以前からの流用

## マザーボード: Asus TUF B450-PRO GAMING

| 項目 | 仕様| 備考 |
| -- | -- | -- |
| フォームファクタ | ATX | |
| CPUスロット | SocketAM4 | |
| チップセット | AMD B450| |
| メモリスロット | DDR4-DIMM 4枚まで |  |sus TUF B450-PRO
| メモリ種類 | 2666/2400/2133 MHz | OC=3533/3466/3200/3000/2800 |
| 最大メモリ　| 64GB | |
| CrossFire | あり | |

### インタフェース

| 項目 | 本数 | 使用済 | 備考 |
| -- | -- | -- | -- |
| SATA |6| 6 | |
| PCI Express 3.0(x16) | 2 | 1 | グラボ |
| PCI Express 3.0(x1) | 3 | 2 | TWIN TURBO HYBRID TYPEB |
| M.2 | 2 |  | SATA5,6が排他.M key, type 2242/2260/2280/22110. |

### オンボード機能

| 項目 | 仕様| 備考 |
| -- | -- | -- |
| オーディオ | Realtek ALC S1200A | |
| 内蔵グラフィックスポート | DVI-D, HDMI | |
| HDMI | 最大 4096x2160 @ 60 Hz | |
| DVI-D | 最大 920x1200 @ 60 Hz | |
| 背面ポート | PS/2, USB Type-Cx1, USB 3.1 Gen 2x2, USB 3.1 Gen 1x2, USB 2.0x2 | |

### ディスプレイ

| 型番 |サイズ | タイプ | 解像度|消費電力| 画素ピッチ |重量| 購入時期 |
| -- | -- | -- | --|--|--|--|--|
| [ASUS VE248HR](http://kakaku.com/item/K0000874256/spec/) | 24 | TN | FullHD (1920x1080) | 35W | 0.2768mm |4.4kg | 2016/9 |
| [LG 43UD79T-B](http://kakaku.com/item/K0000961786/spec/) |42.5 | IPS | 4K（3840x2160） | 70W | 0.245 mm |15.9kg | 2018/8 |


### 備品

- 日本語キーボード 947円
- マウス 403円

### 設定

- メモリの周波数はデフォルトでは2666 MHz
    - BIOS設定で変更する
- マザーボードによっては第3世代Ryzenに対応している最初にBIOSが入っていない場合がある
    - その場合，そもそもBIOSが起動できない
    - AMD CPU Athlon 200GEを5,706円で買ってアップデートした
- 新し目の構成の場合，Linuxカーネルは新しいものが良さそう

