---
# title: '『データサイエンス100本ノック～構造化データ加工編ガイドブック』レビュー'
title: サイト作成Tips
# draft: true
# date: '2024-12-29T01:20:27+09:00'
# weight: 11
draft: false
date: '2021-04-01T00:20:27+09:00'
weight: 1000
slug: 'site-tips'
summary: 'これはsummaryです。'
description: "This is description."
hideSummary: true
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
# images:
# - papermod-cover.png
cover:
  # image: "images/papermod-cover.png" #< /static
  # relative: false
  image: "tree.png" # image path/url
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
<!\--more--> までがリスト表示で出力されます。
summary: の設定より優先度が高いです。
<!--more-->

## 絵文字

🧑‍💻 👨‍💻 👤 👾 🤖  
📈 📊 🔍 ⌨️ 🖥️ 💻 ⚙️ 🧠 🌐 🚀 🪐  
📁 📂 - フォルダ、リポジトリ  
📝 ✍️ - メモ  
📖 📒 🗒️ - ノート  
📘 📙 📕 📚 - 本  
⚠️ - 警告サイン, 最も一般的な注意や警告を示す絵文字  
❗ - 強い注意や緊急性を示す  
🔑 - 鍵、重要なポイントや核心を象徴します  
✔️ ☑️ ✅ - チェックマーク  
ℹ️ - 情報  
➡️ ⬅️ ⬆️ ⬇️ 👉  
:see_no_evil: :hear_no_evil: :speak_no_evil:

## shortcodes {#shortcodes}

### {{</* shortcode */>}} と {{%/* shortcode */%}} の違い

{{< href-target-blank url="https://gohugo.io/methods/page/rendershortcodes/" text="https://gohugo.io/methods/page/rendershortcodes/" >}}
<br></br>
PAGE.RenderShortcodes は、コンテンツファイル内のショートコードをレンダリングするが、
Markdown は保持されることに注意。

### .Page を使用

```go-html-template {linenos=false,anchorLineNos=false}
{{</* page-title */>}}
```
» {{< page-title >}}

### .Site.Params. を使用

```go-html-template {linenos=false,anchorLineNos=false}
{{</* k100/title */>}}
```
➡️ {{< k100/title >}}

```go-html-template {linenos=false,anchorLineNos=false}
{{</* k100/title "s" */>}}
```
→ {{< k100/title "s" >}}

```go-html-template {linenos=false,anchorLineNos=false}
{{</* k100/title "a" */>}}
```
→ {{< k100/title "a" >}}

```go-html-template {linenos=false,anchorLineNos=false}
{{</* k100/git-url */>}}
```
→ {{< k100/git-url >}}

### 部分テンプレートを使用 (partial)

1. text を渡さない場合はデフォルトが適用される
   ```go-html-template {linenos=false,anchorLineNos=false}
   {{</* k100/afilink-book-amazon */>}}
   ```
   → {{< k100/afilink-book-amazon >}}

2. text を渡す場合
   ```go-html-template {linenos=false,anchorLineNos=false}
   {{</* k100/afilink-book-amazon text="こちら📘" */>}}
   ```
   → {{< k100/afilink-book-amazon text="こちら📘" >}}

### param {#param}

1. huto.yaml -> param.k100site.title

   ```go-html-template {linenos=false,anchorLineNos=false}
   {{</* param k100.site.title */>}}  
   ```
   → {{< param k100.site.title >}}  

2. content内のparams

   ```go-html-template {linenos=false,anchorLineNos=false}
   {{</* param testparam */>}}
   ```
   → {{< param testparam >}}  

   ```go-html-template {linenos=false,anchorLineNos=false}
   {{</* param testparam2.nestparam */>}}
   ```
   → {{< param testparam2.nestparam >}}

### href-target-blank

```go-html-template {linenos=false,anchorLineNos=false}
{{</* href-target-blank url="https://..." text="リポジトリ📂" */>}}
```
→   
{{< href-target-blank url="https://github.com/14katsumix/100knocks-dp" text="リポジトリ📂" >}}

### ref {#ref}

- ref: コンテンツディレクトリ (通常content/) のルートからの相対パスを指定
- relref: 現在のページからの相対パスを指定
<br></br>

- overview#bbb へのリンク

  ```md {linenos=false,anchorLineNos=false}
  [overview-BBB はこちら]({{</* ref "overview#bbb" */>}} "overview-BBB")
  ```
  → [overview-BBB はこちら]({{< ref "overview#bbb" >}} "overview-BBB")

