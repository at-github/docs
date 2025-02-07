# PostgresSQL

## Some tips in bulk

### Use postgres user
```shell
sudo su postgres
```

### Launch client
```shell
psql
```

### Pivot columns to lines
```sql
\x
```

### Create
```sql
CREATE DATABASE database_name;
```

```sql
CREATE USER user_name WITH ENCRYPTED PASSWORD 'password';
```

```sql
GRANT ALL PRIVILEGES ON DATABASE database_name to user_name;
```

```sql
ALTER USER user_name CREATEDB;
```

### Use database
```sql
\c database_name
```

### Describe

#### Table
```sql
\d table_name
```

```sql
\d+ table_name
```

### List

#### Database
```sql
\l
```

#### Table
```sql
\dt
```

```sql
\dt+
```
