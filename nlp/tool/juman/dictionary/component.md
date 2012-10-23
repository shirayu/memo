
# 辞書の構成

- 文法辞書
    - JUMAN.grammar （品詞分類を定義）
    - JUMAN.katuyou （個々の活用型の具体的な活用形の一覧を定義）
    - JUMAN.kankei （活用する各品詞に対して活用型の一覧を定義）
    - JUMAN.connect.c（連接関係を定義する連接規則の集合）
- コンパイル後の文法辞書
    - jumandic.tab （連接対応表）
    - jumandic.mat （連接行列）
- 形態素辞書
    - Assert.dic
    - AuxV.dic
    - ContentW.dic
    - Demonstrative.dic
    - Emoticon.dic
    - Noun.hukusi.dic
    - Noun.keishiki.dic
    - Noun.koyuu.dic
    - Noun.suusi.dic
    - Postp.dic
    - Prefix.dic
    - Rengo.dic
    - Special.dic
    - Suffix.dic
- コンパイル後の形態素辞書形態素辞書
    - jumandic.dat （形態素データベース）
    - jumandic.pat （パトリシア木によるインデックス）


# 形態素辞書の仕様


    〈形態素定義〉       ::=    (〈#形態品詞名〉〈形態素情報の並び〉) |                        
                           (〈#形態品詞名〉(〈#品詞細分類名〉〈形態素情報の並び〉))        
    〈形態素情報の並び〉  ::=    〈形態素情報〉 | 〈形態素情報〉〈形態素情報の並び〉        
    〈形態素情報〉        ::=     (〈見出し語情報〉〈読み情報〉〈活用型情報〉〈意味情報〉)        
    〈見出し語情報〉      ::=     (見出し語 〈見出し語内容の並び〉)         
    〈見出し語内容の並び〉::=    〈見出し語内容〉 | 〈見出し語内容の並び〉        
    〈見出し語内容〉      ::=     〈#見出し語表記〉 | (〈#見出し語表記〉)  |         
                             (〈#見出し語表記〉〈#数値〉)         
    〈読み情報〉        ::=     (読み 〈#読み表記〉)         
    〈活用型情報〉      ::=     (活用型 〈#活用型名〉) | NIL         
    〈意味情報〉        ::=     (意味情報 〈#意味記述〉) | NIL



