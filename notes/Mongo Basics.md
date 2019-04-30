---
title: Mongo Basics
tags: [Mongo]
created: '2019-04-30T22:47:24.923Z'
modified: '2019-04-30T23:25:07.818Z'
---

# Mongo Basics 

## Database operation 

* **Create Database** 

Mongo Db creates databases on the fly so one way to create a database is to 
```
use myDBname 
db.newCollection.insertOne({foo: "foo"})
```

This command will create a new database called ```myDBname``` and a new collection called 
```new Collection``` 



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
db.articles.save(articleInfo);
```

## Create Collections 

``` db.createCollection(name, options)```





