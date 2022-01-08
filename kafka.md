Low latency - less than 10 ms
Topic - particular stream of data (like a table in a db)
Topics are split into partitions
Each partition is ordered
Each message in each partition gets an incremental id called offset
Order is guaranteed only within partition
Data is kept for a limited time (default 1 week)
Once the data is written it can’t be changed

Default number of partitions is in server settings
