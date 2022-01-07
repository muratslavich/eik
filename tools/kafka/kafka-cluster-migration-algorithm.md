# Kafka cluster migration algorithm

## 1-2-3 -> 4-5-6

1. Add new brokers to cluster
   1. start brokers
   2. verify that they are part of cluster
   3. **NOTE:**
2. Add new cluster to the API's configuration
3. Increase replication factor
   1. get all topics
   2. create partition reassignment json file
   3. generate -> execute -> verify

```
usr/bin/kafka-reassign-partitions.sh --zookeeper localhost:2181 --topics-to-move-json-file replica-info.json --broker-list “1,2,4,5” --generate

// 50 mb/s
usr/bin/kafka-reassign-partitions.sh --zookeeper localhost:2181 --reassignment-json-file expand-cluster-reassignment.json --throttle 50000000 --execute

usr/bin/kafka-reassign-partitions.sh --zookeeper localhost:2181 --reassignment-json-file expand-cluster-reassignment.json --verify
```

1. Decommission old brokers
   1. shift url to new brokers
   2. shutdown old brokers
2. Decrease replication factor to its initial value
   1. repeat commands with new json file

```
cat replica-info.json
{  
   "version":1,
   "Partitions":[  
      {  
         "topic":"foo1",
         "partition":0,
         "replicas":[4, 5]
      },
      {  
         "topic":"foo1",
         "partition":1,
         "replicas":[4, 5]
      },
      {  
         "topic":"foo2",
         "partition":0,
         "replicas":[4, 5]
      },
      {  
         "topic":"foo2",
         "partition":1,
         "replicas":[4, 5]
      }
   ]
}

$ bin/kafka-reassign-partitions.sh --zookeeper localhost:2181 --topics-to-move-json-file replica-info.json --broker-list “1,2,4,5” --generate

$ bin/kafka-reassign-partitions.sh --zookeeper localhost:2181 --reassignment-json-file expand-cluster-reassignment.json --execute

$ bin/kafka-reassign-partitions.sh --zookeeper localhost:2181 --reassignment-json-file expand-cluster-reassignment.json --verify
```

Migrate zookeeper then

1. add zk node
   1. verify
2. do rolling restart of all the other instances with updated configuration file. Restart the leader last
3. decommission any of old
   1. shut down instance
   2. Remove instance N entry from the configuration file of instances and do a rolling restart. (Restart the leader last)
4. Repeat

***

I think, the process of adding 1 zk and removing 1zk is fine, but that would also require to update kafka broker config zookeeper.connect to point to new zk nodes, otherwise kafka brokers will not be able to talk to zookeeper.

I am trying below approach, and so far its working fine for me:

* Add new zk nodes(4,5,6) at a time.
* For ZK\[1..6] in rolling manner - Update the zoo.cfg file and restart zookeeper service. \[To make 4,5,6 to join cluster]
* For Kafka brokers, in rolling manner - Update zookeeper.connect config and restart Kafka service. \[To let Kafka know about new zk nodes]
* Remove old ZK node(1,2,3), and update ZK\[4,5,6] configs, restart in rolling manner.
* For Kafka brokers, in rolling manner — Update zookeeper.connect config and restart Kafka service. \[To let Kafka update to point to new ZK nodes only, and remove old ZK nodes from config]
