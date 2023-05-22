# Query and Projection Operators
### Comparison
### $eq
```
value uske equal  ho to.
```
### $gt 
```
value uske greterthan
```
### $gte
```
value uske greterthan equal ho to.
```
### $in
```
value us array ke ander h to return kr dega .
```
### $lt
```
values de gi value se km ya lessthan h to.
```
### $lte
```
value de gi values koi km ya barar h to .
```
### $ne
```
value di gi values k not equal h nhi hone chaiy.
```
### $nin
```
not in yani us array ke andr nhi hone chaiy.
```
# Logical
### $and
```
di gi query me dono condition true ho jati h to query ke sare documents return kr degi or ak bhi glt ho gi to kuch
return nhi kregi
```
### $or
```
di gi query me ak bhi condition true h to query ke sare documents return kr gi  nhi kuch bhi return nhi kregi 
```
### $not 
```
di gi query us condiition nhi mile chay y query returns documents that do not match the query . 
```
### $nor
```
Joins query clauses with a logical NOR returns all documents that fail to match both clauses.
```

# field update operators 
### $inc 

yh value ko increment krne ke ly kiya jata h or value nhi hoto value ko add kr deta h 
```sql
  db.student.insertOne({
 "_id":4,
 "name" :"sam",
 "highscore":500,
 "lowscore" :400});
 
 db.student.updateOne(
   { _id:5  },
   { $inc: { highscore: 200, fees: -500 } }
)
```
highscore ko 800 kr dega or fees ko -500 add kr dega

### $slice 

yh un value ko find krta h jtne number hm us me slice k ly dete h uni ko y slice krta h or return krta h 
```sql
db.student.insertMany([
   { "_id" : 15, "semester" : 1, "grades" : [ 'sameer', 'khan', 'sam' ] },
{ "_id" : 16, "semester" : 1, "grades" : [ 'sam','samer','samir' ] },
{ "_id" : 17, "semester" : 1, "grades" : [ 'sam','smir','k' ] },
])

db.student.find({ _id: 16 }, { grades: { $slice: 2 } });
{
  _id: 16,
  semester: 1,
  grades: [
    'sam',
    'samer'
  ]
}
```
### $addToSet

addtoSet value ko add krta h or set krta h agr value h to add nhi krega agr value nhi h to use add kr ke set kr dega.
```sql
db.student.updateOne({ _id: 12 }, { $addToSet: { grades : 26 } });
```
y id 12 me grades 26 ko add kr dega last me



### $pop

y value ko us  array se remove krta h agr hm -1 me dete h to aage se krta h or 1 dete h piche se remove krta h.
```sql
db.student.updateOne({ _id: 17 }, { $pop: { grades: -1 } });
db.student.updateOne({ _id: 17 }, { $pop: { grades: 1 } });(piche se)
```
### $pull 

 y hai value ko remove krne k ly use hota h agr value h to remove kr dega or nhih to remove nhi krega 
 ```sql 
 db.student.updateOne({ _id: 11 }, { $pull: { grades: 70 } });
 db.nodejs.updateOne({ _id: 9 }, { $pull: { grades: { $gt: 85 } } });
 
 ```
### $.

$ ka use kese value ko update krne k ly use kiya jata h value ko change krne k ly kiya  jata h 
```sql
db.student.updateOne(
   { _id: 15, grades: 'sameer' },
   { $set: { "grades.$" : 'b.khan' } }
)
```
"sammer" ki jagh "b.khan" change kr diya is me id ke pass jis filed ko chnge krna h usko diya jata h ko $set ko bhi use kiya jata h.

### $unset 

yh jo value add hoti h usko htane k ly use me liya jata h 
```sql
db.student.updateOne(
  { _id : 4 },
  { $unset: { highscore: ""} }
);
```
isme jise filed ko htana h use ke aage "" lga k hta skte h 

