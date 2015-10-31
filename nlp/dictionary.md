

# 辞書づくりについて
[辞書づくりについて](https://plus.google.com/107334123935896432800/posts/VFRHDAZ28eB)より，

> 一方、経験上タグ付きコーパスを作るのは苦痛だ。作ったところでシステムがどれだけ向上するかどうか予測不可能だし、ほぼランダムに生成される文をつらつら眺めても何も面白くない

もっと辞書について勉強したいなあ．．
特に項構造解析について，「アノテーションor辞書づくり」についての記述が非常に参考になる．


    私も述語項構造解析やゼロ代名詞問題のアノテーション+機械学習のシステムを作ったことがあるが、満足のいくシステムはなかなか作れなかった。
    学習曲線があるところまでは上がるがすぐにフラットになってどんなにデータを増やしてもにっちもさっちもいかないのだ。
    じっくり考えてみれば、このようなアノテーション方法ではうまくいかないことは明白なのだが、機械学習にとりつかれていた以前の私はそんなことまで考えが及ばなかった。
    このような問題を解くには、動詞 食べるの語彙選択制限や名詞寿司・私の意味的カテゴリーといった語彙に関する知識が必要であるし、逆にそのような知識さえあれば単純な推論で同定が行える。
    すなわち、辞書を作成することも格解析を解く方法になりうるし、実はそちらのほうが自然なのかもしれない。(もちろん併用はできる)
    この方法論を実践したパーザーがKNPである。

tweetもされていた．

<blockquote class="twitter-tweet" lang="ja"><p>述語・項構造を機械学習でやると、なんでこんな簡単なことができんのかとモヤモヤしてくる。思うに、こういう高度なタスクは個々のプリミティブな事実の上での単純な推論で導けるているはず。それならばやみくもにタグ付けするより、推論に使われた根拠とその推論過程を明らかにするほうが有益なのかも</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/195542105916047361" data-datetime="2012-04-26T15:57:25+00:00">4月 26, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>



私も今まで，コーパス+機械学習しか頭になかったので，このような指摘で鱗が落ちた様な気分に．

KNPの格解析は大規模格フレーム辞書に基づいており，
この辞書を大規模化するほど，精度が向上するらしい．


#Juman

<blockquote class="twitter-tweet" lang="ja"><p>金曜日、BCCWJのとある中の人と議論。最後には本題からそれてUnidicのダメ出しで盛り上がる。まともに言語処理やってる人なら、Unidic/BCCWJが応用で必要な問題をほとんど解いていない(たくみに回避している)もどかしさを共有できる。結局JUMANがおすすめのこと</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/239723700335804416" data-datetime="2012-08-26T13:59:18+00:00">8月 26, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" lang="ja"><p>Jumanの体系はやはり素晴らしいなー「食べるのが」と「食べるのです」の「の」の扱いがipadic/unidic だと、非自立名詞なのに対し、Jumanでは、前者は名詞、後者は助動詞「のだ」の活用としている。応用上これは区別してくれた方が嬉しい。前者は「こと」と言い換えられる</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/243002898584309760" data-datetime="2012-09-04T15:09:40+00:00">9月 4, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


#unidic
<blockquote class="twitter-tweet" lang="ja"><p>unidicが非自立と自立動詞の区別をなくして可能性に基づく形式にしたのはやり過ぎな気がする。この区別は応用でめちゃめちゃ大事。「食べてみる」と「映画をみる」の「みる」が区別できないのは不便すぎる。そのうち可能性の部分を当てる解析器が出てきそう。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/177724714297458688" data-datetime="2012-03-08T11:57:28+00:00">3月 8, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" lang="ja"><p>以前伝先生とお話したときに、Unidicでは伝統的な活用表による活用処理は破綻しているとおっしゃっていた。活用は全展開している。確かに同じ活用型・活用形でも表記がことなるものが散見される。活用表も便利なときがあるので、なんともかんとも。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/108054587918913536" data-datetime="2011-08-29T05:53:15+00:00">8月 29, 2011</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


