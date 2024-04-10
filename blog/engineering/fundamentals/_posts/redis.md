* Replication for fault-tolerance and load balancing/scaling
  * Does redis have the concept of "read" replicas for read path scaling?
    * Yes
    > Replication can be used both for scalability, to have multiple replicas for read-only queries (for example, slow O(N) 
    > operations can be offloaded to replicas), or simply for improving data safety and high availability.     

    Ref: https://redis.io/docs/management/replication/

* How does partitioning work?
  * Redis uses a concept called hash slots to partition keys across shards in a redis cluster
  Ref: https://redis.io/docs/management/scaling/

* While max key size supported is 512MB, using keys that are over 1MB in size is typically a bad idea    
Ref: https://redis.io/docs/manual/keyspace/
  
# Resources
* https://redis.com/redis-enterprise/technology/linear-scaling-redis-enterprise/
* https://aws.amazon.com/elasticache/redis-features