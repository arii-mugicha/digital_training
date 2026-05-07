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
