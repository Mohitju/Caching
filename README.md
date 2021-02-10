# Different Caching Approaches

## 1. Cache-Aside 

## 2. Read-Through Cache

## 3. Write-Through Cache

## 4. Write-Around

## 5. Write-Back

***

## **1. Cache-Aside**

Cache-Aside is the most commonly used caching approach. The cache sits on the side and the application directly talks to both the cache and the database.


![Cache-Aside](https://codeahoy.com/img/cache-aside.png)

Here’s what’s happening:

1. The application first checks the cache.

2. If the data is found in cache, we’ve cache hit. The data is read and returned to the client.

3. If the data is not found in cache, we’ve cache miss. The application has to do some extra work. 

Pros:

Cache-aside caches are usually general purpose and work best for read-heavy workloads. If the cache cluster goes down, the system can still operate by going directly to the database. 

Cons:

When cache-aside is used, the most common write strategy is to write data to the database directly. When this happens, cache may become inconsistent with the database. 

***

## ***2. Read-Through Cache***

Read-through cache sits in-line with the database. When there is a cache miss, it loads missing data from database, populates the cache and returns it to the application.

![Read_Through](https://codeahoy.com/img/read-through.png)

Pros:

Read-through caches work best for read-heavy workloads when the same data is requested many times.

Cons:

The disadvantage is that when the data is requested the first time, it always results in cache miss and incurs the extra penalty of loading data to the cache. 

***

## ***3. Write-Through Cache***

In this write strategy, data is first written to the cache and then to the database. The cache sits in-line with the database and writes always go through the cache to the main database.

![Write-Through](https://codeahoy.com/img/write-through.png)

Pros:

when it is paired with read-through caches, we get all the benefits of read-through and we also get data consistency guarantee, freeing us from using cache invalidation techniques.

Cons:

On its own, write-through caches don’t seem to do much

***
## ***4. Write-Around***

Here, data is written directly to the database and only the data that is read makes it way into the cache.

Pros:

Write-around can be combine with read-through and provides good performance in situations where data is written once and read less frequently or never.

***

## **5. Write-Back**

Here, data is written directly to the database and only the data that is read makes it way into the cache.

![Write_Back](https://codeahoy.com/img/write-back.png)

This is sometimes called write-behind as well.

Pros:

Write back caches improve the write performance and are good for write-heavy workloads. When combined with read-through, it works good for mixed workloads, where the most recently updated and accessed data is always available in cache.

Cons:

The main disadvantage is that if there’s a cache failure, the data may be permanently lost.

***

[Reference Links](https://codeahoy.com/2017/08/11/caching-strategies-and-how-to-choose-the-right-one/)
