1) show dbs (shows all databases)
2) use databasename (use to create or switch)
3) show collections (As name suggest)
4) db.collectionname.insertOne()  (it will create new collection if not created and insert data)
5) db.colletionname.find().pretty() (use to find or display)


*************************************************************

			:CRUD Operation🤖️:
			
1. Create

Create or insert operations add new documents to a collection. If the collection does not currently exist, insert operations will create the collection.

Syntax:
db.collection.insertOne() 
db.collection.insertMany() 

Example:

> use Programming
switched to db Programming
> show collections
> db.Programming.insertOne({
         "lang": "Python",
         "Version": "3"
    })

> db.Programming.insertMany([
     {
         "lang": "Python",
         "Version": "3"
     },
     {
         "lang": "JavaScript",
         "Version": "1.8"
     },
     {
         "lang":"PHP",
         "Version":"8.0"
     }
  ])
 



2. Read
Read operations retrieve documents from a collection; i.e. query a collection for documents. MongoDB provides the following methods to read documents from a collection:

Syntax:
db.collection.find()
db.collection.find().pretty()

Example:

db.Programming.find()
{ "_id" : ObjectId("5ff2fd971406b52929a7bc9f"), "lang" : "Python", "Version" : "3" }
{ "_id" : ObjectId("5ff2fe011406b52929a7bca0"), "lang" : "Python", "Version" : "3" }
{ "_id" : ObjectId("5ff2fe011406b52929a7bca1"), "lang" : "JavaScript", "Version" : "1.8" }
{ "_id" : ObjectId("5ff2fe011406b52929a7bca2"), "lang" : "PHP", "Version" : "8.0" }


db.Programming.find().pretty()
{
	"_id" : ObjectId("5ff2fd971406b52929a7bc9f"),
	"lang" : "Python",
	"Version" : "3"
}
{
	"_id" : ObjectId("5ff2fe011406b52929a7bca0"),
	"lang" : "Python",
	"Version" : "3"
}
{
	"_id" : ObjectId("5ff2fe011406b52929a7bca1"),
	"lang" : "JavaScript",
	"Version" : "1.8"
}
{
	"_id" : ObjectId("5ff2fe011406b52929a7bca2"),
	"lang" : "PHP",
	"Version" : "8.0"
}



3. Update
Update operations modify existing documents in a collection. MongoDB provides the following methods to update documents of a collection:

Syntax:
db.collection.updateOne() 
db.collection.updateMany() 
db.collection.replaceOne() 

Example:

db.Programming.updateMany({ lang:"PHP"},{$set: {Release_Date: "26 November 2020"}})

db.Programming.find().pretty()
{
	"_id" : ObjectId("5ff2fd971406b52929a7bc9f"),
	"lang" : "Python",
	"Version" : "3"
}
{
	"_id" : ObjectId("5ff2fe011406b52929a7bca0"),
	"lang" : "Python",
	"Version" : "3"
}
{
	"_id" : ObjectId("5ff2fe011406b52929a7bca1"),
	"lang" : "JavaScript",
	"Version" : "1.8"
}
{
	"_id" : ObjectId("5ff2fe011406b52929a7bca2"),
	"lang" : "PHP",
	"Version" : "8.0",
	"Release_Date" : "26 November 2020"
}


4. Delete
Delete operations remove documents from a collection. MongoDB provides the following methods to delete documents of a collection:

Syntax:
db.collection.deleteOne() 
db.collection.deleteMany() 


Example:

db.Programming.deleteMany({}) It will select and delete all delete.



*********************************************************************

Get Specified Data:


db.Programming.find({lang:"PHP"}).pretty()

{
	"_id" : ObjectId("5ff2fe011406b52929a7bca2"),
	"lang" : "PHP",
	"Version" : "8.0",
	"Release_Date" : "26 November 2020"
}

db.Programming.findOne({lang:"PHP"})
(It will return very first match)

{
	"_id" : ObjectId("5ff2fe011406b52929a7bca2"),
	"lang" : "PHP",
	"Version" : "8.0",
	"Release_Date" : "26 November 2020"
}


Aggregation:


db.Books.find().forEach( (bookdata) => {printjson(bookdata.Book)} ) // it is costly operation //it will send everything and then filter out it as per your query.


db.Books.find({}, {Book: 1} ) //it will send email with id and it is cost effective

db.Books.find({}, {Book: 1, _id:0} ) //it return email only 0 means "no" and 1 mean "yes"

db.Books.find({}, {Book: 1, _id:0} ).toArray() // it return email in toArray

db.student_Data.find({name: "Shivam"}) // it return only shivam's data

db.student_Data.findOne({name:"Shivam"}).lastlogin //it return perticular key like lastlogin








