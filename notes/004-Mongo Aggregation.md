---
title: 004-Mongo Aggregation
tags: [Mongo]
created: '2019-04-30T22:47:24.923Z'
modified: '2019-05-01T19:08:54.454Z'
---

# 004-Mongo Aggregation  

Mongo Aggregation grouping data over document by using grouping operators 

## Group documents based on a author and cout 
* `db.studentsInfoCollection.createIndex({age:1});`
- the `1` here reperents ascending or decending  

## count the number of blog posts made by an author 
* `db.postCollection.aggregate({$sum:{_id:"$author", totalPosts:{$sum:1}}})`
<p align="center">
  <img src="@attachment/mongo_notes/aggregation-res1.png" width="592">
</p>


## Using _distinct_ and _count_ 
* `db.postCollection.distinct(subjects)`

res 

```
[ 
  "subject1",
  "subject2",
  "subject3",
]
``` 
The distinct can also work on arays 


* `db.postCollection.find({name: "mango"}).count()`
This will count all the documents that have 