- overview.md#d2 へのリンク

  ```md {linenos=false,anchorLineNos=false}
   [overview-d2 はこちら]({{</* ref "overview.md#d2" */>}} "About us")
  ```
  → [overview-d2 はこちら]({{< ref "overview.md#d2" >}} "About us")

  Rendered:
  ```html {lineNos=false}
  <a href="http://example.org/overview/#bbb" title="About us">こちら</a>
  ```
  xxxxxxxxxxxxxxxxxx

### relref

- overview#d2 へのリンク

  ```md {linenos=false,anchorLineNos=false}
  [overview-d2 はこちら]({{</* relref "overview#d2" */>}} "About us")
  ```
  → [overview-d2 はこちら]({{< relref "overview#d2" >}} "About us")  
  Rendered:
  ``` html {lineNos=false}
  <a href="overview/#bbb" title="About us">こちら</a>
  ```

- lang="ja"

  ```md {linenos=false,anchorLineNos=false}
  [lang="ja" はこちら]({{</* relref path="overview" lang="ja" */>}})
  ```

  → [lang="ja" はこちら]({{< relref path="overview" lang="ja" >}})  

### comment {#comment}

```go-html-template {linenos=false,anchorLineNos=false}
{{%/* comment */%}} 
TODO: rewrite the paragraph below. 
{{%/* /comment */%}}
```

{{% comment %}} 
TODO: rewrite the paragraph below. 
{{% /comment %}}

### details

```html {linenos=false,anchorLineNos=false}
{{</* details 
summary="See the details (detailsショートコード)" 
open=false name="name" title="title" */>}} 
This is a **bold** word. 
{{</* /details */>}}
```
⬇️
{{< details 
summary="See the details (detailsショートコード)" 
open=false name="name" title="title" >}} 
This is a **bold** word. 
{{< /details >}}

### figure {#figure}

```html {linenos=false,anchorLineNos=false}
{{</* figure 
   src="box.png" 
   alt="代替テキスト" 
   align="center" 
   width="50%" 
   link="../overview#bbb" 
   rel="noopener" 
   target="_blank" 
   caption="キャプション" 
   title="Box plot" 
*/>}}
```
👉  
{{< 
figure src="box.png" alt="代替テキスト" align="center"  width="50%" link="../overview#bbb" rel="noopener" target="_blank" caption="キャプション" title="Box plot" 
>}}

### Data sources

read: assets/test/pets.csv

```html {linenos=false,anchorLineNos=false}
{{</* csv-to-table "test/pets.csv" */>}}
```
⬇️  
{{< csv-to-table "test/pets.csv" >}}

## PaperMod {#paperod}

### Code block with PaperMod

#### Rコード {#r}

Rのコードは以下のようになります。

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

Rのコードは以下のようになります。

```r {linenos=inline,lineNoStart=14,hl_lines=[2,"6-8"],anchorLineNos=true}
receipt %>% 
  summarise(amount = sum(amount), .by = "sales_ymd") %>% 
  mutate(
    pre_sales_ymd = lag(sales_ymd, n = 1L, order_by = sales_ymd), 
    pre_amount = lag(amount, n = 1L, default = NA, order_by = sales_ymd)
  ) %>% 
  mutate(diff_amount = amount - pre_amount) %>% 
  arrange(sales_ymd) # コメント
```

次はSQLです。

#### SQL

SQLのコードは以下のようになります。

```sql {linenos=false,lineNoStart=1,hl_lines=["3-4","9-11"]}
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

次は go-html-template コードです。

#### go-html-template コード

go-html-template のコードは以下のようになります。

```go-html-template {linenos=false,anchorLineNos=false}
<div><p>xxxxxxxxxxxxxxxxxxxxxx</p></div>
{{ if eq .Type "alert" }}
  <blockquote class="alert alert-{{ .AlertType }}">
    <p class="alert-heading">
      {{ transform.Emojify (index $emojis .AlertType) }}
      {{ with .AlertTitle }}
        {{ . }}
      {{ else }}
        {{ or (i18n .AlertType) (title .AlertType) }}
      {{ end }}
    </p>
    {{ .Text }}
  </blockquote>
{{ else }}
  <blockquote>
    {{ .Text }}
  </blockquote>
{{ end }}
```

#### go-text-template コード

go-text-template のコードは以下のようになります。

```go-text-template {linenos=false,anchorLineNos=false}
<div><p>xxxxxxxxxxxxxxxxxxxxxx</p></div>
{{ if eq .Type "alert" }}
  <blockquote class="alert alert-{{ .AlertType }}">
    <p class="alert-heading">
      {{ transform.Emojify (index $emojis .AlertType) }}
      {{ with .AlertTitle }}
        {{ . }}
      {{ else }}
        {{ or (i18n .AlertType) (title .AlertType) }}
      {{ end }}
    </p>
    {{ .Text }}
  </blockquote>
{{ else }}
  <blockquote>
    {{ .Text }}
  </blockquote>
{{ end }}
```

#### textコード

```text {linenos=true,lineNoStart=1,hl_lines=["3-4",23], anchorLineNos=true}
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

