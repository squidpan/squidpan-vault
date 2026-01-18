---
categories:
  - "[[Installs]]"
rating:
created: 2025-11-19
last: 2025-11-19
topics:
apps:
title:
---
# Summary

# Prerequisites

# Steps
## telusko Linux (Ubuntu/Debian):

## Install
```code
sudo apt update
sudo apt install postgresql postgresql-contrib
sudo systemctl start postgresql
sudo systemctl enable postgresql

```
Step 3: Verify Installation
1. Open Command Prompt/Terminal
2. Test connection: psql -U postgres
3. Enter the password you set during installation
Step 4: Using pgAdmin
 4. Launch pgAdmin 4 from Start Menu/Applications
5. Create master password for pgAdmin
6. Connect to the PostgreSQL server:
- Host: localhost
- Port: 5432
- Username: postgres
- Password: (your set password)
Step 5: Create Database and Table
7. In pgAdmin, right-click "Databases" → "Create" → "Database"
8. Name: demo
9. Click "Save"
Create Table using SQL:
-- Connect to demo database
-- Create student table
```code
CREATE TABLE student (
sid INTEGER PRIMARY KEY,
sname TEXT NOT NULL,
marks INTEGER
);
-- Insert sample data
INSERT INTO student VALUES (1, 'Navin', 80);

```
## Postgresql
```code
 1338  sudo apt install postgresql
 1342  sudo apt install postgresql-contrib
 1344  sudo systemctl start postgresql
 1345  sudo systemctl enable postgresql
 1348  sudo systemctl status postgresql
 
 1349 sudo -i -u postgres


```
## PgAdmin 4


```code
#
# Setup the repository
#

# Install the public key for the repository (if not done previously):
curl -fsS https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo gpg --dearmor -o /usr/share/keyrings/packages-pgadmin-org.gpg

# Create the repository configuration file:
sudo sh -c 'echo "deb [signed-by=/usr/share/keyrings/packages-pgadmin-org.gpg] https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'

#
# Install pgAdmin
#

# Install for both desktop and web modes:
sudo apt install pgadmin4

# Install for desktop mode only:
sudo apt install pgadmin4-desktop

# Install for web mode only: 
sudo apt install pgadmin4-web 

# Configure the webserver, if you installed pgadmin4-web:
sudo /usr/pgadmin4/bin/setup-web.sh
```


```code
setup-web.sh
pl@pop-os:~/pjs/repos/springboot/IdeaProjects/DemoSpringProj$ sudo /usr/pgadmin4/bin/setup-web.sh
Setting up pgAdmin 4 in web mode on a Debian based platform...
Creating configuration database...
/usr/pgadmin4/venv/lib/python3.10/site-packages/passlib/pwd.py:16: UserWarning: pkg_resources is deprecated as an API. See https://setuptools.pypa.io/en/latest/pkg_resources.html. The pkg_resources package is slated for removal as early as 2025-11-30. Refrain from using this package or pin to Setuptools<81.
  import pkg_resources
NOTE: Configuring authentication for SERVER mode.

Enter the email address and password to use for the initial pgAdmin user account:

Email address: squidpan11@gmail.com
Password: pe12rry12
Retype password: pe12rry12
/usr/pgadmin4/venv/lib/python3.10/site-packages/google/api_core/_python_version_support.py:266: FutureWarning: You are using a Python version (3.10.12) which Google will stop supporting in new releases of google.api_core once it reaches its end of life (2026-10-04). Please upgrade to the latest Python version, or at least Python 3.11, to continue receiving updates for google.api_core past that date.
  warnings.warn(message, FutureWarning)
pgAdmin 4 - Application Initialisation
======================================

Creating storage and log directories...
We can now configure the Apache Web server for you. This involves enabling the wsgi module and configuring the pgAdmin 4 application to mount at /pgadmin4. Do you wish to continue (y/n)? 

```

## PgAdmin 4 desktop issues


```code
connection failed: connection to server at "127.0.0.1", port 5432 failed: FATAL: password authentication failed for user "postgres" connection to server at "127.0.0.1", port 5432 failed: FATAL: password authentication failed for user "postgres" Multiple connection attempts failed. All failures were: - host: 'localhost', port: '5432', hostaddr: '::1': connection failed: connection to server at "::1", port 5432 failed: FATAL: password authentication failed for user "postgres" connection to server at "::1", port 5432 failed: FATAL: password authentication failed for user "postgres" - host: 'localhost', port: '5432', hostaddr: '127.0.0.1': connection failed: connection to server at "127.0.0.1", port 5432 failed: FATAL: password authentication failed for user "postgres" connection to server at "127.0.0.1", port 5432 failed: FATAL: password authentication failed for user "postgres"
```
