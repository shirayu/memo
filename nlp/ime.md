
# IMEと語彙
<blockquote class="twitter-tweet" lang="ja"><p>IME用の辞書を作る時、頻度だけに頼ってネットから組み合わせを取るとノイズだらけになる一方でまだ使われている語彙を落としたりするし、人手の辞書だけを使うと死語が残る上に新語が入らない。iOSの辞書が、ノイズなしに新語をカバーして死語を落としているのは、陰に苦労があるのだろうな。</p>&mdash; Hiroshi MANABEさん (@takeda25) <a href="https://twitter.com/takeda25/status/173389573190201344" data-datetime="2012-02-25T12:51:10+00:00">2月 25, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" lang="ja"><p>iPhoneのIMEは自分にとってはかなり理想に近い。日本語の基本語彙（「賎民」、「白痴」、「屠殺」などを含めた、辞書に載っているような単語）を押さえた上で、「スクショ」「チラ見」「卒アル」などの新語もある。固有名詞も、「らき☆すた」「怒首領蜂」などツボを押さえて入れてある。</p>&mdash; Hiroshi MANABEさん (@takeda25) <a href="https://twitter.com/takeda25/status/173226243234344960" data-datetime="2012-02-25T02:02:09+00:00">2月 25, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


<blockquote class="twitter-tweet" lang="ja"><p>自分の理想のIMEは、固有名詞は多少少なくてもいいから、基本的な変換で残念な間違いをせず、また皆にとって馴染みのある表現は俗語や卑語であってもちゃんと変換するようなもの。「マン毛」、「粗チン」とかだって変換してほしい。だって日本語じゃん。</p>&mdash; Hiroshi MANABEさん (@takeda25) <a href="https://twitter.com/takeda25/status/173223620733173760" data-datetime="2012-02-25T01:51:44+00:00">2月 25, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


<blockquote class="twitter-tweet" lang="ja"><p>ATOKは新用言をもっと本気でやった方がいいんじゃないだろうか。チャラいとか拒否られたとかも変換できないし。</p>&mdash; Hiroshi MANABEさん (@takeda25) <a href="https://twitter.com/takeda25/status/171461130693255168" data-datetime="2012-02-20T05:08:13+00:00">2月 20, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


<blockquote class="twitter-tweet" lang="ja"><p>ATOK 使ってみてる。話し言葉モードが弱い。「すぐでれる」で「すぐデレる」が候補にない、「かそりすぎ」は「賀曽利過ぎ」、「ぼけまくり」で「ボケまくり」がない、「そっこうぽちった」は「速攻歩散った」、「いじりがいがある」は「維持利害がある」、「ぶれない」で「ブレない」がない。</p>&mdash; Hiroshi MANABEさん (@takeda25) <a href="https://twitter.com/takeda25/status/171455677036896256" data-datetime="2012-02-20T04:46:33+00:00">2月 20, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


# IMEの評価

<blockquote class="twitter-tweet" lang="ja"><p>IMEのSharedTaskが議題になったが、単にひらがな→漢字の精度比較だと微妙。その手の精度は成熟しているし、あまり役に立たないのも経験済み。下手したらSMT(Moses)とかいう人がいそうでIMEらしさがない。サジェスト・学習・スペルコレクション・UX・圧縮あたりが面白い</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/136444928707399680" data-datetime="2011-11-15T14:06:20+00:00">11月 15, 2011</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

- [スマートフォン上のIMEの変換精度とはどうあるべきかを考えさせられる動画](https://plus.google.com/107334123935896432800/posts/fAytqvRXgqo)

# 後続語の予測処理
<blockquote class="twitter-tweet" data-in-reply-to="128811290033520640" lang="ja"><p>NLP2011 での以下の発表が近いのかな。C5-4 頻出文脈に基づく分野依存入力支援 ○海野裕也, 坪井祐太 (日本IBM) RT @<a href="https://twitter.com/nokuno">nokuno</a> 最新版のmozcが予測変換でSVMを使うのをやめて，確率と長さの積を使うようになっていたようだ．興味深い</p>&mdash; Zelchさん (@zzzelch) <a href="https://twitter.com/zzzelch/status/128820152706924545" data-datetime="2011-10-25T13:08:12+00:00">10月 25, 2011</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

[mozc/src/prediction/dictionary_predictor.cc](http://code.google.com/p/mozc/source/browse/trunk/src/prediction/dictionary_predictor.cc) を読んでみると，SVMの利用をやめた理由として，

    Before this simple algorithm, we have been using an SVM-base scoring,
     but we stop usign it with the following reasons.
     1) Hard to maintain the ranking.
     2) Hard to control the final results of SVM.
     3) Hard to debug.
     4) Since we used the log(remain_length) as a feature,
        the new ranking algorithm and SVM algorithm was essentially
        the same.
     5) Since we used the length of value as a feature, we find
        inconsistencies between the conversion and the prediction
        -- the results of top prediction and the top conversion
        (the candidate shown after the space key) may differ.

と説明している．
