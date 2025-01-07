---
draft: true
section: page
description: 'description: 用語集です。'
build:
  render: always # glossary ページが常にレンダリングされることを保証する
cascade:
# 内部の設定が glossary コンテンツに適用される (ネストされたコンテンツに設定を適用)
  - build:
      list: local # glossaryページはローカルのリストの一部とする
      publishResources: false # glossaryページに関連するリソース（画像やファイルなど）を公開しない
      render: never
      #> glossary ページを通常のページレンダリングの一部として表示しない.
      #> list.html テンプレートを使ってカスタム表示する.
# リストページ用のテンプレートを layouts/testglossary/list.html にする: 
# (*) 通常は layouts/glossary/list.html を適用する (glossaryセクションのため)
type: "testglossary"
title: Glossary
---

content/glossary/_index.md  
xxxxxxxxxxxxxxx.  
yyyyyyyyyyyyyyyyy.
