# Kafka cluster migration

```
1. добавить новые ноды в инвентарник
[kafka_broker_business]
corpint4 kafka_broker_id=1001
corpint5 kafka_broker_id=1002
corpint7 kafka_broker_id=1004
corpint8    kafka_broker_id=1005
corpint9    kafka_broker_id=1006
corpint11   kafka_broker_id=1007
corpint12   kafka_broker_id=1008

2. запустить новые ноды
ansible-playbook -i ./integration/inv-kafka-business kafka-business.yml -t kafka --limit '!corpint4:!corpint5:!corpint7'

3. проверить количество брокеров `echo dump | nc corpint8 2181`

4. повысить replication factor на новые ноды и сделать reassign
5. дождаться конца реассайна

6. добавить апишкам урлы на новых брокеров
bootstrap-servers:
    - 'corpint4:9092,corpint5:9092,corpint7:9092'
    - 'corpint8:9092,corpint9:9092,corpint11:9092,corpint12:9092'
перезапустить

7. выключить старые брокеры по очереди
8. уменьшить фактор репликации - реассайн

9. удалить в апишках страрые урлы
перезапустить

```

