---
# title: '『データサイエンス100本ノック～構造化データ加工編ガイドブック』レビュー'
title: まとめ
date: '2024-12-29T01:20:27+09:00'
draft: true
weight: 1
slug: 'matome'
summary: 'これはsummaryです。'
description: "This is description."
UseHugoToc: true
TocOpen: true
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
cover:
  # image: "images/papermod-cover.png" #< /static
  # relative: false
  image: "tree.png" # image path/url
  alt: "cover" # alt text
  # caption: "<text>" # display caption under cover
  relative: true # when using page bundles set this to true
  # hidden: true
  hiddenInList: false # hide on list pages and home
  hiddenInSingle: true # hide on single page
# editPost:
#     URL: "https://github.com/<path_to_repo>/content"
#     Text: "Suggest Changes" # edit text
#     appendFilePath: true # to append file path to Edit link
---

このブロックは summary です。  
<!\--more--> までがリスト表示で出力されます。
summary: の設定より優先度が高いです。
<!--more-->

## shortcodes

- {{</* test-shortcode-1 */>}}: {{< test-shortcode-1 >}}

### .Page を使用

- {{</* page-title */>}}: {{< page-title >}}

### .Site.Params. を使用

- {{</* k100-site */>}}: {{< k100-site >}}
- {{</* k100-title-s */>}}: {{< k100-title-s >}}

### param

- {{</* param k100_site */>}}  
  huto.yaml -> param.k100_site : {{< param k100_site >}}  
  <br>
- {{</* param testparam */>}}: {{< param testparam >}}  
- {{</* param testparam2.nestparam */>}}: {{< param testparam2.nestparam >}}

### ref

- overview-BBB は [こちら]({{< ref "overview#bbb" >}} "overview-BBB")  
- overview-d2 は [こちら]({{< ref "overview.md#d2" >}} "About us")  
  Rendered:
  ``` html
  <a href="http://example.org/overview/#bbb">こちら</a>
  ```
  xxxxxxxxxxxxxxxxxx

### relref

- overview-d2 は [こちら]({{< relref "overview#d2" >}} "About us")  
  Rendered:
  ``` html
  <a href="overview/#bbb">こちら</a>
  ```

- lang="ja" は  [こちら]({{< relref path="overview" lang="ja" >}})  

### comment  

{{% comment %}} 
TODO: rewrite the paragraph below. 
{{% /comment %}}

### details

{{< details 
summary="See the details (detailsショートコード)" 
open=false name="name" title="title" >}} 
This is a **bold** word. 
{{< /details >}}

### figure

{{< 
figure 
src="box.png" title="Box plot" alt="代替テキスト" width="50%" link="../setup" 
rel="noopener" target="_blank" caption="キャプション" 
>}}

### Data sources

{{</* csv-to-table "test/pets.csv" */>}}: 

{{< csv-to-table "test/pets.csv" >}}

read: assets/test/pets.csv

---

## PaperMod

### Code block with PaperMod

Rコード: 
```r {linenos=true,lineNoStart=1,hl_lines=[2,"7-8"]}
receipt %>% 
  summarise(amount = sum(amount), .by = "sales_ymd") %>% 
  mutate(
    pre_sales_ymd = lag(sales_ymd, n = 1L, order_by = sales_ymd), 
    pre_amount = lag(amount, n = 1L, default = NA, order_by = sales_ymd)
  ) %>% 
  mutate(diff_amount = amount - pre_amount) %>% 
  arrange(sales_ymd) # コメント
```

```r {linenos=inline,lineNoStart=14,hl_lines=[2,"6-8"]}
receipt %>% 
  summarise(amount = sum(amount), .by = "sales_ymd") %>% 
  mutate(
    pre_sales_ymd = lag(sales_ymd, n = 1L, order_by = sales_ymd), 
    pre_amount = lag(amount, n = 1L, default = NA, order_by = sales_ymd)
  ) %>% 
  mutate(diff_amount = amount - pre_amount) %>% 
  arrange(sales_ymd) # コメント
```

SQL: 
```sql {linenos=true,lineNoStart=1,hl_lines=["3-4","9-11"]}
with customer_amount as (
  select
    customer_id, 
    SUM(amount) as total_amount
  from receipt
  where customer_id NOT LIKE 'Z%'
  group by customer_id
)
select 
  *
from
  customer_amount
where 
  total_amount >= (select AVG(total_amount) from customer_amount)
order by
  total_amount DESC
```

textコード: 
```text {linenos=true,lineNoStart=1,hl_lines=["3-4",23]}
100k
├── matome
│   ├── _index.md
│   └── tree.png
├── _index.md
├── advanced
│   ├── _index.md
│   └── ...
├── overview
│   └── index.md
├── setup
│   ├── index.md
│   └── line.png
├── standard
│   ├── _index.md
│   ├── r-003.md
│   └── r-028.md
└── tips
    └── index.md
```

