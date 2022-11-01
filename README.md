# 2211


# 178D  Redistribution  diff 875

解答遷移 AC

計 1時間 over

備考

➀　思考

メモ化再帰で解けるし、ちょうどいいからエラストテネスみたいにこの問題でお勉強しよう! → python の関数の return 等の仕組みが意味わからん過ぎて時間が死ぬほど経過　→　諦めて素直にdpっぽい感じのコード書いたら通って意味不明


➁ メモ

・@lru_cache(maxsize=None) のようにしないと、記憶する数が 128を超えると忘れてしまうので注意。

・https://blanktar.jp/blog/2014/03/python3-lru_cache

・https://cocoinit23.com/abc178/



# dfs 再帰勉強編

・ dfs は到達順を把握できる ex) アルゴ式 dfs Q3

・ Q1 箱の中

bfsすれば dist[X] が答え。

dfs する場合、結局距離をリストで管理しなければいけないので bfs でいい。それ以外なら 距離をglobal変数で管理するしかない

・ Q5 子孫の数

dfs は帰りがけで処理できるメリットあり




















