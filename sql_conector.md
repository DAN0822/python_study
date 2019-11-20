# MySql_conector
参照リンク
https://qiita.com/valzer0/items/2f27ba98397fa7ff0d74
- コネクションの作成
```
import mysql.connector as mydb

conn = mydb.connect(
    host='hostname',
    user='username',
    port='3306',
    password='password',
    database='dbname'
)
```
- コマンドを実行するためのカーソルを作成
```
cur = conn.cursor()
```

- クエリの発行
```
cur.execute("Query(%s)",<%sに代入する変数>）
```

- クエリ結果の取得
```
#全件取得
 rows = cur.fetchall()

 for row in rows:
         print("%d %s" % (row[0], row[1]))
# 1件取得
 cur.execute("SELECT * FROM test_table WHERE name=%s", ('BTC', ))
 print(cur.rowcount)
 print(cur.fetchone())
# 出力結果

 1
 (1, 'BTC', 10200)

```

- カーソルとコネクションを閉じる
```
# DB操作が終わったらカーソルとコネクションを閉じる
cur.close()
conn.close()
```
