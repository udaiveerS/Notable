---
title: 003-Mongo Indexing
tags: [Mongo]
created: '2019-04-30T22:47:24.923Z'
modified: '2019-05-01T08:12:21.800Z'
---

# 003-Mongo Indexing  

Mongo db stores indexes in a B-Tree and tries to store the indexes in memory
 
## Creating a index 
* `db.studentsInfoCollection.createIndex({age:1});`
- the `1` here reperents ascending or decending  

## finding all indexes in a colleciton 
* `db.studentsInfoCollection.getIndexes();`


* `db.accounts.dropIndex( { "tax-id": 1 } )`
`






