{{- /* An archetype is the starting template for "hugo new". This one is used for any new
       page: "hugo new resources/my-page.md" makes the file with this front matter filled in.
       The text below the dashes is what ends up in the new file. */ -}}
---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
---

