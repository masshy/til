# MySQL

便利なコマンドとか知っておくべきtips。

## EXPLAIN

クエリの先頭に付けると、そのクエリの実行計画を表示する。

```
mysql> EXPLAIN SELECT * FROM table_name; 

```

負荷になりそうなクエリを投げる前にやっておくと便利。

## hex(str)

引数内の文字列を16進数に変換。

```
mysql> select hex("TEST");
+-------------+
| hex("TEST") |
+-------------+
| 54455354    |
+-------------+
1 row in set (0.02 sec)
```

## unhex(str)

`hex`の逆演算。引数の16進数を文字列に変換。

```
mysql> select unhex("54455354");
+-------------------+
| unhex("54455354") |
+-------------------+
| TEST              |
+-------------------+
1 row in set (0.00 sec)
```

## order by

ソートして表示。
ORDER BYを使ったときは明示的にASC, DESCを指定した方が、確認するときも安心。