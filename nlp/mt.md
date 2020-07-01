
# 機械翻訳

## tree-to-string

<blockquote class="twitter-tweet" lang="ja"><p>確率的tree-to-string翻訳を英日・日英翻訳に使ってみたという資料をアップしました： <a href="http://t.co/GGFDsbni" title="http://bit.ly/VsiCn4">bit.ly/VsiCn4</a> 。いろいろな翻訳方式、英語や日本語における構文解析器などを比較しています。</p>&mdash; Graham Neubigさん (@neubig) <a href="https://twitter.com/neubig/status/261697117431681024" data-datetime="2012-10-26T05:13:49+00:00">10月 26, 2012</a></blockquote>

<blockquote class="twitter-tweet" data-in-reply-to="261697117431681024" lang="ja"><p>@<a href="https://twitter.com/neubig">neubig</a> 一度、tree-to-stringにはまると、もうphrase-basedには戻れなくなりますよ。</p>&mdash; Taro Watanabeさん (@tarowatanabe) <a href="https://twitter.com/tarowatanabe/status/261802105206095872" data-datetime="2012-10-26T12:11:00+00:00">10月 26, 2012</a></blockquote>

<blockquote class="twitter-tweet" data-in-reply-to="261802105206095872" lang="ja"><p>@<a href="https://twitter.com/tarowatanabe">tarowatanabe</a> そんな気がします。綺麗なモデルですし、これからの伸びしろもphrase-baseよりだいぶ大きく感じますね。</p>&mdash; Graham Neubigさん (@neubig) <a href="https://twitter.com/neubig/status/261815497044135937" data-datetime="2012-10-26T13:04:13+00:00">10月 26, 2012</a></blockquote>

## MTと"実例"

<blockquote class="twitter-tweet" lang="ja"><p>IMEや機械翻訳のリアルシステムの開発ができていることはある意味ラッキーなのかもしれない。実例を細かく見る機会は圧倒的に増えた。今やっている細かなチューニングは論文には書けないような話ばかりだけど、個々の知見は今後役に立つと思う。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/183214721208557568" data-datetime="2012-03-23T15:32:48+00:00">3月 23, 2012</a></blockquote>

<blockquote class="twitter-tweet" lang="ja"><p>そいや、言語処理学会の時に「フレーズテーブルやどういうフレーズが使われているか人手で見てかなり細かくデバッグしてますよ」と言ったら研究者に驚かれた。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/183212177648398336" data-datetime="2012-03-23T15:22:41+00:00">3月 23, 2012</a></blockquote>

## エスペラント

<blockquote class="twitter-tweet" lang="ja"><p>エスペラントに対応した事よりも、後半のGoogleのコメントが気になる。エスペラントの機械翻訳精度が「驚くほど」高いことは我々研究者に何かを示唆しており、考察の価値あり。▼「Google Translate」、エスペラント語の翻訳に対応　<a href="http://t.co/lPVKKXQw" title="http://internet.watch.impress.co.jp/docs/news/20120223_514069.html">internet.watch.impress.co.jp/docs/news/2012…</a></p>&mdash; 山本 和英さん (@y8o) <a href="https://twitter.com/y8o/status/174318871317192705" data-datetime="2012-02-28T02:23:52+00:00">2月 28, 2012</a></blockquote>

## [翻訳自動評価尺度に関する論点](http://katsuhitosudoh.wordpress.com/2012/04/21/%E7%BF%BB%E8%A8%B3%E8%87%AA%E5%8B%95%E8%A9%95%E4%BE%A1%E5%B0%BA%E5%BA%A6%E3%81%AB%E9%96%A2%E3%81%99%E3%82%8B%E8%AB%96%E7%82%B9/)

> 某会合で翻訳評価の話をしていて帰り道で考えていたことをTwitterに書いたのですが今後のためにまとめておきます．
> ダイナミックレンジ。BLEUはおそらく40前後くらいがよさそう。RIBESは70台あたりか。スコアレンジごとの評価弁別性能が重要そう。
> 最適化適性。BLEUはなんかよくできてる。1点目とも関係するが、理想的には定義域全域でそれなりのgradientがほしい。
> イカサマ耐性。コンテスト参加チームの結果はみんな真面目にやっているので分からないが重要だと思う。これは2点目の最適化適性にもつながる。
> 文単位評価。BLEUもRIBESもコーパス単位では相関があると思うけど文単位ではいまいちで人間の直観に反する。というか専門外の人への説明に困る。
> そもそも自動評価ではなく人手評価でもintrinsicなもの，extrinsicなものの違いがありますし，何に着目するかというのもタスクによって違います．
>
> その一方で多くの関係者で共有するためには共通的に利用・比較できる仕組みが必要なわけで，非常に悩ましいです．
>
> 今後も気が向いたら議論を深めるために掘り下げて書いていきたいと思います．
