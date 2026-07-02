# RDBMS
表型のデータベースをマネジメントするシステム。表（テーブル）から列（カラム）項目を決定し、行（レコード）の値（フィールド）を加える。  
表同士の関係性を追加することが出来る

# 基本操作
```SQL
/*comment out*/
-- also comment out
-- 作成
CREATE TABLE table_name(
  column_name datatype,
  column_name2 datatype
)

-- データ挿入
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);

-- データの取得
SELECT column_name1, column_name2 FROM table_name
[WHERE search_condition (before grouping)]
[GROUP BY column_name]
[HAVING search_condition (after grouping)]
[ORDERED BY sort];

-- 更新
UPDATE table_name SET column_name = value [WHERE句];
UPDATE table_name SET column_name = value [WHERE句];
UPDATE table_name SET column1 = v1, column2 = v2;

-- 削除
DELETE from column_name [WHERE句];

-- WHERE句
SELECT column_name FROM table_name
WHERE value = v;
--- 条件節
value = v;
value < v;
NOT condition;
condition1 AND condition2;
condition1 OR condition2;
BETWEEN lower_bound AND upper_bound; /* lower_bound以上upper_bound以下の条件節 */
value IN (v1, v2, v3);
value IS NOT NULL /* 値が存在している=空欄でない */
LIKE 'SearchString';
-- --ワイルドカード
'_' /* 任意の1文字 */
'%' /* 任意の0文字以上の文字列 */

-- ソート
SELECT column_name FROM table_name
ORDER BY sortby_column [ASC(昇順) DEsC(降順)];
ORDER BY sort1 [ASC/DESC], sort2 [ASC/DESC]; /* sort1が同じ時にsort2でソート */
ORDER BY sortby_column LIMIT limit OFFSET skip; /* 上限表示 */

-- GROUPING 集計関数
SELECT COUNT(age) [AS rename] FROM table_name;
SELECT MAX(age) , MIN(age) FROM table_name;
SELECT SUM(age) , AVG(age), ROUND(AVG(age), display_digit) FROM table_name;
SELECT DISTINCT column_name FROM table_name; /* 重複データを除いて抽出 */
GROUP BY grouping_column1, grouping_column2;

-- JOIN 結合
SELECT joined_table_name.column_name, join_table_name.column_name FROM joined_table_name
JOIN join_table_name ON join_table_mainkey = joined_table_mainkey
/* JOIN: FROM句の一部
中間テーブルを用いて複数のテーブルをJOINで連続して結合可能 */
INNER JOIN left_table.mainkey = right_table.mainkey /* 両方で結合条件に一致するもののみ残す (= JOIN) */
LEFT OUTER JOIN left_table.mainkey = right_table.mainkey /* left_tableの行はすべて残す (= LEFT JOIN)*/
RIGHT OUTER JOIN left_table.mainkey = right_table.mainkey /* right_tableの行はすべて残す (= RIGHT JOIN)*/
FULL OUTER JOIN left_table.mainkey = right_table.mainkey /* 結合に一致する条件と、両方のテーブルの行はすべて残す (= FULL JOIN)*/
CROSS JOIN left_table.mainkey = right_table.mainkey /* 結合条件なく、両方のテーブルの行はすべて残す (ONの条件なしJOINまたは、FROM a.bのように記述)*/

-- WHERE X = SUBQUERY
SELECT column_name FROM table_name 
WHERE column_name = (
  /* subquery */
  SELECT句
);
/* 初めにサブクエリを実行し、その後メインクエリを実行する */

-- WHERE EXISTS SUBQUERY
SELECT * FROM table1
WHERE EXISTS (
  SELECT 1 FROM table2
  WHERE table1.id = tabl2.a_id
);

-- WHERE X in SUBQUERY
WHERE id in (SUBQUERY)

-- FROM SUBQUERY
FROM (SUBQUERY) /* サブクエリを一時的なテーブルとして作成 */
-- SELECT JOINでも同じように利用できる
```

## データ型
|データ型|例|
|-----|----|
|integer|0, 2|
|float|0.2|
|text|'aaa', ''|
|varchar(max_length)|'aaa'|
|date|'2020-01-01'('YYYY-MM-DD')|
|datetime|'2020-01-01 12:34:56'('YYYY-MM-DD HH:MM:SS')|

