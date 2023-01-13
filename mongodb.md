# Mongo DB

**Select a Database**: ```use <db_name>```
**List databases**: ```show databases```
**List collections**: ```show collections```
**Find and select fields to list**: 
```db.items.find({"path": /servicos-online/}, {"path": 1, "updatedBy": 1, "updatedAt": 1}).pretty()```
