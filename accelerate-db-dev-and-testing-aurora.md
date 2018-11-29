### Accelerate Database Develpment and Testing with Amazon Aurora

#### Database Development and Testing Perspective
* DB architecture
* Deployment and automation
* Improve dev/test outcomes
* Performance and availability
* Cost effective deployment

#### Amazon Aurora
* Cloud native database
* Service oriented architecture leveraging AWS services
* Fully managed services, automating administrative tasks (patching, high availability, back-ups)
* Cloud-native capabilities simplify use
* 5x more throughput than MySQL, 3x more throughput than PostgreSQL
* Key characteristics
    * Log-structured storage volume shared between all clusters
    * Readers strictly read-only
    * Optimized for high throughput
        * Higher concurrency
        * Less traffic between reader and writer nodes - so nodes can do more
* Core use case 1
    * Auto scaling optional
    * All readers treaeted the same
    * Any reader can be failover target
    * Application snould use cluster and reader endpoints
    * Dev Tip: Monitor cluster topology for faster failover
* Core use case 2
    * Each reader has a specific purpose
    * Ordered failover targeting
    * Application uses cluster, custom, or even DB instance endpoints
    * Caveat - readers share the same storage and undo log (slow queries on read can impact master)
* Deployment automation
    * Reduce risk of human errors
    * Repeatable deployments
    * Accountability and management of change
    * How?
        * Procedural automation - about outcome, not journey
            * AWS CloudFormation
            * Terraform
        * Declarative - about journey, less about outcome
            * AWS CLI
            * AWS SDKs
* Deployment automation using AWS CloudFormation
    * Check gaps between CloudFormation and APIs (console, CLI, SDKs)
    * Check feasability of workarounds for gaps
    * Ensure efficient ordering during resource provisioning (dependencies + custom resources)
    * Create alternative automation for minimal downtime production workflows

#### Improve Development and Testing Outcomes
* Bad practices
    * App development and testing on tiny subsets of non-production data
    * Bulk exports from live production instances
    * Running long, unoptimized queries on cluster readers
    * Lack of outcome focus
* Right way
    * Know your features, point-in-time restore, database cloning, backtrack
    * Proper workload isolation
    * Test, don't hope for the best

#### Database Cloning
* Test changes in pre-production on relevant data sets
* Reorganize a database with minimal production impact
* Save a point in time snapshot for data analysis without impacting production systems

#### Backtracking
* Periodic snapshots every 5 minutes
* Apply log streams

#### Development focused on production scale
* Bad practices
    * App dev and testing on small subset of prod data
    * Database never fails attitude
    * Running long, unoptimized queries on cluster readers
    * Lack of outcome focus
* Right way
    * Be aware of architectural differences between aurora and other engines
    * Know capabilities and operational procedures - automated failovers, upgrades...
    * Extend aurora features with application side cluster awareness
    * Test, don't hope for the best: failure injection
* Connection management and availability
    * Common MySql and PostgreSQL drivers are not cluster / topology aware
    * Use a client side connection pool - recycle connections periodically; avoid connection storms
    * Use a smart driver or build topology awareness in your client data layer - validate connections
    * Understand the behavior of Aurora DNS endpoints - manage DNS caching
* Monitor query performance
    * Analyze throughput and latency
    * Establish a baseline of acceptable / desired query performance
    * Assess performance impact of workload changes
    * Troubleshoot poor performance, identify bottlenecks
    * Cloudwatch Metrics, Cloudwatch Logs, Enhanced Monitoring, Performance Insights
* Performance Insights
* Aurora serverless (now with http API)

#### Key Takeaways for TH
* Automate alpha, staging clone process with CloudFormation?
    * Clone in CloudFormation
    * Then SQL through a CloudFormation custom resource Lambda function
* Aurora serverless for testing database?
* Enable enhanced monitoring and performance insights
* Does snowflake queries on reader impact the primary instance?
* Key metrics are throughput and latency