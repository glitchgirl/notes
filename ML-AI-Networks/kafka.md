# Apache Kafka

- Topic : is a stream of data
- Topics are split into partitions which are

    - ordered
    - have an offset id
    - their data can't be overwritten
    - data is randomly assigned to a partition
    - should only have one leader
    - Leaders only can receive and server data
    - Message keys - same partition guarantee order

- Brokers
    - Servers, ID(the topic partition)
    - Connect to one, connected to all
    - Data is distributed
    - Topics should be duplicated, this is called a replication factor
    - ISR in sync replica (how the other partitions get data)

- Producers
    - the thing that writes data to the topic
    - Acks = 0 - no wait time, but possible data loss
    - Acks = 1 - leader acknowledges, less data loss a little slower
    - Acks = all - all replicas acknowledge, no data loss, but slower

- Consumers
    - read data from a topic
    - groups - exclusive partitions
    - Can't have more consumers then partitions
    