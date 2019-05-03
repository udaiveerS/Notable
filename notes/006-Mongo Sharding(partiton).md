---
title: 006-Mongo Sharding(partiton)
tags: [Mongo]
created: '2019-04-30T22:47:24.923Z'
modified: '2019-05-03T05:46:04.121Z'
---

# 006-Mongo Sharding(partiton)

## Components 
<p align="center">
  <img src="@attachment/mongo_notes/mongo-shard-1.png" width="392">
</p>

**Mongo Cluster** - A mongo cluster the grouping of all replica sets for a given instance 

**Shard** - The shard in mongo should be a replica set, (AKA a mongod process with 2 replica sets or 1 replica and 1 arbiter). It is 

**Mongos** - The mongos acts as a query router, providing an interface between client applications and the sharded cluster. 

**Config servers** - Stores the metadata for sharded drivers.
* Config servers must also be deployed as a replica set  

**Application Driver** -

**Chunk** - A contiguous range of shard key values within a particular shard. 
* each shard consists of chunks, and each chunk has a size limit of 64GB before monog will splid that chunk. 

**Sharded Cluster Balancer** -  a background process that monitors the number of chunks on each shard. When the number of chunks on a given shard reaches specific migration thresholds, the balancer attempts to automatically migrate chunks between shards 

## Shards 
<p align="center">
  <img src="@attachment/mongo_notes/mongo-shard-2.png" width="392">
</p>

* Every swarm of mongo must have a primary shard. The primary shard stores the _non-sharded_ collections as well as (one or all? sharded collections)

## mongos 
<p align="center">
  <img src="@attachment/mongo_notes/mongo-shard-3.png" width="392">
</p>

### **Responsibilities**
* Caching metadata from config servers 
* Routes quries to shards 
* no persistent state 
* updates cache on metadata change 
* holds balancer 


#### Sharding Configuring 
1. Enable Sharding for the db via `sh.enableSharding("users");` 

2. Shard on a collection `sh.shardCollection("users.history",{user_id:1})` 

3. Use a sharding strategy (Range Based or Hash Based strategy) 


##### Shard Key  
* Shard key is a immutable field or fields that exist in every document 
* Cannot be changed after sharding. 
* To shard a non-empty collection, the collection must have an index that starts with the shard key.

###### Range Based Sharding 

###### Hash based sharding  



