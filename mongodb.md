# Mongo DB

**Select a Database**: ```use <db_name>```

**List databases**: ```show databases```

**List collections**: ```show collections```

**Find and select fields to list**: 
```db.items.find({"path": /servicos-online/}, {"path": 1, "updatedBy": 1, "updatedAt": 1}).pretty()```

**Join two collections**:
```
db.orders.aggregate([
   {
     $lookup:
       {
         from: "items",
         localField: "_id",
         foreignField: "_id",
         as: "item"
       }
  },
  { $unwind: "$item" },
  {
    $project: {
        "_id": 1,
        "price": 1,
        "quantity": 1,
        "description": "$item.description",
        "instock": "$item.instock"
    }
  }
])
```
