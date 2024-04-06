---
created: <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-'W'WW") %>
updated: <% tp.date.now("YYYY-MM-DD") %>
type: Weekly
status: ⌛️ 等待
年度: <% tp.date.now("YYYY", 0, tp.file.title, "YYYY-'W'WW") %>
月份: <% tp.date.now("MM", 0, tp.file.title, "YYYY-'W'WW") %>
评分:
---
## 周度总结

## Fleeting Notes
```dataview
table without id 
	file.link as 日期,
	dateformat(created, "ccc") as 星期, 
	L.text as 闪念笔记, 
	L.link as 链接
from "0-周期笔记"
where type = "Daily"
where created.weekyear = this.created.weekyear
flatten file.lists as L
where
	!L.parent and
	meta(L.section).subpath = "Fleeting Notes"
```
## 本周新建的笔记
```dataview
table type,status
from !"9-Template" AND !"Obsidian管理"
where created.weekyear = this.created.weekyear
sort created asc
```