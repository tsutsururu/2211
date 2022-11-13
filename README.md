# 2211


# 178D  Redistribution  diff 875

解答遷移 AC

計 1時間 over

備考

➀　思考

メモ化再帰で解けるし、ちょうどいいからエラストテネスみたいにこの問題でお勉強しよう! → 再帰関数の変数 や return の仕組みが意味わからん過ぎて時間が死ぬほど経過　→　諦めて素直にdpっぽい感じのコード書いたら通って意味不明

③ 解法

f(S) は f(3) ～ f(S-3) を呼び、答えがそれらの和 +1 になる。これを実装するには f(S,ans) の返り値を ans として、ans に for ループで回した f(3,1) ～ f(S-3,1) を足し合わせればよい。


# dfs 再帰勉強編

・ Q1 箱の中

bfsすれば dist[X] が答え。

dfs する場合であっても結局距離をリストで管理しなければいけないので bfs でいい。

・ Q5 子孫の数

dfs は帰りがけで処理できるメリットあり


# 1102

# 204C Tour  diff 629  再

解答遷移 RE AC

計 11:21 + 05:00

備考

➀　思考

始点を変えて dfsしてたどり着ける点の数をカウントしていけばよいと考えた。始点を変える際に、訪れた都市を管理するリストの初期化が必要。




# 1104

# 計算量 についての再確認

➀ 係数は無視 O(2N) → O(N)

