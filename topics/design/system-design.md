# System Design

## Table of Contents

* [Caching](#caching) 
* [Message Broker](#message-broker)
* [Search Engines](#search-engines)
* [Containers](#container)
* [Web Servers](#web-server)
* [Web Servers](#web-server)


## [Caching](https://aws.amazon.com/caching/)
 - a cache is a high-speed data storage layer which stores a subset of data.
 - typically transient in nature (lasting only for a short time).
 - Improve Application Performance
 - Reduce Database Cost.
 - Reduce the Load on the Backend.
 - Eliminate Database Hotspots.
  
 <image src="../../images/caching-types.png">
 
 [**Redis**](https://aws.amazon.com/redis/) 
   - Stands for Remote Dictionary Server
   - Fast, open source in-memory data store for use as a database, cache, message broker, and queue
   - Data resides in-memory, in contrast to databases that store data on disk or SSDs.
   - Flexible data structures such as Strings , Lists , Sets , Sorted Sets, Hashes , Bitmaps etc 
   - Replication and persistence with RDB(snapshots) and AOF(Append Only File) point-in-time backups (copying the Redis data set to disk).
 
 **Redis Vs Memcached**
   - Memcached preferable when caching relatively small and static data, such as HTML code fragments.
   - Memcached is multithreaded, you can easily scale up.
   - [Memcached is its only the tip of the redis iceberg](https://aws.amazon.com/elasticache/redis-vs-memcached/)
  
 [**An introduction to Spring Data Redis**](https://www.baeldung.com/spring-data-redis-tutorial)
  - Abstractions of the Spring Data platform to Redis – the popular in-memory data structure store.
  - Declaring the Spring Data Redis dependencies **spring-data-redis and jedis** in the pom.xml.
  - To define the **connection settings between the application client and the Redis server instance**, we need to use a Redis client.
  - *Jedis* – a simple and powerful Redis client implementation.
  - Define **RedisTemplate using the jedisConnectionFactory**. This can be used for querying data with a custom repository.
  - Create Redis repository by extending CRUDRepository and Entity with @RedisHash and @id Annotation.
  - RedisTemplate provides operational views like **HashOperations, ListOperations, SetOperations** etc.
  - Redis Messaging (Pub/Sub), Redis Streams and Reactive Redis support.
 **Performance Tuning for Redis**
  - https://medium.com/@abhishekbhardwaj510/redis-best-practices-and-performance-tuning-c48611388bbc
  - https://www.objectrocket.com/blog/how-to/10-quick-tips-about-redis/
  
  

 ## Messaging System
  - Provide communication and coordination for these distributed applications.
  - Significantly simplify coding of decoupled applications, while improving performance, reliability and scalability. 
  - Asynchronous service-to-service communication used in serverless and microservices architectures.
  
   **Kafka As Messaging System**
   - Distributed, partitioned, replicated commit log service. It provides the functionality of a messaging system, but with a unique design.
   - Distributed **publish-subscribe messaging** system.
   - Kafka scales nicely up to **100,000 msg/sec even on a single server**.
   - To a topic, messages published are distributed into partitions.
   - In partition, messages are represented as a log stream.
   - The consumer is responsible for moving through this stream.
   - Messages from each partition are processed in-order only.
   - Employs a dumb broker and uses smart consumers to read its buffer.
   - Retains all messages for a **set amount of time**, and consumers are responsible to track their location in each log.
   - Use cases like Website Activity Tracking, Metrics, Log Aggregation, Stream Processing, Event Sourcing and Commit logs.
   - Durable message store and clients can get a **replay** of the event stream on demand.
   - **Zookeeper** is a configuration service / naming registry for distributed systems.Managing and coordinating Kafka broker. 
   
   **Apache Kafka with Spring**
   - Spring Kafka brings the simple and typical Spring template programming model with a KafkaTemplate and Message-driven POJOs via @KafkaListener annotation.
   - Add the **spring-kafka** dependency to our pom.xml
   - Configure a ProducerFactory which sets the strategy for creating Kafka Producer instances. 
   - Setting BOOTSTRAP_SERVERS_CONFIG, KEY_SERIALIZER_CLASS_CONFIG, VALUE_SERIALIZER_CLASS_CONFIG or JsonSerializer
   - **KafkaTemplate** which wraps a Producer instance and provides convenience methods for sending messages to Kafka topics.
   - Send messages using the KafkaTemplate class **kafkaTemplate.send(topicName, msg);**
   - Configure a **ConsumerFactory** and a **KafkaListenerContainerFactory**. 
   - POJO based consumers can be configured using **@KafkaListener annotation**.
   - **@EnableKafka** annotation is required on the configuration class to enable detection of @KafkaListener annotation on spring managed beans. It is only required for Consumer not producers.
   - Kafka Consumer API is not thread safe. **ConcurrentKafkaListenerContainerFactory** api provides concurrent way of using Kafka Consumer API along with setting other kafka consumer properties.
   - @KafkaListener(topics = "topicName", groupId = "foo")
   - Multiple listeners can be implemented for a topic, each with a different group Id. 
 
    
    
    
