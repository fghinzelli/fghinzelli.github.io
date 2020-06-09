# postgreSQL
 
[Documentação](https://www.postgresql.org/docs/)


#### Comandos via terminal

##### Conectar à base local
```sql
  psql -U postgres
```

##### Listar databases
```sql
  \l
```

#### Restaurar backup
```sql
  pg_restore --user <usuario> --dbname=<database_name> <arquivo_backup.dmp>
```
