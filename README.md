# Kafka tutorial


1. [Setup project](#setup)
2. [Kafka Installation Instructions for Ubuntu 16.04 LTS](#install)
3. [Command line Exercises](#CommandExercises)
4. [Java Exercises](#JavaExercises)


<a name="setup"></a>
## Setup project
`$ mvn clean install`

<a name="install"></a>
## Kafka Installation Instructions for Ubuntu 16.04 LTS

### Installation

#### Install Java 8
 1. `$ add-apt-repository ppa:webupd8team/java`
 2. `$ apt-get update`
 3. `$ yes | apt-get install oracle-java8-installer`

#### Install Kafka
 1. [Download Kafka](https://www.apache.org/dyn/closer.cgi?path=/kafka/0.11.0.1/kafka_2.11-0.11.0.1.tgz)
 2. `$ tar -xzf kafka_2.11-0.11.0.1.tgz`
 3. `$ cd kafka_2.11-0.11.0.1`
 
#### Install ZooKeeper 
 1. [Download ZooKeeper](http://apache.mirrors.spacedump.net/zookeeper/stable/)
 2. `$ cd zookeeper-3.4.10`
 2. `$ sh bin/zookeeper-server-start.sh config/zookeeper.properties`
 3. `$ mv conf/zoo_sample.cfg conf/zoo.cfg`

 
### Verification

#### Start ZooKeeper
```bash
$ sh bin/zkServer.sh start
ZooKeeper JMX enabled by default
Using config: /Users/.../zookeeper-3.4.10/bin/../conf/zoo.cfg
-n Starting zookeeper ... 
STARTED
```
#### Start a Kafka Producer
```bash
$ cd kafka_2.11-0.11.0.1
$ bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
This is my first message
This is another message   
```

#### Start a Kafka Consumer
```bash
$ cd kafka_2.11-0.11.0.1
$ sh bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
This is my first message
This is another message 
```
 
 <a name="CommandExercises"></a>
## Command Line Exercises

### Verify that Kafka is running correctly
There are various ways to verify that all of the Kafka system’s daemons are running. It is important to verify that Kafka is functioning correctly before you start to use it. You may need to restart a daemon process during the class, if it has terminated for some reason.

```bash
$ sudo jps
2183 Jps1752 SupportedKafka 
1832 SchemaRegistryMain 
1775 KafkaRestMain 
1487 QuorumPeerMain
```
The four Kafka-related processes you should see, and their Linux service names, are:

| Java Process Name        | Service Name           | 
| ------------- |:-------------:| 
| QuorumPeerMain      | zookeeper | 
| SupportedKafka      | kafka-server      |  
| KafkaRestMain | kafka-rest     |   
| SchemaRegistryMain | schema-registry |
 
If any of the four Java processes are not present, start the relevant service(s) by typing: `$ sudo service <service-name> start` 
 
  <a name="JavaExercises"></a>
## Java Exercises