### Werner Keynote - Are you well architected?

#### Database Systems
* Transition from relational database (80s, 90s) to more modern approach
* Want database to become a true platform for innovation, hence aurora
* Built on quorums (set of nodes where read and writes overlap) and failures
* Higher quorum set means higher resilience - aurora is at 6 nodes
* MySQL does 5 writs per write - data, metadata, logs...
* If you look at a log - you can resconstruct the database - so the only thing you really need to update is the log (not the data)
* THE LOG IS THE DATABASE - aurora - innovation you can do if you have total control of your storage unit (instead of dumb disk)
* Reducing latency by avoiding quorum reads - performance of read is slowest read - use book keeping of LSN acknowledgements
* Cloud native database as a foundation for innovation - decomposition, low latency by being database and storage aware
* Purpose-built database - Dynamo DB
    * Performance at scale
    * network -> request router -> storage node leader -> replicate to other nodes (cell-based architecture principles)
    * Spread out over multiple AZs
    * Cannot have massive storage units to reduce blast failure
    * Shard processing
    * Burst capacity, adaptive capacity (clone partition when it gets hot)

#### S3
* Manage peaks of 62TB per second in a single day
* Unstructured data
* Microservices
* Culture of durability
    * Static analysis
    * Checksums and proofs
    * Durability checks - go around and audit
    * Operational safeguards
* Account for natural failure rates of drives and hosts
* Also account for loss of entire data center
* Storage replicated across 3 AZs - at least one data center building per AZ

#### Redshift
* Massive improvements in performance based on how customers use system
* 3.5x faster in last 6 months due to feedback loop
* 87% of queries do not have to wait
* 13% - redshift concurrency scaling - 99% will see no additional cost

#### Serverless
* Pay for value
* No infrastructure to provision
* Scales automatically
* Highly available and secure
* Focus on business logic and nothing else
* Event-driven serverless code execution available in all regions
* Architecture
    * Worker - secure environment for code execution
    * Firecracker keeps workers safe and separate

#### AWS Toolkits for Popular IDEs
* Provide full serverless development
* Debugging for lambda functions

#### Language Support for Lambda
* Ruby support for lambda
* Custom runtimes for lambda - build own execution environment
    *  Partner-supported PHP

#### Programming Models for Lambda - Lambda Layers
* Create layers to prevent duplicated code
* Support versioning

#### Nested Applications using Serverless Application Repository

#### Step functions service integrations

#### Web Socket Support for API Gateway
* Real-time stateful applications over the Internet
* Access to containers, EC2, serverless
* Can move from EC2 to serverless without changing APIs

#### ALB Support for Lambda
* Can move to serverless without changing code and still using load balancers

#### Key Takeaways
* Move from EC2 to serverless with our API (ALB support for Lambda, Web socket support for API Gateway) - see link here - https://medium.com/artisanhost/hosting-a-laravel-application-on-aws-lamdba-90b7133c8578
* Serverless lens of the web application framework - https://d1.awsstatic.com/whitepapers/architecture/AWS-Serverless-Applications-Lens.pdf
* Well-architected APN Partner reviews - AWS Well-Architected Tool (stay up to date on best practices)
