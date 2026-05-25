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
