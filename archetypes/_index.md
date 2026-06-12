---
date: '{{ .Date }}'
draft: false
title: '{{ replace (path.Base .File.Dir) "-" " " | title }}'
{{- if eq .File.Section "docs" }}
type: docs
weight: 10
{{- else if eq .File.Section "blog" }}
type: blog
{{- end }}
---

{{ if eq .File.Section "docs" -}}
> 这里是该文档目录 {{ path.Base .File.Dir }} 的简要说明。

{{<directory_tree>}}

{{ else if eq .File.Section "blog" -}}
> 这里是博客分类 {{ path.Base .File.Dir }} 下的文章汇总。
{{<directory_tree>}}

{{ end -}}