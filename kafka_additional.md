[Use cases](https://kafka.apache.org/uses):
* Messaging
* Website Activity Tracking
* Metrics
* Log Aggregation
* Stream Processing
* Event Sourcing
* Commit Log

[Schema registry](https://docs.confluent.io/platform/current/schema-registry/index.html):
* Server process external to Kafka brokers
* Maintains a database of schemas
* HA deployment option available
* Consumer/Producer API component
* Defines schema compatibility rules per topic
* Producer API prevents incompatible messages from being produced
* Consumer API prevents incompatible messages from being consumed
* Supported formats:
    * JSON Schema
    * Avro
    * Protocol Buffers

Quiz:
1. Main APIs of Kafka
    * Consumer API
    * Producer API
    * Connector API
    * Streams API
2. For every Kafka partition, there is one server that acts as the Leader, and none or more servers play Followers' role.
3. Retention duration is based on the message consumption strategy
4. Kafka deploys to containers, VMs, bare metal, cloud
5. Kafka Streams are highly scalable and fault-tolerant
6. It is not possible to use Kafka without ZooKeeper
7. Message size depends on the use-case but should be as small as possible.
8. Performance tuning:
    * Tuning Kafka Consumers
    * Tuning Kafka Producers
9. Kafka has no complete set of monitoring tools.
10. ISR stands for in-sync replicas
11. The Follower is not able to process data as fast as a leader => replica is staying out of ISR for a long time
