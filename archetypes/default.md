---
date: '{{ .Date }}'
draft: true
title: '{{ replace .File.ContentBaseName "-" " " | title }}'
# title: "{{ .Site.Params.site_title }}"
---