![image](https://user-images.githubusercontent.com/109026838/199887431-66876afe-00cc-42e0-aec7-fb89f56235e6.png)

![image](https://user-images.githubusercontent.com/109026838/199887444-d18e30dd-a1a4-4ea6-adcb-c80ffb30a3ed.png)

そもそもオーダーは単なる見積もりなのである。


➁ for ループ

for i in range(N):
  
  for j in range(N):
    
    if j>100:
    
      break
    
    O(1)

のような処理を考えると計算量は O(N^2) である。なぜなら計算量は最悪の場合を考えるので、break が起こらなかった場合 N^2 回 O(1)の計算が発生し、O(N^2)となる。break や continue の解釈はこういうことであり、for ループ の i を進めること自体に O(1)かかっているわけではない。実際 break された結果 100回 O(1) が行われたなら、実際の計算量はO(100)である。つまり、ただポインタを進めるだけのループ処理ならば 計算量は 0 になるわけである。



# 183C Travel  diff 335　　再
 
解答遷移 AC

計 07:18

備考

➀　思考

 itertools.permutation で順番を全探索して時間を比較するだけ。(0,) + 順番 + (0,) で都市0 からスタートして 都市0 に戻る経路をタプルで表現すればよいと考えた。

➁ 初見 dfs 

dfsした場合でも 7! 回再帰するだけなので十分高速


# 226C Martial artist   diff 539  再

解答遷移 AC

備考

➀ 思考

覚えるべき技を根としたグラフを dfs,bfs して時間を累積していくだけ。先に覚えるべき子の処理を完了してから帰りがけで時間を累積する処理と、行きがけで先に累積する処理に違いはないので問題文を素直に受け取らず後者で実装した。


# 211D Number of Shortest paths   diff 755   再

解答遷移 AC

備考

➀ 思考

bfsで各頂点の最短距離を調べあげ、再びbfsして経路数をdp的に数え上げる処理を考えた。

➁ 解法

bfsで各頂点の最短距離を求めながら、調べている経路が最短経路であるならばdp的に経路数を数え上げる処理を行えば 一回のbfsで済ませられる。

③ dfs 計算量

bfsでは、経路数の数え上げ処理で同じ頂点を何度も調べることがあるものの、同一辺は高々1回しか探索されない。したがって計算量は O(M)になる。

一方、dfsでは同じ経路であっても何度も訪れなければいけない。よって明らかにbfsよりも計算量が多く、この問題を解答するアルゴリズムとして適していると言えない


# 270C Simple path  diff 625   本番後初

解答遷移 AC

計 13:14

備考

➀　思考

Xを根にしたグラフを作成し、Yまでの経路を出力すればよいと考えた。これは、dfs or bfs で X から探索を初めて、次の頂点の親が今の頂点であることを連結リスト的に記録することで実装できると考えた。探索後に Y から親を que にappendleft していけば、求めるべき順番が得られる。計算量はdfs,bfsどちらでも O(N+M) 


# 275D Yet Another Recursive Function  diff 606

解答遷移 AC

計 02:49

備考

➀ 思考

メモ化再帰するだけ

➁　計算量

O(引数の種類) になる。引数はN//(2^i* 3^j) と表現できることに注目すると、これは1以上だから、i <= log2N ,j<=log3N となる。したがってs素因数分解の要領で 種類は (i+1)* (j+1) 以下なので O(log2N * log3N) となる。これは N<=2000　の場合に十分すぎるほど高速である。


# 1105

# 256B Batters  diff 83

解答遷移 AC

計 05:26

備考

➀　思考

逆順で累積和とって4以上の個数を判定


# 136D Gathering Children   diff 794

解答遷移 AC

計 26:39

備考

➀　思考

LR の左側に存在する子供は、Lまでの領域に留まし、右側に存在する子供はRを超えることはない。また、子供が最終的に行き着く場所は RL のどちらかになる。例えば S= RRRRLRL  のとき、[0,0,0,2,3,1,1] となる。したがって圧縮して RLRL を考えればよいのかとも思ったが、それらが前から何番目の R,L だったかの情報が落ちることが不便だと考え圧縮せずに考えることに。→ RL の右側にRが何個、左側にLが何個連続しているかが重要なので、Sを前から探索してRを、後ろから探索してLを数え上げてリストに格納。あとは、これを前から探索して、R があればその位置に個数を2で割った値を切り上げたものを累積し、その後ろの位置に個数からそれを引いた値を累積する。Lがあればその位置に個数を2で割った値を切り上げた値を累積し、その前の位置に個数からそれを引いた値を累積する。これで最終的な子供の数を求められた


# 148E Double Factorial  diff 818

解答遷移 AC

計 27:40

備考

➀　思考

N が 奇数なら 0 、偶数なら 10 の倍数の数が答え　→ 合わない → よく考えると、100 は末尾に0を2個追加するので、10の倍数,100の倍数,1000の倍数と数え上げる必要があった → 合わない → 調べる 5 の倍数を数えるとの記事しかなく、今は偶数しか数えないから10を数えているけど、制約なしならそんなことわかってんだ　となる　→ しかし 50 * 12 = 600 になって末尾の 0 が増えることに気づく。→ 奇数を数えないようにしながら 5^x の個数を数え上げてAC

なお、5^x の個数は (N//5^x)//2 として数え上げた。始まりが奇数の5であり、偶数のみ数え上げればよいので //2 した。




# 1105 復習 

# 276D   Divide by 2 or 3

解答遷移 WA × ∞

計 1時間over

備考

➀　思考

まず、aiが2,3以外の素数であると目標は達成できない。素数列挙　→ そんなことしなくても ai が 2 か 3 で割り切れるかで判定できる　→  2 か 3　でしか割れない　場合と、2でも3でも割れる場合を考えれば良さそうだな → 全然よくない　→ 素因数分解の要領で考えるのが良さそう　→ めちゃくちゃ wa をだし、最終的に解答できず終了


➁　解法

aiを素因数分解して 2^xi * 3^yi * zi となったとき、 z1=z2=...zi=..zn である必要がある。aiを2,3で割りきった値 z をXに格納し、set(X)の長さが1 であれば 操作で a1=a2=...an とすることができ、そうでなければできないと判定できる。

③　反省

解法は全く正しいのだが、「5,7,9 などの 2で割れない値があり、aiすべてを操作によってこの素数に一致させられる状況」を、自分で勝手にコーナーケース化してしまった。思考を軌道修正して素因数分解までもっていけたものの、そこまでに積み重なったWA の数、迫る時間に冷静さを失い、サンプルを作ってもコーナーケースを発見できず解答することができなかった。

改善

➀ 初見案の重要性

今回、初見案がめちゃくちゃだったために様々な問題が生じた。➀ 軌道修正 ➁ コーナーケース化　

この問題を解決するには自分の初見案力を向上させるべきだと感じる。

よって ここしばらく、1, 緑以下は5分でコードを書かず初見案を作る 2,それ以上はふつうにとく

の2パターンの演習を行う


# 1106

# 153D Caracal vs Monster  diff 129

解答遷移 AC

初見案 01:53  　〇  

計 05:50

備考

➀ 初見案

メモ化再帰すれば良さそう。ans=1 として、引数 x > 1 ならば ans+= f(x//2) * 2 として ans を返り値とすれば良さそう　→ AC


# 148D Brick Break  diff 182

解答遷移 AC

初見案 01:28  △ : 条件を満たさない場合を考察していない

計 04:47

備考

➀　初見案

残すものがどれか前から探索して調べ、N - その個数 が砕く個数になる。→ coding → 条件を満たさない場合があることを初見で抜け落していた。すべて砕くことはできないから、残す個数が0 の場合に条件を満たさないとして -1 を出力すればよいと判断　→ AC

# 131D Megalomania   diff 588

解答遷移 AC

初見案 03:46 〇

計 07:22

備考

➀　初見案

締め切りがはやいものから仕事を片付けていき、どれかひとつでも締め切りに間に合わないしごとがあれば No とする処理でよさそうなので　ソートして前から順番に判定すれば良さそう。　AC



# ☆ M-SOLUTIONS2020 D  Road to Millionaire  diff 665　難

解答遷移 WA WA AC

初見案 18:57  ×

計 47:02 + 10:00

備考

➀　初見案

売るべきタイミング、買うべきタイミングは Ai と Ai+1 の比較でわかるが、そのタイミングで必ず売買すべきかはわからないので dp　で遷移を把握したい。→ しかし、(100,200),(100,200).... と続いた場合、お金は 1000,0,2000,0,4000 となって、最終的には 1000* 2^40 ≓ 10^15 程度になるのでメモリが足りない。

→ ここで資産を 株の形 と お金の形 の両方で管理し、買うタイミングで株のみを、売るタイミングでお金のみを更新すれば最適化できるのではないかと考える。 これであれば、ある日株を売ることで、一時的に所持金が増えるが実はこのタイミングで売るのが最適ではないようなケースに引っ掛からずに済むと考えた。 ( 例えば 100,150,200 と株価が続くとき、150 の日に売って1500得るより、200の日を待つのが最適となる ) → WA → 最適化の結果 株の形の枚数が同じとき、残金が多くなるようにして AC

なお、100 <= Ai <= 200 から、残金で新しい株を買うことはできないのでこの処理で十分。また、中途半端に株を買う行為は最適にならないだろうと直感で解答した


➁ 解法

売り、買いの順番で日々の遷移を考えると、次に株を買うまでに 以下3通りの状態しかない。1, 前日に株を買わなかった 2, 前日株を買い、翌日売らない 3, 前日株を買い、翌日売る　

ここで翌日に株価が上昇した場合、3 の状態が得をする。なぜなら、1の状態の所持金を 3の状態の所持金が必ず上回るからである。しかしながら、次の日の株価次第でここで売るべきとは限らない。実際 翌日 300円であれば、10株すべて保有して翌日に売るべきである。つまり 2 の状態になるわけだが、これはこの日新たに株を買っても同じ状態になる。新たに手にした 2000 円で 200円の株を　10枚買うのと、この日株を売らなかった状態が一致するわけである。

一方、株価が下落した場合、1 > 3 になる。さらに、この日株を買えば必ず 2の状態より株が増える。 

以上より、毎日持っている株を売ることで、前日に株を買わなかった場合の金額と比較してこの日所持できる最大の金額を把握できる。さらにその後株を買えるだけ買うことで、株の数を更新できるだけでなく、所持金を更新できたがここで売るべきではなかった場合のケアができる。

まとめると、株価によらず毎日売買を行って所持金を最適化することができる。

③　感想

なんとかそれっぽい解答を作成して解答できたが、じっくり考察するととても難しい問題だった。毎日売ることを考えてよいなんてわかんない。考察してなおしっくりこない。難しい。


# 1107 

# 123C Five Transportations  diff 643

解答遷移 AC

初見案 18:26  速度　× ?  正確さ 〇

計 21:04

備考

➀　初見案

一番運べない場所 X がボトルネックになってそうだな　→ X を最後に通過するグループがゴールする時間を答えればよさそう。 → X より前の他の場所で渋滞しても、Xよりかならず早く消化され、結局Xで待つことになる。したがって、X から時刻 t ( Xに一度も待たずに行く場合にかかる時間) に全員スタートする状況を考えても同じことである。 また、対象のグループがXを通過すると、それより後は一切待つ必要がない。よって直感と同じで X がボトルネックになって、X 以外を待たずに通過する時間 + X を最後に通過するグループに必要な時間 答えになることがわかった　


➁　感想

codeing までかかる時間こそ長かったが、ほんとの直感自体は一瞬で、それを証明したり実装する構想を考える時間がほとんどだった。つまり、解答するための初期案(土台)を導く時間自体は悪くないと思われる。


# ☆ 195D Shipping Center  diff 945

解答遷移 WA AC

初見案 06:22  ×

計 1時間で模範解答にいけたものの、ジムの時間で中断。帰宅後AC

備考

➀　初見案

ナップサックっぽいが、どの箱にどの荷物を入れるべきかは一位に決まりそうなので貪欲でどけそうだと感じる → なんなく箱を埋めるのが最適に感じたので、WV を ソートして、クエリごとに箱を生成してソートし容量が小さい箱からできるだけ埋めていく処理を実装した　O(Q * MlogM * N ) より高速 → WA  → なぜ WA なのかわからなかったのでかなり時間をかけてサンプルを作成。→ 価値が大きくて、重さが軽いものから順に、それを入れられる最小の箱にいれるべきだとようやく気付いて AC ( 計算量最高でも O( Q * MlogM * M(M+1)/2  ) ≓ O(50^4 = 3.0* 10^7 ) と推定　したが 100ms もかからなくて謎) 

➁ 感想

カス。初見直感がごみすぎる。本番なら 100 解けてない。価値を最大化しろっつってのに価値ベースで考えないの意味不明。根拠のある直感でしか動いちゃダメ。


# 147C HonestOrUnkind2  diff 977

解答遷移 AC

初見案 05:27  〇

計 24:25

備考

➀　初見案

意味わからんから実験。めちゃくちゃむずそう。 →　サンプル2 を試している途中で だれが正直者であるか決めて矛盾を見つけるのが良さそうと感じる　→ bit 全探索を思いつく!! 制約を見て揺るぎない勝利を確信　→ あとはどうやって実装するかになるが、不親切な人間の証言は矛盾していても構わないので、正直者の証言のみ検証すればよい。N人の証言のテーブルを作って 人i が正直者なら i行目に i の証言 および i が正直者である情報を格納。そうでなければ、i が不親切であることのみ意味を持つ 長さN の情報を格納。このテーブルにおいて、列ごとのに意味を持つ情報に矛盾がなければ、現在仮定している N 人の組み合わせが矛盾を生じないことになる。これをすべての組について考え、正直者の最大値を求めればよいと考えた → 計算量は O (2^15 * 15^2) より十分高速と判断し完了　AC 

➁　感想

パーフェクト神。しかし証言検証はもっと簡単に実装できた。具体的には、ある人が正直者の場合、その人の証言と、現在仮定している組み合わせに矛盾がないか、すべての正直者について知らべればよかったのだ。



# 1108 

# 063C  Bugged  diff 507

解答遷移 AC

初見案 03:09 〇

計 05:44

備考

➀　初見案

合計が10の倍数でなければ全問正解すればよい。そうでない場合、一番配点の低い10の倍数でない問題を解かないことが最適である。すべて10 倍数なら、0点以外とれない。これらのすべてを把握し、自身をもって解答　→ AC


# ☆ 252D Distinct Trio  diff 884

降参

初見案 02:52 ×  20:37 ×

備考

➀　初見案 2 ( 1は覚えていない)

二重ループできないので、探索に工夫が必要　→  個数を管理したり、余事象を考える策は無理そう　→ dp 的に前から順に探索していき、都度数え上げるといけそうだ　→ 具体的には、1 ～ i-1 までに登場する種類を i 番目に管理するテーブルを用いる。すると、[i] <0 なら初めて登場したと考えて table[A[i-1]]+1(A[i-1]を追加) 個から 2個選んで、A[i] とのトリオを作れば条件を満たす。逆に A[i] >=0 なら、二回目以降の登場なので、単純に選ぶことはできない。table[A[i]] から直前にA[i]と同じ値が登場した際にその前にいた値群からは1つ、それ以降に登場した値から1つ選んで、トリオにするか、それ以降に登場した値から2つ選んでトリオにするこ都ができると考えた。(なぜなら、前回のA[i] の前にいた二つとA[i]は既にトリオを形成しているからである。) → サンプル 3があわない。

よく考えるとこの案では、3,1,4,1,5 の状況で、 315,345,145 のみを新たなトリオとして数え上げることはできても 145 を数えることができない。並びによって組み合わせが通用しないパターンがあったのだ。

さらに、1,2,5,4,5,6,7 の場合も、例外となる。



➁　解法

問題分を読み取ることがそもそもできていない。この問題は i<j<k の条件のもと、異なる3要素の組み合わせの総数が問われている。したがって以下3つの解法が考えられる。

1, 余事象

1種類のみ選ぶ組み合わせの総数と 2種類でトリオを作る組み合わせの総数を求める。全体(NC3)よりこれらを引くことで求めるべき要素がすべて異なるトリオの選び方他の組み合わせの総数が得られる


2, 数えやすい選び方に変更する

例えば 1,2,3 から3つ選ぶ場合 (1,2,3) , (2,1,3) , (3,2,1) はすべて同じ組み合わせである。つまり、問題文通りに i<j<k を満たす Ai,Aj,Ak の選び方を求めても、i>j>k を満たす Ai,Aj,Ak の選び方を求めてもそれらの総数は変わらないことがわかる。

ここでは Ai<Aj<Ak を満たす i,j,k の選び方の総数を求める。Aj をAの要素を昇順で探索して調べれば、Aj 未満の個数が　Ai を満たす要素数であり、Aj より大きな値の個数が Ak を満たす要素数になる。これにてO(NlogN) で数え上げられる。もしiを固定した場合には、jの探索も別で行う必要があり、O(N^2)になって間に合わないのだ。

組み合わせは、より便利な代表値を代わりに利用することができることを学んだ。

また、連続性、単調性のある状況下において、3変数を動かす場合 中央を固定すれば、累積和を用いて前後の探索が簡単にできることを学んだ


3, dp

1, 何番目か 2, i-1 番目の要素までに作ることができる長さが3以下の組み合わせの総数 の2つの情報によって遷移を完全に把握できる。


③　感想

問題分を読み取る力、解釈力がたりていないことを痛感することになった。足りていない


# 1109

# aising2020C  XYZ Triplets  diff 378

解答遷移 AC

初見案 〇

備考

➀　初見案

x,y,zの範囲次第で全探索できるな　→ min(x,y,z)^2 * 6 <= n <= 10^6 より x,y,z は100にも満たないとわかる。よって3重ループでx,y,zを探索可能

# 127  Prison  diff 239

解答遷移 AC

初見案 〇

備考

➀　初見案

重複区間を求めればよいが、制約的にくふうが必要　→　連続区間なので imos 法で 格ゲートについて必要なカードをO(1)で求められることに気づいてAC


#  128B  Guidebook  diff 350

解答遷移 AC

初見案 〇

備考

➀　初見案

インデックス番号を追加して、sでソートした順番でインデックス番号を出力すればよいと判断


# 1110 

# 149C NextPrime  diff 172

解答遷移 AC

初見案 00:40 ×  

計 06:05

備考

➀　初見案

二分探索で次の素数を求められそう。→ 区間に単調性、境界性がないので使えないと少ししてわかる。→　普通に素数列挙して次の素数求めればいいか　→ WA →　X以上であることに気づいて修正　AC


# 044B Beautiful Strings  diff 270

解答遷移 AC

初見案 〇

備考

➀　初見案

ふつうに個数を管理して奇数があるか判定するだけ


# 042A Iroha and Haiku (ABC Edition)  diff 89

未 coding

初見案　〇

備考

➀　初見案

5が2つ、7が1つであるか判定するだけ


# 052B  Increment Decrement   diff 156

未 coding

初見案　　〇

備考

➀　初見案

素直に前から全探索して、瞬間値と最大値を二つ管理しながら最大値を更新すればよいと考えた


# 041B  直方体　　diff 385?

未 coding

備考

➀　初見案

( A%MOD * B%MOD * C%MOD )%MOD するだけ


# 107B Grid Compression  diff 448  

解答遷移 AC

初見案 03:01 △(〇)

備考

➀　初見案 

素直に縦横の白マスの個数を管理し、消すべきところを出力しない処理すればいいかな　

➁　思考

最終的な出力時に出力しない行があるのめんどいから、そのような行は消して残った行の個数を管理。その個数に一致する列を出力しない処理でAC

③ 補足

出力しない行を管理しておき、出力時にそのような行を continue しても解けるため初見案は悪くない



# 109C Skip  

解答遷移 AC

初見案 15:23  〇

計 24:35

備考

➀　初見案

いったんスタート地点を無視して、Xのうちのある都市からスタートすることを考えると、D の最大値は都市間の距離の最大公約数のに一致することがわかった。あとはそれと、スタート地点とそこから一番近い都市の距離の最大公約数が答えになると判断

➁　思考

一番近い距離の最大公約数を求めるために二分探索するのもあれだし、各都市との距離の最小値を求めることにした。また、都市間の距離を求める際に都市が1つの場合を含めるとめんどくさいので、N=1　の場合は分けるべきだと考え実装　→ AC


③　解法

実はスタート地点から移動する初めの都市はどこでもよい。なぜなら最も近い都市までのきょりを α とすると、すべての都市までの距離は α + Dx と表せる。D との最大公約数は　α　でも　α+Dx でも同じである。これを利用すればスタート地点と初めの都市の距離を gcd に与えて、各都市間の距離とgcd の最大公約数でgcdを更新し、gcd を出力する処理によって　N=1 の場合でも成立する解答ができる。




# 109B  Shiritori  diff 186

解答遷移 AC

初見案　01:05 〇

計 05:11

備考

➀　初見案

ふつうに前から探索して今の単語に対して、先頭と前の単語の末尾が一致しているか , 既出単語ではないか判定すればよいと考えた


# 1112

解答遷移 AC

初見案 09:38　△ ( 二分探索の精度が甘い 、探索範囲が違った)

計 28:48

備考

➀　初見案

p,q を比較すると、圧倒的に q の制約が厳しいことに注目することわかった。これより 3<= P < 10^6 に気づき、10^6　以下の素数を列挙して q の候補を探索すればよいと考えた。あとは条件を満たすp がいくつか二分探索すれば求められそうだ。

➁ 思考
 
 ok=0 ng= 直前のq+1 として、mid(q^3) <=N を満たすok を更新すればよいと考えていたが、これでは素数以外も含めてしまう。そこでq 以下の素数リストPをあらかじめ用意しておき、Pを二分探索して、N//(q^3) がどこに挿入されるか求めれば条件を満たす個数が分かると考えた。さらに、P[-1]* q^3 >N となれば、次のqの3乗が必ず N を上回ることになるので、ここで探索をうち止められると考えた。　→  サンプル3 があわず考察を深めると、2* 139^3 < N < 131* 137^3 のような例が考えられうち止めが間違っていることに気づく。修正してAC
 
 # 259D Circumferences  diff 947
 
 解答遷移 WA AC
 
 初見案  02:41  〇(△)  接する条件の甘さ
 
 計 32:26 + 05:00
 
 備考
 
 ➀　初見案
 
 移動できる円は中心と半径の関係で求められるので、移動できる円をグラフの形でもってスタートからゴールまでういけるかbfsすればよさそうだ。N=3000 より O(N^2)でも間に合うため素直に組み合わせ全探索できるのでこれで良さそう
 
➁　思考

中心間距離を d とすると、交わる条件は d^2 >= (r1+r2)^2 としていたが、サンプル2で (r1-r2)^2 <= d である必要を発見　→ WA → しょうもない変数間違いを修正してAC



 # 1112 復習
 
 # 277E Crystal Switches  diff 1183
 
 解答できず
 
 備考
 
 ➀　解法
 
 スイッチ on の状態と off の状態の2状態が遷移するので、頂点の状態を2つ考える。これによって U,V,0 であれば (U,0) (V,0) が連結し、U,V,1 であれば (U,1) (V,1) が連結する。また、スイッチのある頂点Sでは (S,0) (S,1) が連結していると考えることで、bfsでこの問題を解答できる。
 
 01bfs や　タイクストラなどのアルゴリズムは不要。頂点が変化する場合に限りdistを更新するdfsで十分。この問題の肝はそんなことではなく、2状態を作ることである
 
 
# jsc2021D  Nowhere P  diff 743  
 
解答遷移 AC
 
初見案 〇

計 11:13

備考

➀　初見案

前から順に探索して、dpしようかと考えたが作りたいテーブルはメモリが許さない  → 1 ～ P-1 のP-1個から1つを決めると 次はこのうちどれか1つとの和 が P の倍数になるので P-2 個のうち一つから選ぶことになる。これをN-1回繰り返して解答できると考えた

# 1113

# 区間スケジューリング勉強

# 典型アルゴリズム問題集 B 区間スケジューリング問題

https://atcoder.jp/contests/typical-algorithm/tasks/typical_algorithm_b

備考

➀ 解法

終了時刻でソート。次に早く終わる予定の開始時刻が、現在の予定の終了時刻より大きければその予定を行えると判定。


# アルゴ式　貪欲法 Q 1-7  区間スケジューリング問題

備考

典型問題と同じ
 


# ☆ 230 Destroyer Takahashi  diff 963

解答遷移 WA WA WA AC

初見案 04:46 ×

計 74:32 + 15:00

備考

➀思考

探索済み かつ まだ壊していない壁のうち最も右端の小さいものを保存しておき、次の壁を破壊可能な、左端位置と比較。左端<=右端ならばその壁を破壊することでまだ破壊していない壁すべてを破壊できる。一方、左端>右端ならばその壁とまだ壊していない壁の同時破壊は行えない。また、未探索の壁の左端がこの条件を見たすことはないので破壊していない壁を一度破壊することになる。これを繰り返して完了


③　解法

各壁の右端を D-1 伸ばせば、区間スケジューリングの要領でこの問題を解答できる。 R でソートし、最初の壁の右端以下の左端をもつ壁はすべて同時に破壊できるので、これを超える左端の壁が出るまで進む。そのような壁の後ろに最初の壁と同時に破壊できる壁があっても、これは新しいこの壁とも同時に破壊できる。これを繰り返せば破壊回数が求まる。































