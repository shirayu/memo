
# コーパス内の頻度

## 意味と頻度
<blockquote class="twitter-tweet" lang="ja"><p>日本語の学習者が「時間をかける」の代わりに「時をかける」（←普通こうは言わない）と言えるか調べるべく、Googleで検索したとします。すると、ヒット数が大きいので、そう言えると思い込むでしょう。しかし、「時をかける」のヒット数が多いのは『時をかける少女』という作品があるためで。</p>&mdash; Fumiaki Nishiharaさん (@f_nisihara) <a href="https://twitter.com/f_nisihara/status/206374293725134849" data-datetime="2012-05-26T13:20:40+00:00">5月 26, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

大規模コーパスの頻度を使って，色々することが多いが，
単純な頻度だけでは，
(1-gramだけでなく，n-gramも)意味を考慮できない．
コーパスで統計処理する際の語義曖昧性解消とというのも，
なかなかの悩ましい．
（そして実際に困ることもある）

## トークナイズ
<blockquote class="twitter-tweet" lang="ja"><p>検索エンジンのヒット数を使って議論するとき、注意すべきなのは、自分の調べたいことと検索エンジンが拾ってくることが違うことがあるということです。大昔は、「義経」について調べたいつもりが、「資本主義経済」まで引っかかるということがありました（資本主*義経*済）。</p>&mdash; Fumiaki Nishiharaさん (@f_nisihara) <a href="https://twitter.com/f_nisihara/status/206373594752745472" data-datetime="2012-05-26T13:17:53+00:00">5月 26, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

トークナイズしてからインデックスするというのは，検索エンジンの常識なので，
その語のトークナイズに失敗したのであろう．
しかし，検索エンジンは多種多様なドメインの文章をトークナイズしないといけないので，
なかなか大変だろうなあ．
ドメイン適応とかしているのかなあ．


# 言語のTTR

<blockquote class="twitter-tweet" lang="ja"><p>日本語のテキストを解析し慣れていないせいか、総語数が約11万語で異語数が5674語という結果に「異語数が少なすぎる。。。処理ミス？」と思ったが、普通にChaSenで解析しても、RMeCabで解析してもほぼ同じ数なので、そんなものなのかと驚く（英語と比べると、TTRが異様に低い）。</p>&mdash; Yuichiro Kobayashiさん (@langstat) <a href="https://twitter.com/langstat/status/168031314707087362" data-datetime="2012-02-10T17:59:21+00:00">2月 10, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

TTRとはType-Token Ratioの略で，異なり語数を延べ語数で割った値．