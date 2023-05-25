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
 ### 1. Vo sare batches ke naam btao jinke student ke marks 50% se kam hai
  ```sql
     db.batches.find(
  { marks: {$elemMatch: {$lt: 50} } },{batchName:1,_id:0});
  ```

### 2. marks array me se sirf vhi marks rkhne hain jo 60+= hain. baki sbko remove krdo
```sql
```
### 3. marks array me starting se 3rd index se 5 new marks add krne hai 
 ```sql
 db.batches.updateMany(
    {},
   {
     $push: {
        marks: {
           $each: [ 51, 61, 71,81,91 ],
           $position: 3
        }
     }
   }
)
```
### 4.Back/Last se 4th position se 5 new marks add krne hain.
 ```sql
 db.batches.updateMany(
    {},
   {
     $push: {
        marks: {
           $each: [ 51, 61, 71,81,91 ],
           $position: -4
        }
     }
   }
)
```
 ### 5.Students array ko ascending and marks Array ko desc order me sort krna hai 
 ```sql
db.batches.updateMany(
   {},
   { $push: { marks: { $each: [ ], $sort: -1 } } }
);
```
```sql

db.batches.updateMany(
   {},
   { $push: { student: { $each: [ ], $sort: 1 } } }
);

```
 ### 6.Marks array me sirf 10 numbers rkhne hain starting se baki sb remove kr dene hain
 ```sql
 db.batches.updateMany(
  { },
  {
    $push: {
      scores: {
         $each: [],
         $slice: 10
      }
    }
  }
);
```
###  7.Agar marks array me max number 99 hai to thik otherwise max number 99 krdo
 ```sql

db.batches.updateMany({},
  {  $max: { marks: 100 } },
);
```
### 8.fees field ko rename krke totalfees krdo 
 ```sql
 db.batches.updateMany(
   { },
   { $rename: { 'myScore': 'totalfees'} }
);
```
### 9. duration ko 2 se multiply krdo 
 ```sql
 db.batches.updateMany(
   {},
   { $mul:
      {
        duration : 2
       }
   }
)
```
 ### 10.students array me se Irfan, Adil ka naam hai to remove krdo
```sql
db.batches.updateMany(
  {},
  { $pull: { student: { $in: ["irfan", "aadil"] } } }
);
```

 ### 11.Agar fees 10000 se jyada hai to duration field ko remove krdo
 ```sql
  db.batches.updateMany(
  { totalfees: { $gt: 10000 } },
  { $unset: { duration: "" } }
);
```

 ### 12.Vo sare students search kro jinke naam me Khan hai aur batchName Designing hai aur fees 12000 se jyada hai aur students array ki size 10 ho
