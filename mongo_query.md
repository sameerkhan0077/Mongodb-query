# field update operators 
### $inc 
```sql
yh value ko increment krne ke ly kiya jata h or value nhi hoto value ko add kr deta h 

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
```sql
yh un value ko find krta h jtne number hm us me slice k ly dete h uni ko y slice krta h or return krta h 

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
```sql
addtoSet value ko add krta h or set krta h agr value h to add nhi krega agr value nhi h to use add kr ke set kr dega.

db.student.updateOne({ _id: 12 }, { $addToSet: { grades : 26 } });

y id 12 me grades 26 ko add kr dega last me
```


### $pop
```sql
y value ko us  array se remove krta h agr hm -1 me dete h to aage se krta h or 1 dete h piche se remove krta h.

db.student.updateOne({ _id: 17 }, { $pop: { grades: -1 } });
db.student.updateOne({ _id: 17 }, { $pop: { grades: 1 } });(piche se)
```
### $pull 
```sql 
 y hai value ko remove krne k ly use hota h agr value h to remove kr dega or nhih to remove nhi krega 
 
 db.student.updateOne({ _id: 11 }, { $pull: { grades: 70 } });
 db.nodejs.updateOne({ _id: 9 }, { $pull: { grades: { $gt: 85 } } });
 
 ```
### $.
```sql
$ ka use kese value ko update krne k ly use kiya jata h value ko change krne k ly kiya  jata h 

db.student.updateOne(
   { _id: 15, grades: 'sameer' },
   { $set: { "grades.$" : 'b.khan' } }
)
"sammer" ki jagh "b.khan" change kr diya is me id ke pass jis filed ko chnge krna h usko diya jata h ko $set ko bhi use kiya jata h.
```
### $unset 
```sql
yh jo value add hoti h usko htane k ly use me liya jata h 

db.student.updateOne(
  { _id : 4 },
  { $unset: { highscore: ""} }
);

isme jise filed ko htana h use ke aage "" lga k hta skte h 
```
