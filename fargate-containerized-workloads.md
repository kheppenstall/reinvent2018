### Fargate Containerized Services

#### Introduction
* Run containers without EC2 instances
* Scale quickly up from baseline and manage own infrastructure

#### Strong operational foundation
* Multi-AZ (through subnets)
* 99.99 availability
* Container level health checks

#### Fargate Security
* AWS manages OS and docker runtime
* Takes care of infrastructure scaling
* Focus of customer effort on to application and container level configuration and networking

#### Fargate Platform
* Abstracts infrastructure

#### Security Benefits
* No direct access to infrastructure
* Can't ssh in for example (enforce best practices)
* VPC flow logs (route to cloudwatch, s3, monitoring)
* All traffice goes through an ENI in your own Amazon VPC
* A task is an isolation boundary (do not share network resources)
* Can use AWS secrets manager

#### Monitoring and Logging
* Cloudwatch to ECS

#### Task Metadata
* Query environmental data and statistics for running tasks (task-level cpu, memory...)
* Determine image pull times

#### Application tracing with AWS X-Ray
* Latency...

#### Fargate CI / CD
* Support for AWS code tools, code commit, code pipeline

#### Cost allocation
* Available for now for fargate and ECS
* Tag services, task definitions, tasks, clusters
* Tasks that belong to a service are taggerd with the service and cluster name

#### Customer Examples
* Turner Labs (enterprise-wide migration) - reduce costs, enable new features quickly - https://github.com/turnerlabs
* Cortiva Agriscience - machine learning algorithm for scoring genetic markers - run globally with low support overhead (faster turnaround and lower cost)
* Aaptiv - mobile application, APIs, microservices - monolith to microservices - cost and automation benefits

#### Shimon Tolts - CTO & Co-fount of DaTree - Building a Serverless Company
* GitOps policy engine - in accordance with best practices
* Git connects development to production
* Who is using what or where with microservices?
* Fargate checks each pull request to make sure the best practices, no secret keys, correct versions...
* No ops team - just developers
* Buy > build
* Fargate != EC2
* No AMIs to configure, monitoring & logging is built in
* All code is packaged using Docker containers - ONLY responsible for what runs without the containers
* No balancing of container and server scaling
* Each service gets DNS through route 53
* ECR docker registry
* Good example - github.com/datreeio/wsdeploy