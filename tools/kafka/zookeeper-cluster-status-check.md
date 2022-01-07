# Zookeeper cluster status check

### Zookeeper commands - four letter words

[https://zookeeper.apache.org/doc/r3.4.14/zookeeperAdmin.html#sc\_zkCommands](https://zookeeper.apache.org/doc/r3.4.14/zookeeperAdmin.html#sc\_zkCommands)

* _**conf**_
* _cons_
* _crst_
* _dump_
* _envi_
* _ruok_
* _srst_
* _srvr_
* _stat_
* _wchs_
* _wchc_
* _dirs_
* _wchp_
* _mntr_

```
// информация о эфемерных нодах
$ echo dump | nc localhost 2181

SessionTracker dump:
org.apache.zookeeper.server.quorum.LearnerSessionTracker@3a8ed14a
ephemeral nodes dump:
Sessions with Ephemerals (3):
0x102a8bca0cc0000:
        /controller
        /brokers/ids/1004
0x102a8bca0cc0001:
        /brokers/ids/1001
0x40ab0daa67e0074:
        /brokers/ids/1002

// у лидера
$ echo mntr | nc corpint7 2181

zk_version      3.4.14-4c25d480e66aadd371de8bd2fd8da255ac140bcf, built on 03/06/2019 16:18 GMT
zk_avg_latency  0
zk_max_latency  1650
zk_min_latency  0
zk_packets_received     2110310
zk_packets_sent 1526598
zk_num_alive_connections        10
zk_outstanding_requests 0
zk_server_state leader
zk_znode_count  12792
zk_watch_count  45966
zk_ephemerals_count     4
zk_approximate_data_size        1522220
zk_open_file_descriptor_count   136
zk_max_file_descriptor_count    1048576
zk_fsync_threshold_exceed_count 8
zk_followers            2                      <-------------- количество фоловеров
zk_synced_followers     2
zk_pending_syncs        0
zk_last_proposal_size   36
zk_max_proposal_size    288377
zk_min_proposal_size    32

$ echo conf | nc corpint7 2181
clientPort=2181                                <-------------- порт
dataDir=/var/lib/zookeeper/version-2
dataLogDir=/var/lib/zookeeper/version-2
tickTime=2000
maxClientCnxns=60
minSessionTimeout=4000
maxSessionTimeout=40000
serverId=4
initLimit=10
syncLimit=5
electionAlg=3
electionPort=3888                               <-------------- порт
quorumPort=2888
peerType=0
```

## jmx connect

***

[https://docs.confluent.io/3.2.0/cp-docker-images/docs/operations/monitoring.html#launching-kafka-and-zookeeper-with-jmx-enabled](https://docs.confluent.io/3.2.0/cp-docker-images/docs/operations/monitoring.html#launching-kafka-and-zookeeper-with-jmx-enabled)

[https://zookeeper.apache.org/doc/r3.4.14/zookeeperJMX.html](https://zookeeper.apache.org/doc/r3.4.14/zookeeperJMX.html)

[https://stackoverflow.com/questions/41457491/how-do-i-enable-remote-jmx-with-port-in-zookeeper-zkserver-cmd](https://stackoverflow.com/questions/41457491/how-do-i-enable-remote-jmx-with-port-in-zookeeper-zkserver-cmd)
