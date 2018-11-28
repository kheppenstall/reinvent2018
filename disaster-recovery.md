### Disaster Recover with AWS

#### Introduction
* CloudRange - disaster recovery

#### Need for disaster recovery
* User errors
* Malicious and insider threats
* Opertional mishaps (bugs)
* Site outages

#### DR strategies - Differences between on-premise and cloud
* On-premise
    * High upfront cost
    * Data growth results in higher hardware and operational costs
    * Difficult to test
* In cloud
    * Scales easily
    * Easier to test - find new solutions (like cloning into staging)

#### Zebra's data protection challenges and business needs
* Challenges
    * Meeting business continuity SLAs
    * Risk to daa loss - manual and scripts
    * Compliance and risk management
* Why Druva CloudManager
    * Cloud-native and offered as a services
    * Single dashboard for all AWS resources, regions, and accounts
    * Remove depenencies on scripts and manual back-ups (new instances automatically included)
    * Replicated 3-tiered architecture
    * Customer-first model with excellent support
    * Ability to clone VPC environments
* Results
    * Automate DR testing ensuring business SLA compliance
    * DR plans automatically updated based on demands
    * Cloned production environment to test fixes
    * Policy-based approach for snapshot management
    * Set retention across all regions and accounts

#### Why does DR fail?
* Lack of testing
* Resource issues, configuration, and network
* Outdated plans, changes not factored

#### The Druva CloudRanger solution
* AWS native solution built for AWS environments
* Zero infrastructure setup for DR
* One-click automated DR
* DR plans based on business SLAs
* Identify, clone, or edit DR environment

#### Architecture
* Route 53 -> Internet > Lambda (API Gateway, S3, Elasticache)  -> ...

#### Druva CloudRange DR Steps for AWS
1. Identify environments
2. Create DR plans
3. Schedule automatica tests for DR plans
4. Generate reports
