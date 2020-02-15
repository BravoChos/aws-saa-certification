# ElasticCache
**ElastiCache**: is an in-memory data store or cache in the cloud it allows you to retrieve information from fast fully managed in-memory caches instead of relying for slower disk based databases. They are two types of ElastiCache.

- Redis: is a key-value store that supports abstract data types and optional data durability.

- Memcached: is a distributed caching solution that uses using client-side hashing to distribute data evenly across one or more cache nodes. You can scale out a Memcached cluster by adding more cache nodes.

## Advanced Concepts...

Existing applications that use Memcached can use ElastiCache with almost no modification. Your applications simply need information about the host names and port numbers of the ElastiCache nodes that you have deployed. The ElastiCache Auto Discovery feature for Memcached lets your applications identify all of the nodes in a cache cluster and connect to them. This means that you don't have to maintain a list of available host names and port numbers. In this way, your applications are effectively insulated from changes to node membership in a cluster.

All new ElastiCache cache clusters are, by default, launched in an Amazon Virtual Private Cloud (Amazon VPC) environment.

**Cache parameter groups** are an easy way to manage runtime settings for supported cache engine software. Amazon ElastiCache uses parameters to control the runtime properties of your nodes and clusters. Generally, newer engine versions include additional parameters to support the newer functionality.

A **node** is the smallest building block of an ElastiCache deployment. It is a fixed-size chunk of secure, network-attached RAM. Each node runs the engine that was chosen when the cluster or replication group was created or last modified. Each node has its own Domain Name Service (DNS) name and port. Multiple types of ElastiCache nodes are supported, each with varying amounts of associated memory and computational power.

Append-only files (AOF) are not supported for cache.t1.micro and cache.t2.* nodes. For nodes of these types, the appendonly parameter value is ignored. For Multi-AZ replication groups, AOF is disabled.





