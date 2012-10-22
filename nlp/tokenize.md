
# ひらがな

<blockquote class="twitter-tweet" lang="ja"><p>ひらがな列の解析が難しいのは、形態素解析器作るとわかる。候補がものすごく膨大に出てくる <a href="https://twitter.com/search/%23nlp2012">#nlp2012</a></p>&mdash; Yuya Unnoさん (@unnonouno) <a href="https://twitter.com/unnonouno/status/180545581159165952" data-datetime="2012-03-16T06:46:35+00:00">3月 16, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>



#点推定モデルと平仮名
<blockquote class="twitter-tweet" lang="ja"><p>kytea の出力を眺めたら、ひらがなの付属語列の解析があやしいというか直感に反する　太郎です=&gt; 太郎|で|す　よくした =&gt; よ|く|し|た 　など....これは意図的なものだろうか。unidic の mecabでは問題ない。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/121961612625186816" data-datetime="2011-10-06T14:54:49+00:00">10月 6, 2011</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" lang="ja"><p>まぁ、kytea や tinysegmenter のような点推定モデル (分かち書きと品詞推定をカスケーディングで解くモデル) は、原理的にひらがな列に弱い。「すももももも... 」はできない。日本語特有の長いひらがな付属語列の汎化には向いていなさそう。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/121963062625443840" data-datetime="2011-10-06T15:00:34+00:00">10月 6, 2011</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" data-in-reply-to="121963062625443840" lang="ja"><p>@<a href="https://twitter.com/taku910">taku910</a> 「すもも」は確かにできませんが、付属語列はほとんど誤らないはずです(誤り例があればぜひ教えてください)。ひらがなで書いた内容語の問題でしたら、ひらがな語の辞書を追加したらそれなりに分割してくれると思います。またモデルを更新するときにやってみます。</p>&mdash; Graham Neubigさん (@neubig) <a href="https://twitter.com/neubig/status/122099780678721536" data-datetime="2011-10-07T00:03:50+00:00">10月 7, 2011</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" data-in-reply-to="122099780678721536" lang="ja"><p>@<a href="https://twitter.com/neubig">neubig</a> 意図的だったのですね。了解しました。手元に環境が無いので確認できませんが、unidicは「て形」の扱いが活用だったので、そのあたりが違和感があるような気がします。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/122843388667113472" data-datetime="2011-10-09T01:18:40+00:00">10月 9, 2011</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


#日英の違い
<blockquote class="twitter-tweet" lang="ja"><p>日本語の単語分割した状態と、英語の生文を同列に扱うのはやめて欲しい。分割後のデータのみを保存し生文を消したり... 非日本語話者が作るとこういう設計になりがち。そりゃ見た目は同じになるが、元の文にあったスペースが復元不可能だし、別の単語分割を適用するのが激しく面倒になる。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/113583416678682624" data-datetime="2011-09-13T12:02:51+00:00">9月 13, 2011</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


<blockquote class="twitter-tweet" lang="ja"><p>欧米人にはテキストはスペースで区切ららているという強い前提があるようだ。そのせいでテキストの単語分割(トークナイゼーション)と品詞推定は独立した処理として定式化しがち。通常日本語処理ではその二つはジョイントモデルで処理するので注意が必要。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/103048731636678656" data-datetime="2011-08-15T10:21:46+00:00">8月 15, 2011</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
