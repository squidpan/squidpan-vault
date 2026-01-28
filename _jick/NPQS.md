---
category:
  - "[[People]]"
tags:
  - people
  - musicians
  - bands
created: 2024-11-25
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