#web #stores #redis

# Redis: in-memory data structure store
- Open-Source
- Used Internally

Provides abstract data structues for websites such as strings/hashes/lists/etc, geospatial capabilities
Useful because it supports multiple data structures


```diff
+ super flexible, supports many different data structures
+ no schema or structures necessary like in RDBMS
+ FAST: 110,000 SETS/s and 80,000 GETS/s

```

can be considered a mix of [[MongoDB]] and [[MemCache]]

Features built-in [[replication]]


### See [[Redis - Basics]] for how to use


## Use Cases
- Database
- [[Redis - Session Caching | Session Caching]]
- Message Broker

Useful for NoSQL Key/Value Storage



## Supported Data Types

Most useful for Node: [[Redis Hashes|Hashes]]

- [[Redis Strings|Strings]]
- [[Redis Lists|Lists]]
- [[Redis Sets|Sets]]
- Sorted Sets
- Bitmaps
- Hyperlogs
- [[Redis Geospatial Indexes|Geospatial Indexes]]



## Supported Languages

Redis is actually usable with just about any language omg
![[Pasted image 20220122172149.png]]




# Security

Redis is NOT something we want exposed to the internet. Trusted Clients ONLY!
- contrast with [[Svelte Stores]]

Data Encryption is not supported, which is important.