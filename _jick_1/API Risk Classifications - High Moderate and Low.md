---
category:
  - "[[Lessons]]"
author: 
cover: 
genre: 
length: 
year: 2025-03-24
rating: 
topics: 
last: 2025-03-24
via: ""
tags:
  - references
  - lessons
created: 2025-03-24
---

## Risk Classifications

APIs and front-end clients will be divided into three different risk classifications of H, M, L. The risk classification of an API will be determined similarly to the security risk classification of legacy applications. Any APIs directly exposed by a backend system will inherit that backend's security classification. Once in place, APIs will follow the same access rules as the legacy applications: H APIs can access all other APIs.

## API Security Risk Classification and Setting
Tow different types of APIs exposed on an API GW:
- those that intract directly with a backend system
- those that are composed of other APIs


