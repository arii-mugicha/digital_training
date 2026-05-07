# RDBMS
表型のデータベースをマネジメントするシステム。表（テーブル）から列（カラム）項目を決定し、行（レコード）の値（フィールド）を加える。  
表同士の関係性を追加することが出来る

# 基本操作
```SQL
/*comment out*/
-- also comment out
-- 作成
Create Table{
  column_name datatype,
  column_name2 datatype
}

-- データ挿入
INSERT INTO table_name (column1, column2, ...)
Values (value1, value2, ...);

-- データの取得
SELECT column_name1, column_name2 FROM table_name
[WHERE search_condition (before grouping)]
[GROUP BY column_name]
[HAVING search_condition (after grouping)]
[ORDERED BY sort];

-- 更新
UPDATE table_name SET column_name = value;
UPDATE table_name SET column_name = column_name + 1;

-- 削除
DELETE from column_name;

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
