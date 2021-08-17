# postgreSQL
 
[Documentação](https://www.postgresql.org/docs/)

## Server commands
* **Reload server/configs**
```service postgres-9.6 reload``` or 
```/etc/init.d/postgresql-8.2 reload```
* **Permissões de acesso**
```vim /var/lib/pgsql/pg_hba.conf```



## Client commands

* **Connect to a database**
```sql
  psql -U postgres -p <porta> -h <host> -d <database_name>
```

* **Listar databases**
```sql
  \l
```

* **Backup / Restore**
```sql
  pg_dump -h <host> -d <database> -U <usuario> -v > <arquivo_backup.dmp>
  
  pg_restore -U <usuario> -d=<database_name> < <arquivo_backup.dmp>
  
  # Restore from text file
  psql -h <host> -p <port> -U <usuario> -d <database> < <file_backup.sql>
```

* **Alterar formato de data**
```sql
ALTER DATABASE doe SET datestyle TO "ISO, DMY";
```

* **Alterar timezone**
```sql
SET TIMEZONE='Brazil/East'
```

* **Permissões**
```sql
GRANT ALL PRIVILEGES ON DATABASE|TABLE <name> TO <username>;

-- 1. Grant CONNECT to the database:
GRANT CONNECT ON DATABASE database_name TO username;

-- 2. Grant USAGE on schema:
GRANT USAGE ON SCHEMA schema_name TO username;

-- 3. Grant on all tables for DML statements: SELECT, INSERT, UPDATE, DELETE:
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA schema_name TO username;

-- 4. Grant all privileges on all tables in the schema:
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA schema_name TO username;

--5. Grant all privileges on all sequences in the schema:
GRANT ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA schema_name TO username;

--6. Grant all privileges on the database:
GRANT ALL PRIVILEGES ON DATABASE database_name TO username;

--7. Grant permission to create database:
ALTER USER username CREATEDB;

--8. Make a user superuser:
ALTER USER myuser WITH SUPERUSER;

--9. Remove superuser status:
ALTER USER username WITH NOSUPERUSER;
```
* **CAST**

``` TO_CHAR(TO_TIMESTAMP(bigint_field / 1000), 'DD/MM/YYYY HH24:MI:SS')```

* **Datestyle**
Chage the file */var/lib/postgresql/data/postgres.conf*
```datestyle = 'iso, dmy'```
