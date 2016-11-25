# MySQL

## Databases & Tables
```
mysql> show databases;
mysql> use {db};
mysql> show tables;
mysql> DESCRIBE {table}
mysql> SELECT table_name, table_schema
         FROM INFORMATION_SCHEMA.TABLES
        WHERE TABLE_TYPE = 'BASE TABLE'
          AND table_schema = '{db}'
mysql> drop database {db};
```

## User
```
mysql> desc mysql.user;
mysql> select * from mysql.user;
```
Common:
```
mysql> select host, user, password from mysql.user;
```

## Grants
```
mysql> SHOW GRANTS FOR openfire@'localhost';
mysql> SHOW GRANTS FOR CURRENT_USER;
```

## Login
```
$ sudo -i mysql
$ mysql -h IP -P 3306 -u user_name -pPass -D db_name -e 'SELECT 1 FROM dual;'
```

## Command Line
```
$ mysql openfiredb -e 'select * from ofUser'
```

## Set root password
```
$ mysql -u root
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpwd');
```

## Backup
```
$ mysqldump database_name > database_name.sql
$ mysqldump --databases db2 db3 > many_db.sql
$ mysqldump --all-databases > all_databases.sql
```
### Restoring
```
mysql database_name < database_name.sql
mysql --one-database database_name < all_databases.sql

```
