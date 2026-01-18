---
categories:
  - "[[Troubleshoots]]"
author:
  - "[[Me]]"
url:
published:
topics: []
status:
created: 2025-11-19
last: 2025-11-19
rating:
---
# Issues
## Description
connection issue from pgAdmin4 to Postgresql freshely installed

## Environments

## How to reproduce - steps

```code
  
```

# Resolution steps

After installation of Postgres, set the postgres user password using the command
go to pgAdmin 4 desktop and use postgres password to register server

## Steps


```code
pl@pop-os:~$ sudo -u postgres psql postgres
could not change directory to "/home/pl": Permission denied
psql (14.19 (Ubuntu 14.19-0ubuntu0.22.04.1))
Type "help" for help.

postgres=# \password postgres
Enter new password for user "postgres": pe12rry12
Enter it again: pe12rry12
postgres=# \q
pl@pop-os:~$ 

```



