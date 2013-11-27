

# CaboChaのChangeLog

各種文献から，CaboChaの更新履歴をまとめた．

## 2008-01-14: [CaboCha 0.60 pre1](http://chasen.org/~taku/blog/archives/2008/01/cabocha_060_pre.html)

- UTF8対応 (``./configure --with-charset=UTF8``)
- 文節区切りと固有表現抽出にCRF(実装は[CRF++](https://code.google.com/p/crfpp/))を使用
- ChaSenへの依存を廃止
    - MeCabのみのサポート
- 固有表現を行う前に文字列の正規化
    - 若干の精度向上
- 簡易並列処理の廃止
    - 係り受けのみ．
- APIの一新．より粒度の細かい制御が可．
- PerlやMakefileに依存していた部分の排除
- 単一バイナリ``cabocha-learn``による学習の簡易化 (Windowsでも学習が可能)
- TinySVMへの依存を排除
    - 単体で学習可能
- Jumanのサポートを復活
    - 形態素解析は``mecab-juman``に限定
- 評価ツール``caboca-system-eval``の提供 


## 2005-12-24: CaboCha 0.53
- 極端に長い文を解析すると``segmentation falt``になる問題を修正

## 2004-10-07: CaboCha 0.52
- MeCabをサポート
- ``% cabocha --morphological-analyzer=mecab``とすれば``mecab``が起動される

## 2004-08-05: CaboCha 0.51
- ``cabocha_new``，``cabocha_new2``に失敗した時にメモリリークが起きる問題を修正
- Windows版インストール時にadministrator権限でインストールすると，全ユーザが使用可能にできるように
    - インストール時のオプションで変更可能

## 2004-03-28: CaboCha 0.50
- 解析速度を大幅に高速化．(7-8倍高速)
    - SVM の分類アルゴリズムの高速化手法であるPKE(ACL 2003にて発表)を適用
    - (非力な計算機では動作が遅くなるかもしれません．メモリは 512MB 以上，CPUは 1.0GHz 以上の計算機をお使い下さい.)
- YamCha 0.30 対応．
    - YamCha 0.27以下のバージョンでは動きません．アップグレードを行ってください.
- 文節切りに用いる学習データの量を増やした.
- 係り受け学習時のパラメータを変更し，若干精度が向上した.
- 小規模モデルを削除した．
    - 分類の高速化に伴い，小規模のモデルを使う必要がなくなっため
- [固有表現抽出をやめれば，KNP と同じぐらいの速度](http://web.archive.org/web/20050313181144/http://chasen.org/~taku/blog/archives/2004/03/cabocha_050.html)

## 2004-03-08: CaboCha 0.44
- ライセンスを LGPL に変更
- 数値 (DATE，MONEY) の固有表現抽出の精度向上のために，数字の連結品詞相当を実装し，再学習した
    - 明治16年は「時間」と解析できるが，明治6年はできない[問題](http://web.archive.org/web/20050313181144/http://chasen.org/~taku/blog/archives/2004/03/cabocha_1.html)
    - 1，6が別の形態素になってしまうため，この2つの事例がdistinctなものになってしまう．
    - 連結品詞は無くなる方向なので，NE側で解決する．
- 文節区切りの誤り事例を追加し，再学習した
- Windows版に附属の ChaSen を ChaSen 2.1 から ChaSen 2.3.3 に変更

## 2003-10-24 CaboCha-PKE
- CaboCha-PKEの公開
```
RWCP コーパス 2000文 の解析時間
    PKE (高速版):  26.71s  user 0.31s system 99% cpu 27.122  total
    今の cabocha:  206.14s user 0.05s system 100% cpu 3:26.18 total
7.7倍程度高速になる模様.
もともとが PKI という手法を使てて，12倍ほどはやいから，オリジナルの SVM より 
12 * 7.7 = 92倍高速に動作していると思われる.
```

## 2003-09-14: CaboCha 0.43
- C の API を使うと，特定の環境で (RedHat 9) 解析結果が変になる (素性選択に失敗する) バグを修正.
    - (RetHat9 上で C API，perl/ruby/python モジュールを使ってる方は，早急 にアップグレードしてください)
- ruby の正規表現ライブラリを使っていたが，使うのをやめた
- [経緯](http://web.archive.org/web/20050313181234/http://chasen.org/~taku/blog/archives/2003/09/regex.html)
    - Cのlibrary (``cabocha_sparse_tostr()``)とC++のlibrary (``CaboCha::Parser::parseToString()``)の2つの出力結果がRedHat 9で異なる．
    - これはrubyの正規表現ライブラリ由来の問題．
    - そこで，正規表現をやめて，``PatternMatcher``クラスを作成し代替．


## 2003-08-15: CaboCha 0.42
- 不正な NE タグ列を出力する可能性があるバグを修正．(例: 文頭に I タグが付いたり，I-LOCATION，I-PERSION といった不正なタグ列)
- ``getenv``が``configure``スクリプトで正しく読めない問題を修正
    - (``~/.cabocharc``の読みこみができなかった)

## 2003-07-04: CaboCha 0.41
- C の``stdio``と非同期に動作させていたのをやめた．(perl/ruby の``open2``，``open3``経由で使えるようになった)
- yamcha 0.26 以降を使うことで，sparc 環境で正常に動作するようになった.

## 2003-05-12: CaboCha 0.4
- 固有表現抽出機能を付与
    - IREXで定義される固有表現タグを出力
    - 精度はF値で85前後
- 固有表現抽出機能の整合性の都合上 JUMAN のサポートを停止した.
- C++ レベルの API の変更
- C 用 API への関数追加，スクリプトバインディング(perl/ruby/python) のインタフェイスの変更
- pre
    - [CaboCha 0.4pre2 (2003.04.08)](http://web.archive.org/web/20050313180935/http://chasen.org/~taku/blog/archives/2003/04/cabochane.html)
    - [CaboCha 0.4pre1 (2003.04.04)](http://web.archive.org/web/20050313180935/http://chasen.org/~taku/blog/archives/2003/04/cabocha04pre1.html)



## 2003-03-31: CaboCha 0.36
- まっさらの環境にインストールする際，``make check``がうまく動かない バグを修正した.
- ``$HOME/.cabocharc``および環境変数``CABOCHARC``による``cabocharc``の指定が正常に行われないバグを修正した.

## 2003-03-29: CaboCha 0.35
- IPA のモデルを再学習，再構築
    - 従来は，IPA品詞体系と京大コーパス の「文節切り」の整合性を ad-hoc に解決していたが，厳密に解決した
    - IPA品詞体系の連語 (として，について) の解析が正しく行えるようになった
    - 個々の文節長が長くなるため「みかけ」の精度は下がるが，実用上の精度は向上している
- 並列+同格の情報を付与するモデルを添付
- ChaSenの連結品詞の機能を使う必要がなくなった
    - (連結品詞の機能を off にした ChaSen で文節切りの学習データを作成した.)
- ``chasen``を呼ぶ``class``をsingletonにした
    - 複数回呼びだされても，1回の呼びだしとなる
    - ``-c``オプションによる``chasenrc``の指定は，最初の1回のみに限定される
    - (chasenが再入不可能なライブラリのため仕方がない)
- JUMANのモデルファイルを別配布にした
- Windows 版を自己解凍形式に変更，インストールが容易になった
    - [Inno Setup](http://web.archive.org/web/20050313180921/http://chasen.org/~taku/blog/archives/2003/03/cabocha_035.html)

## 2003-01-31: CaboCha 0.34
- ``chasen``を呼ぶときに，``-F``オプション付きで呼ぶのをやめた
    - それに より「未知語品詞」を使うことができるようになった
    - 未知語の多くが名詞の場合は，精度が向上すると思われる
- ``cabocha_sparse_tostr ()``の戻り値にゴミが入るバグを修正
- メモリーリークのバグの修正
- Windows Versionの開発をmingwから Visual Studio .NET C++ に変更

## 2003-01-06: CaboCha 0.33
- ``param.cpp`` (コマンドライン解析ルーチン) の変更

## 2002-11-21: CaboCha 0.32 Released
- ``-o``オプションが動作しないバグを修正

## 2002-11-20: [CaboChaの改良について](http://web.archive.org/web/20060208183548/http://chasen.org/~taku/blog/archives/2002/11/cabocha_5.html)
```
map<> で表現していた素性を trie で表現したりがむばる.
```

```
京大コーパス 2.0 1/9日分 約 1200文

高速版 time ./cabocha -r /usr/etc/cabocharc -I2 -m dep.0.0001.cmodel < test > /dev/null
5.45s user 0.20s system 49% cpu 11.489 total

従来: time cabocha -r cabocharc -I2 < test > /dev/null
25.95s user 0.08s system 49% cpu 52.474 total

結果はかわらず．できたモデルファイルが 451MB にもなってしまった.．
(mmap で読んでるので，ほとんど問題になりません)
trie の中間 node を毎回頭からなめているので，実はまだ高速にできると思う.
```

```
2年前 perl で実装した cabocha のプロトタイプが，解析に10分ぐらい，
それを C++ でかいて，1分．さらにいろいろ工夫して5秒ぐらまできました.
```


## 2002-11-13: CaboCha 0.31
- ``-r``オプションが動作しないバグを修正
- chasen のリンクが cygwin，FreeBSD でうまくいかない問題を修正
- 0.3は，オプションの指定ができないバグが含まれているので，0.31をお使いください.

## 2002-11-11:
- 2文節しかない文を入力したときに，係り受けタイプが出力されないバグを修正
- 部分解析ができていないバグを修正
- Oタグに関する解説を追加
- 係り受けの学習に関するドキュメントの修正 (一部誤りがあった)
- ソースコードをきれいにした.
- gcc 3.2，Borland C++，Visual Studio .NET に対応

## 2002-02-21 [CaboChaの速度について](http://web.archive.org/web/20060208183451/http://chasen.org/~taku/blog/archives/2002/02/cabocha_7.html)
```
9年分の新聞記事を解析させてみる.
小一時間動かすも，20日ぶんぐらいしか終わっていない.
10日 = 30分という計算だと

1ヶ月 90分
1年 1080分 = 18時間
9年 9720分 = 162時間 = 1週間

ってことか...
```


## 2001-10-22: CaboCha 0.21
- JUMAN用 chunker モデルに欠陥があり，解析中に core dump するバグを修正
- IPA用 chunker モデル中のバグを修正
- ChaSen用 handler が入力フォーマットを上書きしてしまうバグを修正

## 2001-10-19: CaboCha 0.2
- データ構造とメモリ管理の工夫により，20-30%の高速化
- C++/Perl/Ruby/Python interface の充実
- 文節切りの位置をユーザが指定できるようになった．(必ず切る/絶対切らない/任意の位置の指定)
- XML出力の暫定対応

## 2001-07-07: CaboCha 0.1
- Initial Release!


# Links
- [公式サイト](https://web.archive.org/web/20110725161529/http://chasen.org/~taku/software/cabocha/)
