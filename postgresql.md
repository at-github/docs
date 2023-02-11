```shell
sudo su postgres
```

```shell
psql
```

```sql
CREATE DATABASE database_name;
```

```sql
CREATE USER user_name WITH ENCRYPTED PASSWORD 'password';
```

```sql
GRANT ALL PRIVILEGES ON DATABASE database_name to user_name;
```
