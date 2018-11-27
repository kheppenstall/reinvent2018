### Airbnb's Journey from Self-Managed Redis to ElastiCache for Redis

#### About Airbnb

#### Redis at Airbnb
* Redis Use Cases
    * Authentication
    * Verification and fraud detection
    * Payments (booking and host)
    * Feeds
* Previous solutions
    * High operational overhead
    * No support for sharding
    * No support with encryption

#### Why Elasticache
* Key-value store
* Fully managed and hardened (snapshots)
* Secure and compliant (encrption at rest/transit)
* Highly available and reliable - read replicas, multiple primaries, multi-AZ with automatic failover
* Easily scalable - up to 6.1 TB
* Can enforce using a password

#### Migration Requirements
* Zero downtime
* No data loss
* No cold starts (dual-writes)

#### Procedure
* Stage the application
* Deploy ElastiCache Redis Cluster
* Sync data (slaveof restricted command)
* Failover (disable alerts, block traffic, allow sync to finish) - perform switch
* Cleanup
