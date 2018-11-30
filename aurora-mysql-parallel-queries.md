### Aurora MySql Parallel Queries (PQ) - Accelerating Analytic Queries

#### Aurora Overview
* Scale-out, distributed architecture
* Head nodes and storage nodes (logging is pushed there)
* 6 copies of data, 2 in each AZ
* Serverless - scales up and down with workload
* Instant redo recovery
* In memory = cached in page view
* LRA - out of memory scan
* Batch scan - in memory scan
* AKP
* Hash joins

#### Parallel Query
* Fully managed
* Scales with storage
* No special hardware required
* No pre-provisioning required
* No setup and tuning required

#### Deep Dive
* Aurora storage has thousands of CPUs (hundreds of storage nodes)
* Optimizer helps pick which queries are best optimized with PQ
* Database node processing
    * Query optimizer produces PQ plan and creates PQ context
    * PQ request is sent to storage node along with PQ context
* Can run 16 PQ processes at a time per storage node

#### What do we get?
* Performance - 120x lower latencies
* High concurrency
* Cost effective - no extra cost
* Quiet tenant - reduced chance of evicting frequently used pages from the buffer pool that are used by OLTP workload
* Ecosystem - get aurora goodies like PiTR, continuous backup, fast cloning with PQ

#### Performance
* Peak speed-up of 187x less latency

#### Global databases
* Master in one region and replicas in other regions
* Increased data locality and disaster recovery
* Low replica lag < 1 sec cross-country lag (across US east and US west)
* Fast recover < 1 min to accept full read-write workloads after region failure

#### Key Takeaways
* OLDP vs. OLAP
* Restore existing 5.6 clusters to use parallel queries
    * `show global status like '%Aurora_pq_requests`
    * `select @@aurora_pg_supported`
    * `set session aurora_pq = { 'ON' / 'OFF' }`
    * use `explain` to determine if pq is going to be used
    * `aurora_pq_request_attempted`, `aurora_pq_request_executed`... variables
* This is my architecture video series - https://aws.amazon.com/this-is-my-architecture/