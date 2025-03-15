---
created: 2023-12-25
tags:
  - ref
source: https://blacksmithgu.github.io/obsidian-dataview/
links:
  - "[[!Obsidian]]"
---

- [Output](https://blacksmithgu.github.io/obsidian-dataview/queries/query-types/)
	- `LIST "File Path: " + file.folder + " _(created: " + file.cday + ")_"`
	- `TABLE author, file.ctime as "created"`
	- TASK 
	- CALENDAR
- FROM ([Source](https://blacksmithgu.github.io/obsidian-dataview/reference/sources/))
	- all `FROM ""`
	- folders `FROM "HAMZA.MD"`
	- tags `FROM #Games`
	- Combination `FROM  "HAMZA.MD" OR #GAMES`
- WHERE (Filter) `WHERE due AND due < date(today)`
- Sort 
- GROUP BY `GROUP BY file.link`
- LIMIT `LIMIT 10`
- FLATTEN (one result into multiple)

## Data From one file
- [T1::4]
	[T2::5]
	[T3::6]
- [T1::7]
	[T2::8]
	[T3::9]
```dataview
TABLE WITHOUT ID L.T1, L.T2, L.T3
WHERE file = this.file
FLATTEN file.lists AS L
SORT L.stars DESC
```
