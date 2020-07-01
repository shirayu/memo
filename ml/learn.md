
# 学習

## 素性

<blockquote class="twitter-tweet" lang="ja"><p>「言語モデル確率を素性に利用する」ことや「品詞に写像して連接確率を学習する」ことなどは「多くの素性を１つに束ねて、高い精度を実現するために必要な素性の数を減らす」ことに値する。一般的にこれができると新しいデータへの汎化能力が向上し、精度や安定性、分野適応性も向上するに違いない。</p>&mdash; Graham Neubigさん (@neubig) <a href="https://twitter.com/neubig/status/169256619287384064" data-datetime="2012-02-14T03:08:17+00:00">2月 14, 2012</a></blockquote>

## 高速化

<blockquote class="twitter-tweet" lang="ja"><p>あまり知られていませんが、CaboChaは、単純なSVM分類器を動かすのではなく、カーネルを素性マイニングを使って線形判別機に変換することで劇的に高速化しています。今実験したら 3.55文/sec→1720文/secでした。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/97701675179057153" data-datetime="2011-07-31T16:14:29+00:00">7月 31, 2011</a></blockquote>

## 能動学習

<blockquote class="twitter-tweet" data-in-reply-to="169249679064825856" lang="ja"><p>@<a href="https://twitter.com/neubig">neubig</a> 学習に使うコーパスが同じであれば、識別モデルがいいと思いますが複雑性とのトレードオフだと思います。言語モデルはあくまでもソース言語(入力ひらがな)の知識がいらないので量をいくらでも増やせます。IMEもMTだと思えば、MERTを使って組み合わせるるのが自然</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/169255162437844992" data-datetime="2012-02-14T03:02:29+00:00">2月 14, 2012</a></blockquote>

<blockquote class="twitter-tweet" lang="ja"><p>能動学習は、タグ付けのコストを小さくする目的を、サンプル数の最小化という手段で実現にしてるにすぎない。それは間違ってはいないが、手段の目的化に見える。同目的を達成するにはUIの工夫や作業者とのコミュニケーション手段などのほうが重要なことが多いと思う。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/155480017898438656" data-datetime="2012-01-07T02:44:59+00:00">1月 7, 2012</a></blockquote>

## その他

<blockquote class="twitter-tweet" lang="ja"><p>SVMではデータ全体で一回しか出てこない素性の重みwは0&lt;=w*&lt;=Cなんですね。反復するたびにガスガス増えていくそんじょそこらのオンライン学習アルゴリズムとは違いますね。</p>&mdash; 松島 慎さん (@masin29) <a href="https://twitter.com/masin29/status/145532515187310592" data-datetime="2011-12-10T15:57:10+00:00">12月 10, 2011</a></blockquote>

<blockquote class="twitter-tweet" lang="ja"><p><a href="https://twitter.com/search/%23pfiseminar">#pfiseminar</a> 話は前後するけど、今の考えは、解析アルゴリズムはパラメータを人手でいじれるぐらいに単純に。未知語処理は最低限で基本やらない。語彙獲得をオフラインでがんばってやる。ってのが実世界では良いかな～。もちろん精度は犠牲になるかもしれませんが…</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/127046905694912512" data-datetime="2011-10-20T15:41:57+00:00">10月 20, 2011</a></blockquote>

<blockquote class="twitter-tweet" lang="ja"><p><a href="https://twitter.com/search/%23pfiseminar">#pfiseminar</a> NAISTのA氏が言っていたけど、言語処理学会に出てくるような話の XX%は、それと同じ時間を形態素解析の辞書の整備にあてたほうが、精度が良くなる、とのこと。うだうだ悩むより作ったほうが早いことはよくある。Mozcの麻雀・外国地名辞書等はほぼ手作り。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/127043950195384320" data-datetime="2011-10-20T15:30:12+00:00">10月 20, 2011</a></blockquote>
