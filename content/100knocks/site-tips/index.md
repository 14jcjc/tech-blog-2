---
# title: '『データサイエンス100本ノック～構造化データ加工編ガイドブック』レビュー'
title: サイト作成Tips - include
draft: true
date: '2024-12-29T01:20:27+09:00'
weight: 11
# draft: false
# date: '2021-04-01T00:20:27+09:00'
# weight: 1000
slug: 'site-tips'
summary: 'これはsummaryです (include).'
description: "This is description."
hideSummary: false
hideFooter: false
# ShowToc: false
UseHugoToc: true
TocOpen: true

# related:
#   show: true
#   limit: 7 # 関連コンテンツを最大 N件まで表示 (default: 5)

categories: 
  - "DS-100本ノック"
tags: 
  - R
  - SQL
# tags_weight: 1
params:
  params:
    math: true # Mathematics in Markdown
  testparam: "これは params.testparam."
  testparam2: 
    nestparam: "これは testparam2.nestparam."
# images:
# - papermod-cover.png
cover:
  # image: "images/papermod-cover.png" #< /static
  # relative: false
  image: "box.png" # image path/url
  alt: "cover" # alt text
  caption: "This is caption" # display caption under cover
  relative: true # when using page bundles set this to true
  # hidden: true
  hiddenInList: false # hide on list pages and home
  hiddenInSingle: true # hide on single page
# Edit Link for Posts
# 投稿のファイルパスを使用して編集先にリンクし, 変更を提案するボタンを追加する: 
# editPost:
#     URL: "https://github.com/<path_to_repo>/content"
#     Text: "Suggest Changes" # edit text
#     appendFilePath: true # to append file path to Edit link
---

このブロックは summary です。  
<!\--more--> までがリスト表示で出力されます.
summary: の設定より優先度が高いです. 
<!--more-->

--- 

{{% include "/test/100k/site-tips/index.md" %}}
