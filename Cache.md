# What is a cache?

an application stores data in the cache so that it's faster to retrieve when it is needed.
- located in RAM
- sub millisecond latency



1. Check for data in cache
2. if there's a hit, serve data
3. if there's a miss
	- fetch from permenant store (slower)
	- store data copy in cache
	- serve data


[[store vs cache]]