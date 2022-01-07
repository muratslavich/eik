# Kafka reassignment

```
docker run --rm -it --dns-search=moscow.alfaintra.net infra.binary.alfabank.ru/cp-kafka:5.3.1 usr/bin/kafka-topics --zookeeper corpint4:2181 --list > ./reassignment/topics.json

docker run --rm -it --dns-search=moscow.alfaintra.net -v "$(pwd)"/reassignment:/app infra.binary.alfabank.ru/cp-kafka:5.3.1 usr/bin/kafka-reassign-partitions --zookeeper corpint4:2181 --topics-to-move-json-file /app/topics.json --broker-list "1001,1002,1004" --generate > ./reassignment/reassignments.json

docker run --rm -it --dns-search=moscow.alfaintra.net -v "$(pwd)"/reassignment:/app infra.binary.alfabank.ru/cp-kafka:5.3.1 usr/bin/kafka-reassign-partitions --zookeeper corpint4:2181 --reassignment-json-file /app/reassignment-new.json --throttle 50000000 --execute

docker run --rm -it --dns-search=moscow.alfaintra.net -v "$(pwd)"/reassignment:/app infra.binary.alfabank.ru/cp-kafka:5.3.1 usr/bin/kafka-reassign-partitions --zookeeper corpint4:2181 --reassignment-json-file /app/reassignment-new.json --verify




org.apache.zookeeper.KeeperException$NoAuthException: KeeperErrorCode = NoAuth for /config/topics/SIMPLE
	at org.apache.zookeeper.KeeperException.create(KeeperException.java:116)
	at org.apache.zookeeper.KeeperException.create(KeeperException.java:54)
	at kafka.zookeeper.AsyncResponse.maybeThrow(ZooKeeperClient.scala:560)
	at kafka.zk.KafkaZkClient.setOrCreateEntityConfigs(KafkaZkClient.scala:368)
	at kafka.zk.AdminZkClient.changeEntityConfig(AdminZkClient.scala:378)
	at kafka.zk.AdminZkClient.changeTopicConfig(AdminZkClient.scala:338)

http://support-it.huawei.com/docs/en-us/fusioninsight-all/maintenance-guide/en-us_topic_0222551464.html



$ docker exec -it kafka_um usr/bin/kafka-topics --zookeeper localhost:5151 --list

Error: JMX connector server communication error: service:jmx:rmi://corpint8.moscow.alfaintra.net:9988
sun.management.AgentConfigurationError: java.rmi.server.ExportException: Port already in use: 9988; nested exception is:
	java.net.BindException: Address already in use (Bind failed)
	at sun.management.jmxremote.ConnectorBootstrap.exportMBeanServer(ConnectorBootstrap.java:800)
	at sun.management.jmxremote.ConnectorBootstrap.startRemoteConnectorServer(ConnectorBootstrap.java:468)
	at sun.management.Agent.startAgent(Agent.java:262)
	at sun.management.Agent.startAgent(Agent.java:452)

```
