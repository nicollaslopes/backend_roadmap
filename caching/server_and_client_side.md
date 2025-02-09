# Server and Client side
## Server Side

Caching can be categorized into two types: **local caching** and **distributed caching**.

* **Local caching** refers to storing data on a single machine or within a single application. It's more used when the volume of data is relatively small. For example: browser caches of application-level caches.
* **Distributed caching** involves storing data across multiple machines or nodes, often in a network. When we talk about applications that need to scale and need to ensure that data will be available, we need to use distributed caching.

### **Example**

Assuming that you have to access an e-commerce website that receives thousands of request per second and the website only store product details on the server where the website is hosted. As time passes and the number of requests increases, the user experience will not be good because of the delay in responses. For this approach, distributed caching can be used. It will ensure that product details are stored across multiple cache servers located in different regions, so that when a user accesses the website, they will be able to retrieve the product details more quickly. 

### **Cache servers and their roles**

Cache servers are the primary components in a distributed caching system. They store temporary data across multiple machines or nodes, ensuring that the data is available close to where it’s needed. Each cache server can operate independently, and in case of a server failure, the system can reroute requests to another server, ensuring high availability and fault tolerance.

- **Consistent hashing:** This method ensures that data is evenly distributed across cache servers and minimizes data movement when new servers are added or existing ones are removed.
- **Virtual nodes:** Virtual nodes are used to handle scenarios where cache servers have varying capacities. They ensure that data distribution remains balanced even if some servers have higher storage capacities than others.

### **Overview of leading solutions**

Distributed caching solutions have evolved over the years to cater to the growing demands of scalable and high-performance applications. Some of the leading solutions in the market include Redis, Memcached, Hazelcast, and Apache Ignite.

**Redis**

Redis is an open-source, in-memory data structure store that can be used as a cache, [database](https://redis.io/blog/redis-cache-vs-redis-primary-database-in-90-seconds/), and [message broker](https://redis.io/solutions/messaging/). It supports various data structures such as strings, hashes, lists, and sets. Redis is known for its high performance, scalability, and support for data replication and persistence.

**Memcached**

Memcached is a general-purpose distributed memory caching system. It is designed to speed up dynamic web applications by reducing database load. Memcached is simple yet powerful, supporting a large number of simultaneous connections and offering a straightforward key-value storage mechanism.

### Caching in PHP Web Applications

https://medium.com/@josephosoo/caching-in-php-web-applications-a-developer-guide-5d1a211541b4

## Client Side

https://www.youtube.com/watch?v=HiBDZgTNpXY


*References:*

https://redis.io/glossary/distributed-caching/