# kafka-series
````
cd d:\Work\kafka\kafka_2.11-1.0.1\bin\windows\
````
#starting zookeeper
````
kafka\bin\windows\zookeeper-server-start.bat ..\..\config\zookeeper.properties
````
#starting kafka
````
kafka\bin\windows\kafka-server-start.bat ..\..\config\server.properties
````
#starting kafka 2
````
kafka\bin\windows\kafka-server-start.bat ..\..\config\server2.properties
````
# TOPICS
````
kafka-topics.bat --zookeeper localhost:2181 --create --replication-factor 2 --partitions 2 --topic first
kafka-topics.bat --zookeeper localhost:2181 --describe --topic first
kafka-topics.bat --zookeeper localhost:2181 --create --replication-factor 2 --partitions 6 --topic second
kafka-topics.bat --zookeeper localhost:2181 --delete --topic second
kafka-topics.bat --zookeeper localhost:2181 --list`
````
# Producer
````
kafka-console-producer.bat --broker-list localhost:9092 --topic first
kafka-console-producer.bat --broker-list localhost:9092 --topic first --producer-property acks=all
````
# Consumer
````
kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic first --from-beginning
````
# Consumer group
````
kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic first --group my-first-group 
kafka-consumer-groups.bat --bootstrap-server localhost:9092 --list
kafka-consumer-groups.bat --bootstrap-server localhost:9092 --describe --group my-first-group
````
# Consumer group --reset-offsets
````
kafka-consumer-groups.bat --bootstrap-server localhost:9092 --group my-first-group --reset-offsets --to-earliest --execute --topic first
kafka-consumer-groups.bat --bootstrap-server localhost:9092 --group my-first-group --reset-offsets --shift-by -2 --execute --topic first
````