### Aurora Deep Dive

#### Amazon RDS Introduction
* Aurora is MySQL and Maria Db compatible
* Focusing on MySQL

#### Why MySQL?
* Popular - exercised, stable, large ecosystem
* Innovative - MySQL 8.0
    * Common table expressions (WITH clause, RECURSIVE) - more performant
    * Window functions!! - OVER
    * Json improvements
    * utf8mb4
    * 5108 spatial reference systems
* Availability
    * Instant ADD COLUMN -- ALGORITHM = INSTANT
    * Unified, transactional metadata dictionary
    * Atomic, crash-safe DDL
* Performance
    * 2x - 5x perfomance versus MySQL 5.7 (.5x than MySQL 5.6)
    * Hot-spot management
    * Descending indexes
    * Invisible indexes (for toying around)
    * Improved optimizer cost model
    * Resource groups - control how resources are used
    * Improved replication
* Security and Manageability
    * Roles - named collection of privileges

#### Why RDS
* Popular
    * Largest community of MySQL in the world
* Innovative
    * Point-in-time recovery (5 minutes)
    * Automated backups, manual snapshots (no impact on performance)
    * Automated, O-RPO failover across AZ's - 
    * Elastic volumes up to 32 TB
    * Managed x-region replicas for DR
    * Snapshots across regions
    * Security and Manageability
        * IAM DB Authentication
        * Industry comnpliance
        * Automated OS and database upgrades
        * IAM DB Authentication
    * Performance insights - measures load, identifies bottlenecks, adjustable timeframe
* Open
    * Freedom to migrate - EC2, S3, Redshift, Dynamo DB

#### Tips and Tricks
* What instance should I use?
    * Burstable - T2/T3 - Dev / Test instances
    * General purpose - M2 / M3 - CPU intensive
    * Memory optimized - R2 / R3 - Query intensive (TH uses these)
* Multi-AZ vs. Read Replicas?
* Backups or Manual Snapshots? - manual doesn't delete
* Secure database?
    * Network isolation - VPC
    * Aws Identity and Access Management (IAM)
* Monitoring
    * Cloudwatch metrics - CPU, storage, swap usage, I/O, laency, throughput, replica lag
    * Cloudwatch logs - long term retention - slow queries, error logs
    * Enhanced monitoring
* Know when events happen
    * Cloudwatch events - Lambda or Amazon ECS tasks


#### Takeaways
* Upgrade to MySQL 8.0 (from 5.6) due to instant algorithm, window functions, invisible indexes, performance
* Automated, O-RPO failover across AZ's - backup in another region
* Enable Performance insights on production db?
* Move staging and alpha to T2 / T3?

