# Installation Instructions for Ubuntu 16.04 LTS

## Installation

### Install Java 8
 1. `$ add-apt-repository ppa:webupd8team/java`
 2. `$ apt-get update`
 3. `$ yes | apt-get install oracle-java8-installer`

### Install Kafka
 1. [Download Kafka](https://www.apache.org/dyn/closer.cgi?path=/kafka/0.11.0.1/kafka_2.11-0.11.0.1.tgz)
 2. `$ tar -xzf kafka_2.11-0.11.0.1.tgz`
 3. `$ cd kafka_2.11-0.11.0.1`
 
### Install ZooKeeper 
 1. [Download ZooKeeper](http://apache.mirrors.spacedump.net/zookeeper/stable/)
 2. `$ cd zookeeper-3.4.10`
 2. `$ sh bin/zookeeper-server-start.sh config/zookeeper.properties`
 3. `$ mv conf/zoo_sample.cfg conf/zoo.cfg`
 
## Verification

### Start ZooKeeper
```bash
$ sh bin/zkServer.sh start
ZooKeeper JMX enabled by default
Using config: /Users/.../zookeeper-3.4.10/bin/../conf/zoo.cfg
-n Starting zookeeper ... 
STARTED
```
### Start a Kafka Producer
```bash
$ cd kafka_2.11-0.11.0.1
$ bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
This is my first message
This is another message   
```

### Start a Kafka Consumer
```bash
$ cd kafka_2.11-0.11.0.1
$ sh bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
This is my first message
This is another message 
```
 