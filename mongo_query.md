# field update operators 
### $inc 
yh value ko increment krne ke ly kiya jata h or value nhi hoto value ko add kr deta h 
```
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
