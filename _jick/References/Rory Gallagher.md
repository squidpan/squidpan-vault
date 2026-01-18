---
category: "[[People]]"
tags:
  - people
  - musicians
created: 2025-02-01
---
## Albums

```dataview
table without id
	file.link as Album,
	artist as Artist,
	genre as Genre,
	rating as Rating
where
	contains(category,[[Albums]]) and
	contains(artist,this.file.link)
sort rating desc
```