## 設計
```SQL
-- primary key
Create Table table_name(
  primary_key_name datatype PRIMARY KEY, /* primary key constraint */
)
CREATE TABLE table_name(
  primary_key_name datatype PRIMARY KEY AUTOINCREMENT, /* 自動的に生成 DBによって異なる */
)
CREATE TABLE table_name(
  column1 datatype,
  column2 datatype,
  ... ,
  PRIMARY KEY (column1, column2) /* Composite Primary Key */
)

-- Unique Key
CREATE TABLE table_name(
  column datatype UNIQUE /* 値が重複しない、ただしNULLを許容 */
)
CREATE TABLE table_name(
  column1 datatype,
  column2 datatype,
  ...,
  UNIQUE KEY (column1, column2) /* Composite Unique Key */
)

-- Foreign Key
pragma foreign_key = ON; /* 外部キー使用可能にするコマンド */
CREATE TABLE table_name (
  column_name datatype,
  ...
  FOREIGN KEY (column_name) REFERENCES refered_table_name (reference_key_column)
)

CREATE TABLE table_name (
  column_name datatype,
  ...
  FOREIGN KEY (column_name) REFERENCES refered_table_name (reference_key_column)
    ON XXXX(OPERATION) YYYY(reference operation)
)
```
|参照操作名|内容|
|----|----|
|RESTRICT|参照整合性を満たさない操作の禁止|
|NO ACTION|RESTRICTと同様、ただしトランザクション後に検証|
|SET NULL| 参照カラムにNULLを設定|
|CASCADE|参照先が更新/削除されたときに参照先も更新/削除する|

```SQL
-- NOT NULL
CREATE TABLE table_nama(
  column datatype NOT NULL,
  ...
);
-- DEFAULT VALUE
CREATE TABLE table_name(
  column datatype DEFAULT default_value,
  ...
);
```

## index
``` SQL
-- UNIQUE 指定で自動的にINDEX作成
CREATE INDEX index_name ON table_name (column_nmae)
DROP INDEX index_name
-- クエリの計画
EXPLAIN QUERY PLAN (query);
/*
output: detail
  SCAN table_namr: 全件サーチ
  SEARCH table_name USING INDEX index_columns: インデックスサーチ
*/

-- PostgreSQL
EXPLAIN ANALYZE query...
```

## 式と関数
式内で四則演算は可能
```SQL
-- cAST
SELECT CAST(column_name AS TYPE) FROM ...;
/* CAST TYPE: NONE, TEXT, REAL, INTEGER, NUMERIC*/
-- COALESCE: NULLの時に置換
SELECT COALESCE(values, default_value)
-- NULLIF
NULLIF(v1, v2) /* if v1==v2 return NULL, else return v1 */

-- CASE
CASE column
  WHEN case1_value THEN return1
  WHEN case2_value THEN return2
  ...
  ELSE return_else_value /* NO ELSE -> return NULL */
END

CASE
  WHEN condition THEN return1
  ...
END

-- concat string
v1 || v2 -> v1v2

LENGTH(v)
REPLACE(column_name, before, after)
SUBSTR(column, start_index, end_index)
[L/R]TRIM(column)
Upper/Lower(column)
ABS(num)
POWER(num, power_num)
MOD(num, modular)
CIEL/FLOOR(num)
TRUNC(num) /* 整数部分 */
RANDOM()

-- datetime
CURRENT_TIMESTAMP /* -> YYYY-MM-DD HH:MM:SS*/
CURRENT_DATE /* -> YYYY-MM-DD*/
-- 第二引数を取れる
DATETIME(date_string) /* -> YYYY-MM-DD HH:MM:SS (nowを使える)*/
DATE(date_string) /* -> YYYY:MM:DD */
DATE(date, 'start of manth'); /* 月の初日 */
TIME(time_string) /* -> HH:MM:SS (time_stringなしで現在時刻)*/
/*
第二引数
'localtime'
'+3 hour'
'start of month'
*/
STRFTIME('%Y...', string)
DATE_TRUNC('month', column;)
```

## CHECK 制約
``` SQL
CREATE TABLE table_name(
  column_name datatype CHECK (condition)
  column_name datatype DEFAULT default_value CHECK (condition)
  column_name datatype CONSTRAINT check_name CHECK (condition)
) 
```

## Tips
```SQL
-- INSERT + SELECT
INSERT INTO table (columns) /* 最初のカラムから順に評価する */
SELECT columns,...
WHERE
```


# Subquery (Copilot)
# SQLite サブクエリ チートシート

## サブクエリとは

SQL文の中に埋め込む `SELECT` 文です。

```sql
SELECT *
FROM users
WHERE id = (
    SELECT user_id
    FROM profiles
    WHERE email = 'test@example.com'
);
```

実行順序

```text
1. サブクエリ実行
2. 結果取得
3. 外側のクエリ実行
```

---

# 1. WHERE句で使用する

## 単一値を返すサブクエリ

平均価格以上の商品を取得

```sql
SELECT *
FROM product
WHERE price > (
    SELECT AVG(price)
    FROM product
);
```

比較演算子

```sql
=
<>
>
<
>=
<=
```

---

# 2. IN句で使用する

## 複数行を返すサブクエリ

注文履歴のある顧客を取得

```sql
SELECT *
FROM customer
WHERE id IN (
    SELECT customer_id
    FROM orders
);
```

---

## NOT IN

注文履歴のない顧客を取得

