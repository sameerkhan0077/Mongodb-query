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
addtoSet value ko add krta h or set krta h agr value h to add nhi krega agr value nhi h to use add kr ke set kr dega
```sql
db.student.updateOne({ _id: 12 }, { $addToSet: { grades : 26 } });
```
y id 12 me grades 26 ko add kr dega last me
