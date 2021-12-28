## Generate a list of values

```SELECT * FROM TABLE(sys.odcinumberlist(1,2,3,4,5,6,7,8,9);```


## Get all tables with relation to one

```
select table_name, constraint_name, status, owner
from all_constraints
where r_owner = 'ADMRH'
and constraint_type = 'R'
and r_constraint_name in
 (
   select constraint_name from all_constraints
   where constraint_type in ('P', 'U')
   and table_name = 'FUNCIONARIOS'
   and owner = 'ADMRH'
 )
order by table_name, constraint_name
```
## Update sequence index

```
ALTER SEQUENCE ADMRH.OPERADORES_SEQ INCREMENT BY 362;
SELECT ADMRH.operadores_seq.NEXTVAL FROM dual
ALTER SEQUENCE ADMRH.OPERADORES_SEQ INCREMENT BY 1;
```

## Get data of sequence

```
SELECT *
  FROM all_sequences 
  where 
  sequence_owner = 'ADMRH' AND
  sequence_name = 'OPERADORES_SEQ'
```
## Find columns of a table
```
select COLUMN_NAME from ALL_TAB_COLUMNS where TABLE_NAME='DEPENDENTES' AND OWNER = 'ADMRH' ORDER BY COLUMN_ID;
```
