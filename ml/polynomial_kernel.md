


# 多項式カーネル != 組み合わせ

<blockquote class="twitter-tweet" lang="ja"><p>2次の多項式カーネルを使うのと，自分で全素性の組み合わせを作って線形カーネルを使うのと，何が違うの??</p>&mdash; Yuta Hayashibeさん (@shirayu) <a href="https://twitter.com/shirayu/status/154113982020583426" data-datetime="2012-01-03T08:16:51+00:00">1月 3, 2012</a></blockquote>


<blockquote class="twitter-tweet" data-in-reply-to="154113982020583426" lang="ja"><p>@<a href="https://twitter.com/shirayu">shirayu</a> 自由度．</p>&mdash; Kazushi Ikedaさん (@kazushi_) <a href="https://twitter.com/kazushi_/status/154119293515206656" data-datetime="2012-01-03T08:37:57+00:00">1月 3, 2012</a></blockquote>

<blockquote class="twitter-tweet" data-in-reply-to="154121374821126144" lang="ja"><p>@<a href="https://twitter.com/shirayu">shirayu</a> 真の解がその空間に含まれているなら多項式カーネルの方がオーバーフィットしにくい．我田引水すると<a href="http://t.co/sWTRdPcj" title="http://hawaii.naist.jp/~kazushi/comments.htm">hawaii.naist.jp/~kazushi/comme…</a> の18と25．</p>&mdash; Kazushi Ikedaさん (@kazushi_) <a href="https://twitter.com/kazushi_/status/154123534694756352" data-datetime="2012-01-03T08:54:48+00:00">1月 3, 2012</a></blockquote>


- 18 池田 和司: 多項式カーネルをもつカーネル法の幾何学と学習曲線, 電子情報通信学会論文誌, J86-D-II/7 (2003), 918-925, 情報論的学習理論特集号招待論文.
- 25 Kazushi Ikeda: An Asymptotic Statistical Theory of Polynomial Kernel Methods, Neural Computation, 16/8 (2004), 1705-1719.


# 2次の多項式カーネルと主問題

<blockquote class="twitter-tweet" lang="ja"><p>SVMの学習は、線形カーネル+主問題+バイアス無しでやると高速になることは知られている(liblinearはこのアプローチ)。で、最近の計算機は十分メモリあるしNLPの素性は疎なので、2次の多項式カーネルも主問題で解けるんじゃねと思ったら、うまくいった。絶対誰かやってると思うけど</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/256705270430961664" data-datetime="2012-10-12T10:38:00+00:00">10月 12, 2012</a></blockquote>

<blockquote class="twitter-tweet" data-in-reply-to="256705270430961664" lang="ja"><p>@<a href="https://twitter.com/taku910">taku910</a> 理解不足で的外れかもしれませんが、主問題を解いているのであれば普通の組み合わせ素性とほとんど一緒になりませんか？それとも主問題でもカーネルを使うことで効率化できたりしますか？</p>&mdash; Graham Neubigさん (@neubig) <a href="https://twitter.com/neubig/status/256708907559444481" data-datetime="2012-10-12T10:52:27+00:00">10月 12, 2012</a></blockquote>

<blockquote class="twitter-tweet" data-in-reply-to="256708907559444481" lang="ja"><p>@<a href="https://twitter.com/neubig">neubig</a> 一緒になります。主問題を解くのでカーネルは出て来ません。実際には双対問題を解くのですが、同時に主パラメータも更新します。主パラメータは学習の高速化(具体的には分離平面の距離計算)に使われます。距離を双対パラメータだけで解くと学習データ数に比例した計算量が必要です</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/256720953625673728" data-datetime="2012-10-12T11:40:19+00:00">10月 12, 2012</a></blockquote>

<blockquote class="twitter-tweet" data-in-reply-to="256720953625673728" lang="ja"><p>@<a href="https://twitter.com/taku910">taku910</a> やはりそうですね。「カーネル」という言葉が出てきたので何かのトリックがあるのではないかと思ったのですが、主問題を解いている限りあまりトリックのしようがないですね。</p>&mdash; Graham Neubigさん (@neubig) <a href="https://twitter.com/neubig/status/256742624839471104" data-datetime="2012-10-12T13:06:26+00:00">10月 12, 2012</a></blockquote>

<blockquote class="twitter-tweet" data-in-reply-to="256742624839471104" lang="ja"><p>@<a href="https://twitter.com/neubig">neubig</a> 実際には、双対パラメータの更新が必要なときにはじめて主パラーメータの更新(組み合わせ素性の重みの更新)を行うので、あらかじめ全展開するよりも効率がよいと思います。(比較したわけではないですが) 特に、サポートベクターの数が少ない時には高速になると思います。</p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/256971131096010753" data-datetime="2012-10-13T04:14:26+00:00">10月 13, 2012</a></blockquote>

<blockquote class="twitter-tweet" lang="ja"><p>@<a href="https://twitter.com/neubig">neubig</a> 多項式カーネルを陽に展開する話は以前にやってて、それを学習時にも適用しただけです。最終結果は多項式カーネルを使ったものと同一になります。配布するモデルはサイズの節約のために双対パラーメータにしてテスト時に近似的に展開します。<a href="http://t.co/9sHeQvpQ" title="http://acl.ldc.upenn.edu/acl2003/main/pdfs/Kudo.pdf">acl.ldc.upenn.edu/acl2003/main/p…</a></p>&mdash; Taku Kudoさん (@taku910) <a href="https://twitter.com/taku910/status/256973547757531136" data-datetime="2012-10-13T04:24:02+00:00">10月 13, 2012</a></blockquote>



<blockquote class="twitter-tweet" data-in-reply-to="256973547757531136" lang="ja"><p>@<a href="https://twitter.com/taku910">taku910</a> ああ、なるほど！確かにサポートベクトルでない事例は最終的な重みに影響しないのでカーネルの計算だけですみますね。勉強になります。</p>&mdash; Graham Neubigさん (@neubig) <a href="https://twitter.com/neubig/status/257629233579429888" data-datetime="2012-10-14T23:49:30+00:00">10月 14, 2012</a></blockquote>


<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>



# 補足
- 線形計画問題
    - 目的関数と制約条件が全て線型性を有する最適化問題
- 主問題（Primary problem）
    - 目的関数は n 個の変数を線形に組み合わせたもの
    - m 個の制約条件があり、それぞれが n 個の変数の線形な組合せの上限を定めている
    - 問題は、制約条件を満たしつつ、目的関数の値を最小化する変数の値の組合せを求めることである。解は n 個の値のベクトル（リスト）であり、それらの値を目的関数に入力することで最小値が得られる。
- 双対問題(Dual problem)
    - 主問題の補問題
    - 目的関数は m 個の値の線形な組合せ
    - これらは主問題の m 個の制約条件（上限値）それぞれに対応
    - n 個の双対制約条件（dual constraints）があり、それぞれが m 個の双対変数（dual variables）の線形な組合せの下限を定めている
    - この場合、目的関数の値を最大化する双対変数の値の組合せを求める
- 双対定理(duality theorem)
    - 主問題と双対問題のいずれか一方が最適解を持つなら、もう一方も最適解を持ち、主問題の最小値と双対問題の最大値は一致する。

[Wikipedia](http://ja.wikipedia.org/wiki/%E5%8F%8C%E5%AF%BE%E5%95%8F%E9%A1%8C)より