### Code block with Hugo's internal highlight shortcode

{{< highlight r >}}
receipt %>% 
  summarise(amount = sum(amount), .by = "sales_ymd") %>% 
  mutate(
    pre_sales_ymd = lag(sales_ymd, n = 1L, order_by = sales_ymd), 
    pre_amount = lag(amount, n = 1L, default = NA, order_by = sales_ymd)
  ) %>% 
  mutate(diff_amount = amount - pre_amount) %>% 
  arrange(sales_ymd) # コメント
{{< /highlight >}}

{{< highlight go-html-template >}}
{{ range .Pages }}
  <h2><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></h2>
{{ end }}
{{< /highlight >}}

{{< highlight go-html-template "lineNos=inline, lineNoStart=42" >}}
{{ range .Pages }}
  <h2><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></h2>
{{ end }}
{{< /highlight >}}

---

## Markdown

### Markdown attributes

This is a paragraph.
{class="foo bar" id="baz"}

This is a paragraph.
{.foo .bar #baz}

Rendered: 
```html
<p class="foo bar" id="baz">This is a paragraph.</p>
```

\> This is a blockquote.
{class="foo bar"}
<!-- {class="foo bar" hidden=hidden} -->

Rendered: 
```html
<blockquote class="foo bar" hidden="hidden">
  <p>This is a blockquote.</p>
</blockquote>
```

### 注釈

テキスト[^1]

### Inline Code

これは `This is Inline Code` です。

### convert CSV to Markdown table

| aaaaaa   | bbbbbb   | cccccc   |
| ---: | :---: | :--- |
| 1   | 2   | 3   |

### convert Markdown table to CSV

aaaaaa,bbbbbb,cccccc
1,2,3

### エスケープ

例2： \### aaa  
例1： \`インライン表示されなくなる`  

### 引用

1. 
> aaaaaaaaaaaaaaaaaaa

2. 
> xxxxxxxxxxxxxx
>> yyyyyyyyyyyyyyyyyy


---

<font color="Red">カラーテキスト</font>

~~打ち消し線~~  
ABC ~打ち消し線~ XYZ  
**太字**  
*斜体*  

...  
<< >>

'  ‘  ’  "  ”  

--  

[^1]: 注釈1の内容

### Mathematics in Markdown

- This is an inline \(a^*=x-b^*\) equation.

- These are block equations:

\[a^*=x-b^*\]

\[ a^*=x-b^* \]

\[
a^*=x-b^*
\]

- These are also block equations:

$$a^*=x-b^*$$

$$ a^*=x-b^* $$

$$
a^*=x-b^*
$$

- aligned

\[
\begin{aligned}
KL(\hat{y} || y) &= \sum_{c=1}^{M}\hat{y}_c \log{\frac{\hat{y}_c}{y_c}} \\
JS(\hat{y} || y) &= \frac{1}{2}(KL(y||\frac{y+\hat{y}}{2}) + KL(\hat{y}||\frac{y+\hat{y}}{2}))
\end{aligned}
\]

-  math contexts の外では$をダブルエスケープする: 

```text
A \\$5 bill _saved_ is a \\$5 bill _earned_.
```

=> A \\$5 bill _saved_ is a \\$5 bill _earned_.

- Chemistry

$$C_p[\ce{H2O(l)}] = \pu{75.3 J // mol K}$$

---

## Diagrams

### GoAT diagrams (ASCII) 

```goat
      .               .                .               .--- 1          .-- 1     / 1
     / \              |                |           .---+            .-+         +
    /   \         .---+---.         .--+--.        |   '--- 2      |   '-- 2   / \ 2
   +     +        |       |        |       |    ---+            ---+          +
  / \   / \     .-+-.   .-+-.     .+.     .+.      |   .--- 3      |   .-- 3   \ / 3
 /   \ /   \    |   |   |   |    |   |   |   |     '---+            '-+         +
 1   2 3   4    1   2   3   4    1   2   3   4         '--- 4          '-- 4     \ 4

```

---

## shortcodes (SNS)

### twitter

{{< twitter user="0149ph_leonardo" id="807218695550472196" >}}

### instagram

<!-- https://www.instagram.com/p/CxOWiQNP2MO/ -->
<!-- {{< instagram CxOWiQNP2MO >}} -->

<!-- https://www.instagram.com/p/C9Tq0qdPSTF -->
{{< instagram C9Tq0qdPSTF >}}

### youtube

<!-- https://www.youtube.com/watch?v=0RKpf3rK57I -->
{{< youtube id="0RKpf3rK57I" autoplay=false >}}

### vimeo

<!-- https://vimeo.com/channels/staffpicks/55073825 -->
{{< vimeo 55073825 >}}
