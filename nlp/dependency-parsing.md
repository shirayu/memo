
# 係り受け

## 文節係り受けの難点

<blockquote class="twitter-tweet" data-in-reply-to="176672949875646464" lang="ja"><p>@<a href="https://twitter.com/taku910">taku910</a> あえて文節係り受けの難点をいえば「木が切られた」と「健が髪を切られた」の統語構造の違いを反映できないとかでしょうか。文節という単位がおおきすぎる例です。体言と用言で粒度をわけた方がよい気がしますね。体言の内部構造は統語にいらない。</p>&mdash; 高岡一馬さん (@klmquasi) <a href="https://twitter.com/klmquasi/status/176833781645320193" data-datetime="2012-03-06T00:57:13+00:00">3月 6, 2012</a></blockquote>

[単語単位の係り受けの違和感](https://plus.google.com/107334123935896432800/posts/KHoDsDssycf)

<blockquote class="twitter-tweet" data-in-reply-to="176833781645320193" lang="ja"><p>@<a href="https://twitter.com/klmquasi">klmquasi</a> 体言と用言で変えるのには賛成です。機能表現は英語の助動詞みたいに振る舞うので一つの独立とした語として扱ったほうがいいのかもしれません。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/177236509194326016" data-datetime="2012-03-07T03:37:31+00:00">3月 7, 2012</a></blockquote>

<blockquote class="twitter-tweet" lang="ja"><p>品詞は雑多hな処理に便利なんですよね。毎日そんなことばっかりです。「ら抜き・れ足す言葉の一覧を作る」「五段動詞が可能動詞化(一段化)されたものの一覧」「特定の動詞につきやすい機能語列の一覧」などなど.... 研究者はこんなことはやらんでしょうが...</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/140113133611134977" data-datetime="2011-11-25T17:02:28+00:00">11月 25, 2011</a></blockquote>

<blockquote class="twitter-tweet" lang="ja"><p>@<a href="https://twitter.com/unnonouno">unnonouno</a> 昼間言っていた、単語ペアのPMIで係り受けスコアを計算するのはこれです。bit.ly/o3WueG 次のは P(a,dir|h) をスコアにしています。bit.ly/rgsbhd 英語の文では隣にかけるベースラインに負けています。bit.ly/nB7HsN</p>&mdash;Murawakiさん (@murawaki) <a href="https://twitter.com/murawaki/status/116469369638371328" data-datetime="2011-09-21T11:10:36+00:00">9月 21, 2011</a></blockquote>

## 品詞体系

<blockquote class="twitter-tweet" lang="ja"><p>Unidicの品詞体系で係り受け解析やるのはいろいろ工夫が必要そう。短単位なので主辞を取り出しても係り受けに必要な情報が抜け落ちている可能性が大きい。また、可能性に基づく品詞体系なので曖昧性を解消する部分を構文解析でやらないといけない。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/100095910364725248" data-datetime="2011-08-07T06:48:19+00:00">8月 7, 2011</a></blockquote>

## コーパス

<blockquote class="twitter-tweet" lang="ja"><p>KNBCコーパスは、格解析の時と係り受け解析とでは違うユニットを使っているみたい。ちゃんとそのへんを考慮すると、まともな文節区切りになった。ライセンス的には問題なさそうなので、CaboChaの学習データに入れてみようかな。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/251695826160730113" data-datetime="2012-09-28T14:52:15+00:00">9月 28, 2012</a></blockquote>

## 英語

<blockquote class="twitter-tweet" data-in-reply-to="94021210060505088" lang="ja"><p>@<a href="https://twitter.com/zzzelch">zzzelch</a> 英語の構文解析の変遷を見ると面白いです。10年前はPTBスタイルでしたが、そりゃ本質的ではないし応用しにくいということで係り受けになりました。その最初の提唱者は松本先生(山田&松本論文)です。その後Nirve&Ryan, CoNLLと続き係り受けが成熟しました。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/94060426706419712" data-datetime="2011-07-21T15:05:27+00:00">7月 21, 2011</a></blockquote>

<blockquote class="twitter-tweet" data-in-reply-to="94021210060505088" lang="ja"><p>@<a href="https://twitter.com/zzzelch">zzzelch</a> PTBスタイルは使いづらいという動機づけでもう一つ生まれたのはshallow parsingです。これは日本語の文節まとめ上げに近い。当時松本研ではshallow parsing+係り受けで日本語ライクにやってもいいのではといった議論がありました。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/94062297047248896" data-datetime="2011-07-21T15:12:53+00:00">7月 21, 2011</a></blockquote>

<blockquote class="twitter-tweet" data-in-reply-to="94021210060505088" lang="ja"><p>@<a href="https://twitter.com/zzzelch">zzzelch</a> 実際にはshallow parsing も93%程度の精度しか出せないので、そのアプローチはエラーの積算問題があるので消えました。ただ shallow parsingという方法論や base phrase単位の分割はテキストマイニング等で応用されているようです</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/94062800850255872" data-datetime="2011-07-21T15:14:53+00:00">7月 21, 2011</a></blockquote>

<blockquote class="twitter-tweet" data-in-reply-to="94021210060505088" lang="ja"><p>@<a href="https://twitter.com/zzzelch">zzzelch</a> 英語のパージングの歴史を見ると、結局、本質的・直感的な正しさと応用のしやすさで生き残るかどうか決まるのではないかと思います。そのどちらの側面からみても日本語単語単位は微妙... 例えば機能表現内の単語係り受けは本質的かと言われるとそうは思わない。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/94064387794538496" data-datetime="2011-07-21T15:21:12+00:00">7月 21, 2011</a></blockquote>
