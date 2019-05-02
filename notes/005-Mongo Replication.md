---
title: 005-Mongo Replication
tags: [Mongo]
created: '2019-04-30T22:47:24.923Z'
modified: '2019-05-02T23:20:41.866Z'
---

# 005-Mongo Replication  

## Replication benefits 

* Availability  
* Redundancy/failover 
* Dissaster Recovery 
* Reporting 
* Backup 
* Increases the data locality in distributed env 
* Increase the read frequency 


`Heartbeat` - Is a ping that is sent from one node to the other node to check for availability, 
`Replication Election Protocol` - is a primary election protocol used by mongodb to elect new servers 
`Arbitor` - is a dummy mongo db instance used to cast votes incase of ties 


## Mongo Architecture

* How do replicate Sets communicate? 
  * They communicate via `Heartbeat` 
  

* What is `Arbitor` 
  * _Arbitor_ is a empty mongodb instance with not data attached
    * It is used to cast a vote during `election` when primary goes down 


* Election for primary: Factors and conditions 
  * If the primary does not connect with any replicas for more than 10 secs the pirmary will call for election 
  * `Replication Election Protocol` _Mongo V3.2_ - used _memeber priority_ field and the protocol
  to find the best server that can be a _primary_ 
    * if _memeber priority_ is 0 the member can not call for eleciton 
  * **Data Center goes down**  
    * the second datacenter must have access to data nodes to start a election 
  * **Network Partition** - There are 6 servers that are partitioned into 2 sets, (primary, secondary) and (secondary, seondary, secondary, secondary) the set 2 will now elect their own primary.


## Voting and non voting members 

* _Voting Members_ 
  * Max of 7 voting member in a replica sets 

* _Non Voting Members_ 
  * Max of 43 non voting members in a replica set 

* **States**: Each member in a replica set has following state 
  * primary
  * secondary 
  * recovering 
  * rollback 
  * Arbitar 


## Configuration

Configuring a mongo node as a voting or non voting member 
```
{
  "id" = Num // automaticly filled 
  "host" = <hostname:port>
  "arbiterOnly" = true|false
  "buildIndexs" = true 
  "hidden" = true|false
  "priority" = 0|1 // for voting or nonvoting member
  "tags" = {

  }, 
  votes: 0|1 
}
``` 

## Delayed Node 
- is a node that syncs on a dealayed timer for a op log.
- has a limitation on the max time delayed becasue of oplog size   


## Write Concern  
`w: <value>, j:<boolen>, wTimeout: <number>` 
- w: the nubmer of mongo instances that should be written to `M` stands for majority 
- j: acknowledge that the write is durable 
- wrtieTimeout: time elapsed on the write 

## Read Preference 
1. primary(default) - all reads are done via primary 
2. primaryPerferred
3. secondary 
4. secondaryPrefered 
5. nearest - using ping for servers to find the nearest 
6. maxStalenes - maximum staleness withing some given time from primary 

  



