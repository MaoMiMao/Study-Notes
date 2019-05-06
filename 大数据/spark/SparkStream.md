### Spark Streaming & Structured Streaming 

#### Spark Streaming

##### kafka 

- Receiver-based Approach (基于kafka高级API)

``` java
   JavaPairReceiverInputDStream<String, String> kafkaStream =
       KafkaUtils.createStream(streamingContext,
       [ZK quorum], [consumer group id], [per-topic number of Kafka partitions to consume]);
```

- Direct Approach ( kafka 低级API)

``` java
 JavaPairInputDStream<String, String> directKafkaStream =
     KafkaUtils.createDirectStream(streamingContext,
         [key class], [value class], [key decoder class], [value decoder class],
         [map of Kafka parameters], [set of topics to consume]);
```

