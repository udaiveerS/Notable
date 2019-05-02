---
title: 002-Mongo Basics
tags: [Mongo]
created: '2019-04-30T22:47:24.923Z'
modified: '2019-05-01T05:35:16.917Z'
---

# 002-Mongo Basics 

## Database operation 

* **Create Database** 

Mongo Db creates databases on the fly so one way to create a database is to 

```
use myDBname 
db.newCollection.insertOne({foo: "foo"})
```

This command will create a new database called `myDBname` and a new collection called 
`new Collection` 



* **Drop Database**

``` 
> db.dropDatabase();
{ "dropped" : "myblogs", "ok" : 1 }
> show db
``` 

## Insert

**Insert one** 

```
b.coll1.insert({"name":"sunil", "rollNo":123})
```


**Insert Many** 

```
b.coll1.insert([
  {"name":"sunil", "rollNo":123},
  {"name":"sunil", "rollNo":123},
  {"name":"sunil", "rollNo":123},
  {"name":"sunil", "rollNo":123}
])
```


**Saving a document in a collectin** 

```
var articleInfo ={};
articleInfo.articleName= “MongoDB Introduction”;
articleInfo.authorName =”Sunil G”;
articleInfo.tags = [“database”,“NoSQL”,”DBA”,“DEV”];
// saving a document to collection
db.articles.save(articleInfo)
``` 


## Create Collections 

`db.createCollection(name, options)`

<p align="center">
  <img src="@attachment/mongo_notes/create-collection.png" width="592">
</p>

* _capped_ - automaticly deletes the old data based on the `max` memmory size 
* _autoIndexId_ - will add the index to the `_id` column in mongo 
* _size_ - the max data size in byes for collection 
* _max_ the max number of documents in the collection  


## Find elements 

* `db.myCol.find({name: "myName"})` 
query based of come exacy value 


* `db.myCol.find({age: {$eq:12}})`
query based on a qualifier: find all documents that have age of 12 

* `db.myCol.find({age: {$lt:9}})` 
Operators: **$lt | $gt | $lte | $gte | $ne ** 
query based on a qualifier: find all documents that have age less than 9 

### Array operators 

* `db.myCol.find({subject: {$in: ["small business"]}})` 
Operators: **$in | $nin ** 
- in, and nin work on subject even if subjects is a array 

* `db.myCol.find({subject: {$exist: true, $nin: ["small business"]}})` 
Query will check if the key subject exists and then check if its not "small business" 
- if exists is set to `fasle`, the query will return all objects not having subjects 

## Update 

* `db.studentCollection.update({name.firstName: "sunil"}, {$set:{age:17},{upsert=true}})`
The is a generic update statement and the upsert will add this element and the query
into the collection if it does no exist 

* `db.studentCollection.update({name.firstName: "sunil"}, {$set:{subjects.1:"Science"}})`
This database call does an update on the collections and sets the second value in the 
array to science 

## Delete 

* `db.studentsCollection.remote({"name.firstName": "Alun")})` -> greedy 
* `db.studentsCollection.remote({"name.firstName": "Alun")}, true)` -> only delete first one  
* `db.coll.remove({})` -> will remove all documents in a collection 

delete is greedy by default and will delte all mathing the query. 
- by passing true in the second param you tell mongo to delete only one document





