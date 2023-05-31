# jsonSchema validation 
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
