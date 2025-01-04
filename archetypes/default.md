---
date: '{{ .Date }}'
draft: true
# title: '{{ replace .File.ContentBaseName "-" " " | title }}'
# title: "{{ .Site.Params.site_100knocks }}"
title: "{{ .Site.Params.site_rsql }}{{ .Site.Params.site_100knocks }}（{{ .Site.Params.site_suffix_s }}）{{ title .File.ContentBaseName }}"
categories: 
  - "{{.Site.Params.site_100knocks}}（{{ .Site.Params.site_suffix_s }}）"
---