### Code block with Hugo's internal highlight shortcode {#code}

Rのコードは以下のようになります。

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

htmlのコードは以下のようになります。

{{< highlight html >}}
{{ range .Pages }}
  <h2><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></h2>
{{ end }}
{{< /highlight >}}

go-html-template のコードは以下のようになります。

{{< highlight go-html-template "lineNos=inline, lineNoStart=42" >}}
{{ range .Pages }}
  <h2><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></h2>
{{ end }}
{{< /highlight >}}

## Markdown

### Markdown attributes

#### paragraph (段落)

```md {lineNos=false}
This is a paragraph.
{class="foo bar" id="baz"}
```
→  
This is a paragraph.
{class="foo bar" id="baz"}

``` {lineNos=false}
This is a paragraph.
{.foo .bar #baz}
```
→  
This is a paragraph.
{.foo .bar #baz}

Rendered: 
```html {lineNos=false}
<p class="foo bar" id="baz">This is a paragraph.</p>
```

#### blockquote {#blockquote}

``` {lineNos=false}
> This is a blockquote.
{class="foo bar"}
```
→ 

> This is a blockquote.
{class="foo bar"}
<!-- {class="foo bar" hidden=hidden} -->

Rendered: 
```html {lineNos=false}
<blockquote class="foo bar">
  <p>This is a blockquote.</p>
</blockquote>
```

### 引用 (\>, \>>)

#### 出典を明記しない引用

> *ブロック引用符内*でマークダウン構文を使用できることに**注意してください**。

``` {lineNos=false}
> - aaaaaaaaaaaaaaaaaaaaa
> - bbbbbbbbbbbbbbbbbbbbb
>> xxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
→ 
> - aaaaaaaaaaaaaaaaaaaaa
> - bbbbbbbbbbbbbbbbbbbbb
>> xxxxxxxxxxxxxxxxxxxxxxxxxxxx

#### 出典を明記した引用

```htm {lineNos=false}
> Don't communicate by sharing memory, share memory by communicating.
>
> — <cite>Rob Pike[^3]</cite>
```
→ 
> Don't communicate by sharing memory, share memory by communicating.
> 
> — <cite>Rob Pike[^3]</cite>

[^3]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.

#### footerを明記した引用

```html {lineNos=false}
> Don't communicate by sharing memory, share memory by communicating.
> <footer>Rob Pike</footer>
```
→ 
> Don't communicate by sharing memory, share memory by communicating.
> <footer>Rob Pike</footer>

### アラート (Alerts) {#alerts}

定義ファイル:
- layouts/_default/_markup/render-blockquote.html
- i18n/ja.yaml

```text {lineNos=false}
> [!TIP]
> Helpful advice for doing things better or more easily.
```

1. 
> [!NOTE]
> この blockquote レンダリング フックは、アラート指定子が存在する場合は多言語アラートをレンダリングし、
> それ以外の場合は CommonMarkdown の仕様に従って blockquote をレンダリングします。

2. 
> [!TIP]
> Helpful advice for doing things better or more easily.

3. 
> [!IMPORTANT]
> Key information users need to know to achieve their goal.

4. 
> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

5. 
> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.

### 注釈

テキスト[^1]  
テキスト[^2]

[^1]: 注釈1の内容

[^2]: 注釈2の内容

### Inline Code

これは `This is Inline Code` です。

### convert CSV to Markdown table

| aaaaaa   | bbbbbb   | cccccc   |
| ---: | :---: | :--- |
| 1   | 2   | 3   |

### convert Markdown table to CSV

aaaaaa,bbbbbb,cccccc  
1,2,3

### エスケープ (\\)

例2： \### aaa  
例1： \`インライン表示されなくなる`  

### 段落

テキストの行間に空白行を残すことで、新しい段落を作成できる.

### 改行

末尾にバックスラッシュ(\\)かスペース2つを含める: \
aaaaaaaaaaaaaaaaaa\
bbbbbbbbbbbbbbbbbbbbbb

### フォント

<pre>これはPlainテキスト。</pre>

```html {linenos=false,anchorLineNos=false}
<font color="Red">カラーテキスト</font>
```
→ <font color="Red">カラーテキスト</font>

\~ or ~~: \
~~打ち消し線~~  
ABC ~打ち消し線~ XYZ  

\*, **, ***: \
*斜体*  
**太字**  
***太字と斜体***

\<ins>: \
これは<ins>下線付きの文章</ins>です。

\<sub> :\
これは下付き<sub>テキスト</sub>です。

\<sup>: \
これは上付き<sup>テキスト</sup>です。

\<mark>: \
Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.

\<kbd>: \
Press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> to end the session.

### リスト

1. 1111111111
   - aaaaaaaaaa
   - bbbbbbbbbbb
   - ccccccccccccc
     - ddddddddddddd
     - eeeeeeeeeeeeee
2. 2222222222
     * fffffffffff
     + gggggggggggg
       - hhhhhhhhhhhh
       - iiiiiiiiiiiii

### タスクリスト

- [x] aaaaaaaaaaaaaaaaa
- [ ] bbbbbbbbbbbbbbbbbb
- [x] cccccccccccccccccccc 


### 記号

...  
<< >>  
'  ‘  ’  "  ”  

--  

For example, the base template below calls the [partial](https://gohugo.io/functions/partials/include/) function to include partial templates for the `head`, `header`, and `footer` elements of each page, and it uses the [block](https://gohugo.io/functions/go-template/block/) function to include `home`, `single`, `section`, `taxonomy`, and `term` templates within the `main` element of each page.

A home template renders your site’s home page. For a single page site this is the only required template. For example, the home template below inherits the site’s shell from the base template, and renders the home page content with a list of pages.

ショートコードの定義方法に応じて、引数は名前付き、位置指定、またはその両方になりますが、1 回の呼び出しで引数タイプを混在させることはできません。

## H2 見出し2

Hugo は、特定のページのテンプレートを選択する際に、以下にリストされているパラメータを考慮します。テンプレートは、詳細度によって順序付けられています。これは自然なことのはずですが、さまざまなパラメータのバリエーションの具体的な例については、以下の表をご覧ください。

### H3 見出し3

Hugo は、特定のページのテンプレートを選択する際に、以下にリストされているパラメータを考慮します。テンプレートは、詳細度によって順序付けられています。

```go-html-template {linenos=false,anchorLineNos=false}
{{%/* comment */%}} 
TODO: rewrite the paragraph below. 
{{%/* /comment */%}}
```

これは自然なことのはずですが、さまざまなパラメータのバリエーションの具体的な例については、以下の表をご覧ください。

ショートコードの定義方法に応じて、引数は名前付き、位置指定、またはその両方になりますが、1 回の呼び出しで引数タイプを混在させることはできません。名前付き引数の形式は、 という形式の HTML の形式をモデルにしていますname="value"。

#### H4 見出し4

Hugo は、特定のページのテンプレートを選択する際に、以下にリストされているパラメータを考慮します。テンプレートは、詳細度によって順序付けられています。

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

これは自然なことのはずですが、さまざまなパラメータのバリエーションの具体的な例については、以下の表をご覧ください。

##### H5 見出し5

Hugo は、特定のページのテンプレートを選択する際に、以下にリストされているパラメータを考慮します。テンプレートは、詳細度によって順序付けられています。

これは自然なことのはずですが、さまざまなパラメータのバリエーションの具体的な例については、以下の表をご覧ください。

###### H6 見出し6

Hugo は、特定のページのテンプレートを選択する際に、以下にリストされているパラメータを考慮します。

テンプレートは、詳細度によって順序付けられています。これは自然なことのはずですが、さまざまなパラメータのバリエーションの具体的な例については、以下の表をご覧ください。

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

```text {lineNos=false}
A \\$5 bill _saved_ is a \\$5 bill _earned_.
```

→  A \\$5 bill _saved_ is a \\$5 bill _earned_.

- Chemistry

$$C_p[\ce{H2O(l)}] = \pu{75.3 J // mol K}$$

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

## shortcodes (SNS)

### twitter

```html {linenos=false,anchorLineNos=false}
{{</* twitter user="0149ph_leonardo" id="807218695550472196" */>}}
```
→ 
{{< twitter user="0149ph_leonardo" id="807218695550472196" >}}

---

### instagram

<!-- https://www.instagram.com/p/CxOWiQNP2MO/ -->
<!-- {{< instagram CxOWiQNP2MO >}} -->

<!-- https://www.instagram.com/p/C9Tq0qdPSTF -->

```html {linenos=false,anchorLineNos=false}
{{</* instagram C9Tq0qdPSTF */>}}
```
→ 
{{< instagram C9Tq0qdPSTF >}}

---

### youtube

```html {linenos=false,anchorLineNos=false}
{{</* youtube id="0RKpf3rK57I" autoplay=false */>}}
```
→ 
{{< youtube id="0RKpf3rK57I" autoplay=false >}}
<!-- https://www.youtube.com/watch?v=0RKpf3rK57I -->

---

### vimeo

```html {linenos=false,anchorLineNos=false}
{{</* vimeo 55073825 */>}}
```
→ 
{{< vimeo 55073825 >}}
<!-- https://vimeo.com/channels/staffpicks/55073825 -->

