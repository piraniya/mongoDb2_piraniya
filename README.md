**1. Create a Database called customers**
```
use customers
switched to db customers
```

**2. Create a collection called customerdetails**
```
db.createCollection("customerdetails")
{ ok: 1 }
```

**3. Insert all documents into the collection named customer details**
```
db.customerdetails.insertMany([{name:"John",age:25,gender:"Male",city:"New york"},{name:"Emily",age:22,gender:"Female",city:"London"},{name:"Daniel",age:28,gender:"Male",city:"Sydney"},{name:"Sophia",age:24,gender:"Female",city:"Paris"},{name:"William",age:26,gender:"Male",city:"Chicago"},{name:"Olivia",age:23,gender:"Female",city:"Los Angels"},{name:"Benjamin",age:27,gender:"male",city:"Toronto"},{name:"Mila",age:29,gender:"Female",city:"Berlin"},{name:"James",age:30,gender:"Male",city:"Tokyo"}])
{

{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("654ce405affcb26e5da41e72"),
    '1': ObjectId("654ce405affcb26e5da41e73"),
    '2': ObjectId("654ce405affcb26e5da41e74"),
    '3': ObjectId("654ce405affcb26e5da41e75"),
    '4': ObjectId("654ce405affcb26e5da41e76"),
    '5': ObjectId("654ce405affcb26e5da41e77"),
    '6': ObjectId("654ce405affcb26e5da41e78"),
    '7': ObjectId("654ce405affcb26e5da41e79"),
    '8': ObjectId("654ce405affcb26e5da41e7a")
  }
}
```
**4. Retrieve all documents from the collection and sort the results by the “age” field in ascending order**
```
db.customerdetails.find().sort({age:1})

[
  {
    _id: ObjectId("654ce405affcb26e5da41e73"),
    name: 'Emily',
    age: 22,
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e77"),
    name: 'Olivia',
    age: 23,
    gender: 'Female',
    city: 'Los Angels'
  },
{
    _id: ObjectId("654ce405affcb26e5da41e75"),
    name: 'Sophia',
    age: 24,
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e72"),
    name: 'John',
    age: 25,
    gender: 'Male',
    city: 'New york'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e76"),
    name: 'William',
    age: 26,
    gender: 'Male',
    city: 'Chicago'
  },
{
    _id: ObjectId("654ce405affcb26e5da41e78"),
    name: 'Benjamin',
    age: 27,
    gender: 'male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e74"),
    name: 'Daniel',
    age: 28,
    gender: 'Male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e79"),
    name: 'Mila',
    age: 29,
    gender: 'Female',
    city: 'Berlin'
  },
{
    _id: ObjectId("654ce405affcb26e5da41e7a"),
    name: 'James',
    age: 30,
    gender: 'Male',
    city: 'Tokyo'
  }
]
```
**5. Count the number of females.**
```
db.customerdetails.countDocuments({gender:"Female"})
```
4
**6. Insert one document into the customerdetails collection**
```
db.customerdetails.insertOne({name:"Juliana",age:30,gender:"Female",city:"Scabro"})

{
  acknowledged: true,
  insertedId: ObjectId("654ce55caffcb26e5da41e7b")
}
```
**7.Update city=SriLanka to John**
```
db.customerdetails.update({name:"John"},{$set:{city:"SriLanka"}})

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```
**8.Remove the customer from Tokyo**
```
db.customerdetails.remove({city:"Tokyo"})

DeprecationWarning: Collection.remove() is deprecated. Use deleteOne, deleteMany, findOneAndDelete, or bulkWrite.
{ acknowledged: true, deletedCount: 1 }
9.Find customers not from Los Angeles.

db.customerdetails.find({city:{$ne:"Los Angels"}})

[
  {
    _id: ObjectId("654ce405affcb26e5da41e72"),
    name: 'John',
    age: 25,
    gender: 'Male',
    city: 'SriLanka'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e73"),
    name: 'Emily',
    age: 22,
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e74"),
    name: 'Daniel',
    age: 28,
    gender: 'Male',
    city: 'Sydney'
  },
 {
    _id: ObjectId("654ce405affcb26e5da41e75"),
    name: 'Sophia',
    age: 24,
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e76"),
    name: 'William',
    age: 26,
    gender: 'Male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e78"),
    name: 'Benjamin',
    age: 27,
    gender: 'male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e79"),
    name: 'Mila',
    age: 29,
    gender: 'Female',
    city: 'Berlin'
  },
  {
    _id: ObjectId("654ce55caffcb26e5da41e7b"),
    name: 'Juliana',
    age: 30,
    gender: 'Female',
    city: 'Scabro'
  }
]
```
**10.Find the customers who are older than age 25**
```
db.customerdetails.find({age:{$lt:25}})

[
  {
    _id: ObjectId("654ce405affcb26e5da41e73"),
    name: 'Emily',
    age: 22,
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e75"),
    name: 'Sophia',
    age: 24,
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("654ce405affcb26e5da41e77"),
    name: 'Olivia',
    age: 23,
    gender: 'Female',
    city: 'Los Angels'
  }
]
```
**11.Retrieve the males who are less than 25**
```
db.customerdetails.find({gender:"Male",age:{$lt:25}})

empty data```
** 12. Update Francis age to 35; if Francis is not available  upsert**
```
db.customerdetails.update({name:"Francis"},{$set:{age:35}},{upsert:true})

{
  acknowledged: true,
  insertedId: ObjectId("654cecb742247926b5894c48"),
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 1
}
```

** 14. Find a customer who is lesser than or equal to  23**
```
db.customerdetails.find({age:{$lte:23}})


```
