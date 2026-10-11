{{- /* The starting template for bulletin board posts: "hugo new posts/my-post.md".
       Hugo picks this file because the new page is inside content/posts/.
       The date is today's date; the title is made from the file name (dashes become spaces). */ -}}
---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date | time.Format "2006-01-02" }}
---

