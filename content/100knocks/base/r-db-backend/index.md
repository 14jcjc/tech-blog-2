---
title: "R によるデータベースクエリ操作について"
slug: "r-db-backend"
date: 2025-01-05T00:03:13+09:00
draft: false
# draft: true
weight: 15
# description: ""
# summary: ""
categories: ["DS-100本ノック+α"]
tags: ["R", "SQL"]
cover:
  # image: "images/papermod-cover.png" #< /static
  # image: "images/100knocks/cover-100k-standard.png" #< /static
  relative: false
  hiddenInList: false
  hiddenInSingle: false # hide on single page
  # hidden: true
# ShowToc: false
# TocOpen: false
# disableHLJS: false
# disableShare: false
# hideSummary: false
# searchHidden: false
# ShowReadingTime: false
# ShowWordCount: false
---

基本的な使い方は以下のような流れになります。

```r
# 必要なパッケージをロード
pacman::p_load(
  DBI, dplyr, dbplyr, 
  RPostgres, # PostgreSQL の場合
  install = T # 存在しないパッケージをインストールする
)

# データベースへの接続 (PostgreSQL の場合)
dbConnect(
  RPostgres::Postgres(), 
  host = "your_host", 
  port = 5432, 
  dbname = "your_database_name", 
  user = "your_username", 
  password = "your_password"
) -> 
con

# データベースのテーブル参照を取得
db_table = tbl(con, "your_table_name")

# テーブル操作をSQLクエリとして保持
db_table %>% 
  filter(sales_ymd >= 20180101L ) %>%  
  group_by(product_cd) %>% 
  summarise(total_sales = sum(amount)) %>% 
  arrange(desc(total_sales)) -> 
  db_result

# SQLクエリの自動生成・確認
db_result %>% show_query(cte = T)

# SQLクエリの結果をR側に取り込む
df_result = db_result %>% collect()  

# データベース接続を解除
dbDisconnect(con)

# 以下、データフレームでの処理
df_result %>% head(10)
```

ハイライトした箇所のように、データベースのテーブルを dplyr の構文を用いてデータフレームライクで操作できます。

対応しているデータベース一覧は << こちら >> で確認できます。

## R によるデータベース・バックエンド処理と遅延評価の仕組み

