```shell
sudo su postgres
```

```shell
psql
```

```postgresql
CREATE DATABASE database_name;
```

```postgresql
CREATE USER user_name WITH ENCRYPTED PASSWORD 'password';
```

```postgresql
GRANT ALL PRIVILEGES ON DATABASE database_name to user_name;
```
