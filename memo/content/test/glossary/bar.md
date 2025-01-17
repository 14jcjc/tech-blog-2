---
title: bar
---

### Bar

**bar の用語**に関するコンテンツ。

Hugo は、特定のページのテンプレートを選択する際に、以下にリストされているパラメータを考慮します。テンプレートは、詳細度によって順序付けられています。

{{% comment %}} 
TODO: rewrite the paragraph below. 
{{% /comment %}}
これは自然なことのはずですが、さまざまなパラメータのバリエーションの具体的な例については、以下の表をご覧ください。

ショートコードの定義方法に応じて、引数は名前付き、位置指定、またはその両方になりますが、1 回の呼び出しで引数タイプを混在させることはできません。

#### ショートコード: href-target-blank

```go-html-template {linenos=false,anchorLineNos=false}
{{</* href-target-blank url="https://..." text="リポジトリ📂" */>}}
```
→ 
{{< href-target-blank url="https://github.com/14katsumix/100knocks-dp" text="リポジトリ📂" >}}

- a
- b
- c
