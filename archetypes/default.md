---
date: '{{ .Date }}'
draft: true
slug: '{{ .File.ContentBaseName }}'
# title: '{{ replace .File.ContentBaseName "-" " " | title }}'
title: "{{ .Site.Params.site_rsql }}{{ .Site.Params.site_100knocks }}（{{ .Site.Params.site_suffix_s }}）{{ title .File.ContentBaseName }}"
categories: 
  - "{{ .Site.Params.site_category_s }}"
---
