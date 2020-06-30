# postgreSQL
 
[Documentação](https://www.postgresql.org/docs/)

## Server commands
* **Reload server**
```service postgres-9.6 reload```
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
  pg_dump -h <host> -d <database> -U <usuario> > <arquivo_backup.dmp>
  pg_restore --user <usuario> --dbname=<database_name> <arquivo_backup.dmp>
```

* **Alterar formato de data**
```sql
ALTER DATABASE doe SET datestyle TO "ISO, DMY";
```
