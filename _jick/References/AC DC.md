---
category:
  - "[[People]]"
  - "[[Bands]]"
tags:
  - people
  - musicians
  - bands
members:
  - "[[Malcolm Young]]"
  - "[[Angus Young]]"
  - "[[Bon Scott]]"
  - "[[Cliff Williams]]"
  - "[[Phil Rudd]]"
genre:
  - "[[Rock]]"
year: 1973
rating: 7
created: 2024-11-11
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