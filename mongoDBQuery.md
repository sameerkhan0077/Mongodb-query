# jsonSchema validation 
```sql
use wecodeacademy
```
```sql
db.createCollection("students", {
  validator: {
$jsonSchema: {
 bsonType: "object",
 
 required: [ "name" , "fatherName", "motherName", "DOB" ,  "emailid" ,"mobile","address","batchName","fees","marks" ],
 properties: {
 name: {
 bsonType: "string",
description: "studentName must be a string"
 },
  fatherName: {
  bsonType: "string",
 description: "fatherName must be a string"
 },
  motherName: {
bsonType:"string",
description: "motherName must be a string"
            },
dob:{
    bsonType:"date"
},
 mobile: {
        bsonType : "string",
        pattern: "^(\+?91|0)?[6789]\d{9}$"
      },
emailid:{
    bsonType:"string",
    description:"emaile address string",
     pattern:"^[a-zA-Z0-9._]+@+[a-zA-Z]+\.+[a-zA-Z]{2,}$"
},
address:{
    bsonType:"string",
    description:"student address must be string",
},
batchName:{
    enum:['nodejs' ,'designing' , 'javascript' , 'computerscience'],
    description:"batchName should be string or enum",
},
fees:{
    bsonType:"Number",
     minimum: 2000,
      maximum: 50000,
      description:"fees must be a number and min 2000 or max 50000"
},
marks:{
    bsonType: "array",
    description:"marks in array"
}
}
}   
}
})
```
# Query 
### 1. Create a collection named "books" in MongoDB.
```sql
db.createCollection("books)
```

### 2. Insert a document into the "books" collection with the following details:
 Title: "The Great Gatsby"
  Author: "F. Scott Fitzgerald"
  Year: 1925
```sql
db.books.insrtOne({
   Title: "The Great Gatsby",
  Author: "F. Scott Fitzgerald",
  Year: 1925 
})
```
### 3. Insert another document into the "books" collection with the following details:

  Title: "To Kill a Mockingbird"
  Author: "Harper Lee"
  Year: 1960

  ```sql
db.books.insrtOne({
 Title: "To Kill a Mockingbird",
  Author: "Harper Lee",
  Year: 1960
})
```

### 4. Write a query to find all documents in the "books" collection.
```sql
db.books.find({})
```

### 5. Write a query to find documents in the "books" collection where the author is "F. Scott Fitzgerald".
```sql
db.Books.find({Author : { $eq : "F. Scott Fitzgerald"}});
```

### 6. Write a query to find documents in the "books" collection where the year is greater than 1950.

```sql
db.books.find({Year  : { $gt : 1950}});
```

### 7. Write an update query to change the author of the document with the title "To Kill a Mockingbird" to "Harper Lee (edited)".
```sql
db.books.updateOne(
    {Title:"To Kill a Mockingbird"},
{$set:{author}"Harper Lee (edited)"})
```

### 8. Write an update query to add a new field "genre" with the value "Fiction" to all documents in the "books" collection.
```sql
db.books.updateMany({},{$set:{"genre":"Fiction}})
```

### 9. Write a query to find documents in the "books" collection where the genre is "Fiction".
```sql
db.books.find({genre:{$eq:"Fiction"}})
```

### 10. Write a query to find documents in the "books" collection where the title starts with the letter "T".
```sql
db.books.find({},{Title:/^T/})
```
### 11. Write an update query to increment the year by 1 for all documents in the "books" collection.
```sql
db.books.updateMany({}, { $inc: { Year: 1,} })
```

### 12. Write a query to find documents in the "books" collection where the year is between 1950 and 1970.
```sql
db.books.find(,{Year:{$gt:1950,$lt:1970}})
```

### 13. Write a query to find documents in the "books" collection where the author's name contains the letter "a".
```sql
db.books.find({Author: /a/ })
```
### 14. Write an update query to remove the "genre" field from all documents in the "books" collection.
```sql
db.books.updateMany({},{ $unset: {genre : ""} })
```

###  15. Write a query to find documents in the "books" collection where the author's name ends with the letter "y".
```sql
db.books.find({Author: /y$/ })
```

###  16. Write an update query to change the title of the document with the author "Harper Lee" to "Go Set a Watchman".

```sql
db.books.updateOne({Author:"Harper Lee(edited)"},{$set:{Author:"Go Set a Watchman"}})
```

###  17. Write a query to find documents in the "books" collection where the title contains the word "Great".
```sql
db.books.find({Title:/Great/})
```

###  18. Write a query to find documents in the "books" collection where the title is an exact match for "The Great Gatsby".

```sql
db.books.find({Title:{$eq:"The Great Gatsby"}})
```

###  19. Write an update query to add an array field named "categories" with the values ["Classic", "Fiction"] to all documents in the "books" collection.

```sql
db.books.updateMany({},{$set:{categories:["Classic", "Fiction"] }})
```

###  20. Write a query to find documents in the "books" collection where the "categories" field contains the value "Fiction".
```sql
db.books.find({categories:"Fiction"})
```

###  21. Write a query to find documents in the "books" collection where the title contains the word "The" in a case-insensitive manner.

```sql
db.books.find({Title:/The/})
```

###  22. Write a query to find documents in the "books" collection where the author's name starts with the letter "J".
```sql
db.books.find({Author:/^J/});
```

### 23. Write an update query to increment the "year" field by 5 for all documents in the "books" collection.

```sql
db.books.updateMany({}, { $inc: { Year: 5,} })
```

###  24. Write a query to find documents in the "books" collection where the title is not equal to "Moby Dick".

```sql
db.books.find({Title:{$ne:"Moby Dick"}})
```
###  25. Write a query to find documents in the "books" collection where the author's name is either "J.K. Rowling" or "George R.R. Martin".

```sql
db.books.find({$or:[{Author:"J.K.Rowling"}, {Author: "George R.R. Martin"}]})
```

###  26. Write a query to find documents in the "books" collection where the year is either 2000 or 2010.
```sql
db.books.find({$or:[{Year:2000}, {Year:2010}]})
```
###  27. Write an update query to multiply the "year" field by 2 for all documents in the "books" collection.
```sql
db.books.updateMany({},{$mul:{Year: 2}})
```

###  28. Write a query to find documents in the "books" collection where the title ends with the letter "s".
```sql
db.books.find({ Title: /s$/ })
```

###  29. Write a query to find documents in the "books" collection where the author's name is not in ["Stephen King", "Agatha Christie"].
```sql
db.books.find( { Author: { $nin: [ "Stephen King", "Agatha Christie" ] } } )
```
### 30. Write an update query to set the "year" field to 2022 for the document with the highest year in the "books" collection.
```s ql
db.books.updateOne(
  { },
  { $set: { "Year": 2022 } },
  { sort: { "Year": -1 }}
)
```

