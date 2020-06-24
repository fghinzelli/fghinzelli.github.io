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
  psql -U postgres
```

* **Listar databases**
```sql
  \l
```

* **Restaurar backup**
```sql
  pg_restore --user <usuario> --dbname=<database_name> <arquivo_backup.dmp>
```
