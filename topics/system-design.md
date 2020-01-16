# System Design

## Table of Contents

* [Caching](#caching) 
* [Message Broker](#message-broker)
* [Search Engines](#search-engines)
* [Containers)](#container)
* [Web Servers)](#web-server)
* [Web Servers)](#web-server)


## [Caching](https://aws.amazon.com/caching/)
 - a cache is a high-speed data storage layer which stores a subset of data.
 - typically transient in nature (lasting only for a short time).
 - Improve Application Performance
 - Reduce Database Cost.
 - Reduce the Load on the Backend.
 - Eliminate Database Hotspots.
  
 <image src="../../images/Cachinng.png">
 
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
  

 
    
    
    
