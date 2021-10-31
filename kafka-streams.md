2 internal topics:
* changelog - for aggregates, how they change
* partition - if the key changes, new keys

2 stream types:
* KStream - infinite log of events (insert)
* KTable - aka db table, updated view (upsert, delete on null value)

transformations:
* MapValues - KStream/KTable
* Map - KStream (changes key, triggers a repartition)
* Filter - KStream/KTable
* FilterNot - KStream/KTable
* FlatMapValues - KStream
* FlatMap - KStream
* Branch - KStream, split KStream based on predicate (predicates are evaluated in order, no match => record dropped)
* SelectKey - Kstream, assign a new key to a record, mark for repartition (best practice, isolate transfomation to know where the repartitioning happens)


2 type of writes:
* to - terminal operation
* through - write and get bach stream/table

Log compaction:
* for KTables
* should be enabled by the user
* when we require a snapshot instead of the full history
* deleted records can still be seen by consumers for a period of delete.retention.ms

KGroupedStream/KGroupedTable:
* Obtained after groupBy/groupByKey
* Count counts the number of records by grouped key
* Null keys are ignored
* Null values ignored by stream, treated as delete by table

Aggregate:
* KStream - groupedStream.aggregate(initializerFun, adder, aggregateSerde, topic)
* KTable - groupedTable.aggregate(initializerFun, adder, substractor, aggregateSerde, topic)

Peek:
* apply side operations to a KStream and get the same KStream as a result

Transform/TransformValues:
* Applies a Transformer to each record
* The Transformer leverages the low level Processor API
* Advanced, not in scope of a course

Exactly once garantee:
* data processing on each message will happen only once
* pushing the message back to Kafka will also happen effectively only once

How exactly once achieved:
* The producers are now idempotent (if the same message is sent more that one time, Kafka will make sure to only keep one copy of it)
* You can write multiple messages to different Kafka topics as part of one transaction (either all are written or none). This is a new advanced api from Kafka 0.11
* For now advanced api implemented only for Kafka Streams (in future maybe Spark, NiFi and others)

3 join types:
* KStream / KStream
* KTable / KTable
* KStream / KTable
* Can only happen when the data is co-partitioned (The same number of partitions)

GlobalKTable:
* KTable living on every instance

Links:
[udemy course repo](https://github.com/simplesteph/kafka-streams-course/tree/1.1.0)
[Crossing the Streams – Joins in Apache Kafka](https://www.confluent.io/blog/crossing-streams-joins-apache-kafka/)
[Streams testing](https://kafka.apache.org/11/documentation/streams/developer-guide/testing.html)
