---
category:
  - "[[Apps]]"
tags:
  - apps
  - references
maker: 2025-04-04
rating: 
created: 2025-04-04
year: 2025-04-04
last: 2025-04-04
---
## Installation
[swagger editor](https://swagger.io/docs/open-source-tools/swagger-editor/)

```
pl@pl:~$ docker pull docker.swagger.io/swaggerapi/swagger-editor
docker run -d -p 80:8080 docker.swagger.io/swaggerapi/swagger-editor
Using default tag: latest
latest: Pulling from swaggerapi/swagger-editor
59b809be84a5: Download complete 
6d79cc6084d4: Download complete 
0c7e4c092ab7: Download complete 
43f2ec460bdf: Download complete 
984583bcf083: Download complete 
e7b8acce241a: Download complete 
a616ab0ad40c: Download complete 
8d27c072a58f: Download complete 
405997e85a16: Download complete 
8901f6e8cf63: Download complete 
ab3286a73463: Download complete 
84dd2248193b: Download complete 
a7135ef473bd: Download complete 
f18232174bc9: Download complete 
ccc35e35d420: Download complete 
Digest: sha256:f0e638ac1a49fa79a5fa8bef2ad766817d30334e86bd4e5be98191da3d844f87
Status: Downloaded newer image for docker.swagger.io/swaggerapi/swagger-editor:latest
docker.swagger.io/swaggerapi/swagger-editor:latest
02ee953c6acaed3cf1f840cb5f1fefecd07bbcdaa5965531fa9243de1e099e8f
pl@pl:~$ 
```

This will run Swagger Editor (in detached mode) on port 80 on your machine, so you can open it by navigating to `http://localhost` in your browser.