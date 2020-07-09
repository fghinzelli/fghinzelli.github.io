# postgreSQL
 
[Documentação](https://www.postgresql.org/docs/)

## Server commands
* **Reload server/configs**
```service postgres-9.6 reload```
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
