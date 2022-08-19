# mysql

## Create database
`CREATE DATABASE databasename;`

## Create user & grant it for one database

### Create user
`CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';`

### Grant all privileges to username on databasename
`GRANT ALL ON databasename.* TO 'username'@'localhost';`

### Delete user
DROP USER 'username';

## Restore database
`mysql -u username -p databasename < filename.sql`
