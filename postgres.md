# Postgres

# Install
```
$ sudo apt-get install postgresql-client
```
# Login
```
$ psql -h localhost -U postgres_usr -W postgres_db
```
# Common
|Command|Action|
|:------|:-----|
| \l    | databases |
| \c db | switch |
| \dt   | All tables in db |
# Creating a user and a database
```
$ createuser john -P
$ createdb --owner=john mydb
```
