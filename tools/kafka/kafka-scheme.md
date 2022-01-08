# Kafka scheme

### 3zk - 3brokers

![](<../../.gitbook/assets/image (9) (1) (1).png>)

***

### 3 data centers

![](<../../.gitbook/assets/image (2) (1) (1).png>)

* rack.id=\<location>
* replica.selector.class= \<ReplicaSelector impl>
* Out of the box:
  * LeaderSelector (default)
  * RackAwareReplicaSelector

###

### 2 data centers

![](<../../.gitbook/assets/image (6) (2).png>)

* If dc1 goes down zookeeper wouldn't keep the quorum consensus.
* Outage.

![](<../../.gitbook/assets/image (1) (1).png>)

* Hierarchical zookeeper quorum.
* Brokers configured to talk with local zk's.
* Availability over consistency.
* Clients lose visibility of partition leaders in other DC
* Production either partially continues or blocks, depending on replication settings
* Manual intervention required to resume processing



![](<../../.gitbook/assets/image (3) (1) (1).png>)

![](<../../.gitbook/assets/image (10) (1).png>)

* ZooKeeper behavior is same as 3DC setup.
* Replication tradeoffs are the same as 2DC setup.

![](<../../.gitbook/assets/image (8) (1) (1).png>)

[Note width](https://www.evernote.com/client/web?\_sourcePage=7jVaQtBg9FPiMUD9T65RG\_YvRLZ-1eYO3fqfqRu0fynRL\_1nukNa4gH1t86pc1SP&\_\_fp=CNjcoCCKkE83yWPvuidLz-TPR6I9Jhx8\&hpts=1636349086780\&showSwitchService=true\&usernameImmutable=false\&rememberMe=true\&login=\&login=Sign+in\&login=true\&hptsh=C20w84OffDBq4cI4ezHJ2aCgLDk%3D)

* Mirror cluster to the second dc.
