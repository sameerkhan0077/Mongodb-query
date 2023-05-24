# query Questions 
### Create database
```sql
use wecodeacademy
```
### create collection
```sql
db.createCollection("batches");
```
###  add documents and data
```sql
db.batches.insertMany([
  {batchName : "Node.js", student : ["sameer khan", "sher ", "khalil","aarif khan"],
  duration : 5, fees: 5000, marks : [10,20,30,40,50]},
  ```
```sql
    {batchName : "designing", student : ["naveed khan", "soyal", "irfan khan", "adil khan"], 
    duration : 5, fees: 12000, marks : [30,40,50,60]},
```
```sql

    {batchName : "Javascript", student : ["jawed khan", "rasid khan", "frman khan", "sam khan"],
    duration : 5, fees: 12000, marks : [35,45,55,60,]}]);
  ```
