# GnuCash
この情報は
- GnuCash 2.4.10
-- リビジョン: r21973
- Ubuntu 12.04
での情報です

#日本のマーケットの情報を表示できるようにする

- ``cpan``で``Finance::Quote``がインストールされているディレクトリを確認する

```
sudo cpan
    > i Finance::Quote
    INST_FILE    /usr/share/perl5/Finance/Quote.pm
```

- (INST_FILE)のディレクトリ以下の``Quote``に移動
    - この場合は``/usr/share/perl5/Finance/Quote/``
- ``sudo wget https://raw.github.com/LiosK/Finance--Quote--YahooJapan/master/lib/Finance/Quote/YahooJapan.pm``
- ``FQ_LOAD_QUOTELET='-defaults YahooJapan' gnucash``で起動

# 為替情報を表示できるようにする
- 次のパッチをQuote.pmにあてる [(参考)](https://rt.cpan.org/Public/Bug/Display.html?id=74660#txn-1038090)
```
    --- lib/Finance/Quote.pm.orig   2012-02-15 10:28:52.000000000 +0100
    +++ lib/Finance/Quote.pm        2012-02-15 10:30:04.000000000 +0100
    @@ -246,13 +246,15 @@
    my $tb = HTML::TreeBuilder->new_from_content(decode_utf8($data));

    # Find the <div> with the data
    -  my $div = $tb->look_down('id','yfi_quote_summary_data');
    +  my $div = $tb->look_down('id','yfi_investing_content');
    # Make sure there's a <div> to parse.
    return undef unless $div;

    -  # The first <b> should contain the quote
    -  my $rate_element=$div->look_down('_tag','b');
    -  # Make sure there's a <b> to parse.
    +  # Find the <span> that contains the quote
    +  my $lcfrom = lc($from);
    +  my $lcto = lc($to);
    +  my $rate_element=$div->look_down('id', "yfs_l10_$lcfrom$lcto=x");
    +  # Make sure there's a <span> to parse.
    return undef unless $rate_element;

    my $exchange_rate=$rate_element->as_text;
```
- ``Finance::Quote 1.17``ではパッチをあてる必要はなかった

