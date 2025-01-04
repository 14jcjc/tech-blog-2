---
title: '『データサイエンス100本ノック～構造化データ加工編ガイドブック』レビュー'
date: '2024-12-29T01:20:27+09:00'
draft: true
weight: 1
slug: '100knocks-dp-guidebook'
draft: true
summary: 'これはsummaryです。'
categories: 
- "DS-100本ノック"
tags: 
- R
- SQL
# tags_weight: 1
params:
  testparam: "これは params.testparam."
  testparam2: 
    nestparam: "これは nest param."
cover:
  # image: "images/papermod-cover.png" #< /static
  image: "tree.png"
  # relative: false
  relative: true
  hidden: false
  hiddenInList: true
---

## ショートコード

- shortcode: {{< test-shortcode-1 >}}

- huto.yaml -> param.site_100knocks : {{< param site_100knocks >}}

- shortcode: {{< site-100knocks >}}
- shortcode: {{< title-100k-s >}}

### ref

- overview-BBB は [こちら]({{< ref "overview#bbb" >}} "overview-BBB")  
- overview-d2は [こちら]({{< ref "overview.md#d2" >}} "About us")  
Rendered:
``` html
<a href="http://example.org/overview/#bbb">こちら</a>
```

### relref

- overview-d2は [こちら]({{< relref "overview.md#d2" >}} "About us")  
Rendered:
``` html
<a href="overview/#bbb">こちら</a>
```

### comment  

{{% comment %}} 
TODO: rewrite the paragraph below. 
{{% /comment %}}

### param

- {{< param testparam >}}  
- {{< param testparam2.nestparam >}}

param.site_100knocks : {{< param site_100knocks >}}

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

---

## PaperMod

### Code block with PaperMod

```r {linenos=true,lineNoStart=1,hl_lines=[2,4,7]}
receipt %>% 
  summarise(amount = sum(amount), .by = "sales_ymd") %>% 
  mutate(
    pre_sales_ymd = lag(sales_ymd, n = 1L, order_by = sales_ymd), 
    pre_amount = lag(amount, n = 1L, default = NA, order_by = sales_ymd)
  ) %>% 
  mutate(diff_amount = amount - pre_amount) %>% 
  arrange(sales_ymd) # コメント
```

```r {linenos=inline,lineNoStart=14,hl_lines=[4,8]}
receipt %>% 
  summarise(amount = sum(amount), .by = "sales_ymd") %>% 
  mutate(
    pre_sales_ymd = lag(sales_ymd, n = 1L, order_by = sales_ymd), 
    pre_amount = lag(amount, n = 1L, default = NA, order_by = sales_ymd)
  ) %>% 
  mutate(diff_amount = amount - pre_amount) %>% 
  arrange(sales_ymd) # コメント
```

textコード: 
```text
func someFunction(s string, n int) string
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
