# Zookeeper cluster migration

```
### Zookeeper migration

1. Добавить новые ноды zk - corpint8, corpint9, corpint11

[zookeeper_business]
corpint4 zookeeper_id=1
corpint5 zookeeper_id=2
corpint7 zookeeper_id=4
corpint10    zookeeper_id=7
corpint11    zookeeper_id=5
corpint12    zookeeper_id=6

ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t zookeeper --limit '!corpint4:!corpint5:!corpint7'

2. Пересоздать zk ноды 1,2,4 по очереди, чтобы обновить у них zoo.cfg и присоеденить новые ноды к кластеру

ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t zookeeper --limit 'corpint4'
ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t zookeeper --limit 'corpint5'
ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t zookeeper --limit 'corpint7'

--- cat /etc/zookeeper/zoo.cfg
# Server list for clusters of 3 or more hosts
server.1=corpint4:2888:3888
server.2=corpint5:2888:3888
server.4=corpint7:2888:3888
server.5=corpint9:2888:3888
server.6=corpint11:2888:3888
server.7=corpint8:2888:3888

3. Проверить zk кластер `echo stat | nc corpint4 2181`

4. Пересоздать по очереди всех кафка брокеров с новым конфигом zookeeper.connect
Прописывается в env `-e KAFKA_ZOOKEEPER_CONNECT={{ kafka_zk_connect }}`

ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t kafka --limit 'corpint4'
ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t kafka --limit 'corpint5'
ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t kafka --limit 'corpint7'

проверять между брокерами, что они стартанули и начали отвечать

Проверить cat /etc/systemd/system/kafka.service
-e KAFKA_ZOOKEEPER_CONNECT=corpint4:2181,corpint5:2181,corpint7:2181,corpint8:2181,corpint9:2181,corpint11:2181 \

5. Остановить старые ноды по очереди
sudo systemctl start zookeeper.service
sudo rm /etc/systemd/system/zookeeper.service

6. Убрать старые ноды из инвентарника
[zookeeper_business]
corpint8    zookeeper_id=7
corpint9    zookeeper_id=5
corpint11   zookeeper_id=6

7. По очереди пересоздать zk ноды с новым zoo.cfg
ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t zookeeper --limit 'corpint8'
ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t zookeeper --limit 'corpint9'
ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t zookeeper --limit 'corpint11'

--- cat /etc/zookeeper/zoo.cfg
# Server list for clusters of 3 or more hosts
server.5=corpint9:2888:3888
server.6=corpint11:2888:3888
server.7=corpint8:2888:3888

8. По очереди пересоздать кафка брокеров, чтобы брокеры использовали новый конфиг zookeeper.connect

ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t kafka --limit 'corpint4'
ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t kafka --limit 'corpint5'
ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t kafka --limit 'corpint7'

```