```sql
SELECT *
FROM customer
WHERE id NOT IN (
    SELECT customer_id
    FROM orders
);
```

### NULL対策

```sql
SELECT *
FROM customer
WHERE id NOT IN (
    SELECT customer_id
    FROM orders
    WHERE customer_id IS NOT NULL
);
```

---

# 3. EXISTSを使用する

## 関連データが存在する

注文履歴がある顧客

```sql
SELECT *
FROM customer c
WHERE EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customer_id = c.id
);
```

---

## 関連データが存在しない

注文履歴がない顧客

```sql
SELECT *
FROM customer c
WHERE NOT EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customer_id = c.id
);
```

---

# 4. SELECT句で使用する

顧客ごとの注文数を表示

```sql
SELECT
    c.id,
    c.name,
    (
        SELECT COUNT(*)
        FROM orders o
        WHERE o.customer_id = c.id
    ) AS order_count
FROM customer c;
```

結果例

```text
id | name   | order_count
---+--------+------------
1  | Tanaka | 5
2  | Sato   | 2
```

---

# 5. FROM句で使用する

## 仮想テーブルを作成

顧客ごとの購入金*を集計

```sql
SELECT *
FROM (
    SE*ECT
        customer_id,
        S*M(amount) AS total_amount
    FROM*orders
    GROUP BY customer_id
) *
WHERE t.total_amount >= 10000;
``*

イメージ

```text
orders
   ↓
GROUP *Y
   ↓
仮想テーブル
  *↓
検索
```

---

# 6. 相関サブクエ*

## 外側のテーブルを参照する*
顧客ごとの平均購入額以上の注文を*得

```sql
SELECT *
FROM orders o1
*HERE amount >= (
    SELECT AVG(am*unt)
    FROM orders o2
    WHERE *2.customer_id =*o1.customer_id
);
```

特徴

```text*外側の行ごとにサブクエリが実行され*
↓
大量データでは遅*なりやすい
```

---

# *. MAX/M*N取得

## 最新データ取得

最新注文

```sql
SELE*T *
FROM orders
WHERE order_date =*(
    SELECT MAX(order_date)
    F*OM orders
);
```

---

## 最大値取得

最*額商品

```sql
SELECT *
FROM product
*HERE price = (
    SELECT MAX(pric*)
    FROM product
);
```

---

# 8. HAVING句で使用する

顧客ごとの注文回数が平均以上

```sql
SELECT
    customer_id,
    COUNT(*) AS order_count
FROM orders
GROUP BY customer_id
HAVING COUNT(*) >= (
    SELECT AVG(cnt)
    FROM (
        SELECT COUNT(*) AS cnt
        FROM orders
        GROUP BY customer_id
    )
);
```

---

# 9. JOINへの書き換え

## サブクエリ版

```sql
SELECT *
FROM customer
WHERE id IN (
    SELECT customer_id
    FROM orders
);
```

## JOIN版

```sql
SELECT DISTINCT c.*
FROM customer c
INNER JOIN orders o
    ON c.id = o.customer_id;
```

---

# 10. 実務でよく使うパターン

## 平均以上

```sql
SELECT *
FROM product
WHERE price > (
    SELECT AVG(price)
    FROM product
);
```

---

## 存在確認

```sql
SELECT *
FROM customer c
WHERE EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customer_id = c.id
);
```

---

## 存在しない確認

```sql
SELECT *
FROM customer c
WHERE NOT EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customer_id = c.id
);
```

---

## IN検索

```sql
SELECT *
FROM customer
WHERE id IN (
    SELECT customer_id
    FROM orders
);
```

---

## 集計結果を仮想テーブル化

```sql
SELECT *
FROM (
    SELECT
        customer_id,
        SUM(amount) AS total_amount
    FROM orders
    GROUP BY customer_id
) t;
```

---

# サブクエリ選択指針

| やりたいこと | 推奨 |
|-------------|------|
| 存在確認 | EXISTS |
| 存在しない確認 | NOT EXISTS |
| 値との比較 | スカラーサブクエリ |
| 一覧との比較 | IN |
| 集計結果の再利用 | FROM句サブクエリ |
| 可読性重視の複雑なSQL | CTE(WITH句) |
| データ取得中心 | JOIN |

---

# 覚えておくべき構文

```sql
-- 単一値
WHERE price > (
    SELECT AVG(price)
    FROM product
)

-- 複数値
WHERE id IN (
    SELECT customer_id
    FROM orders
)

-- 存在確認
WHERE EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customer_id = c.id
)

-- 存在しない確認
WHERE NOT EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customer_id = c.id
)

-- 仮想テーブル
FROM (
    SELECT *
    FROM orders
) t

-- 相関サブクエリ
WHERE amount >= (
    SELECT AVG(amount)
    FROM orders o2
    WHERE o2.customer_id = o1.customer_id
)
```
