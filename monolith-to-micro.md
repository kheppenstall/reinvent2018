### From Monolith to Modern App: Best Practices

#### The Serverless Advantage
* No provisioning, no management (no patching OS)
* Pay for value
* Automatic scaling
* Highly available and secure
* Agility, elasticity, total cost efficiencyy
* 10% on infrastructure, 90% on application
* Lambda, Fargate, Aurora Serverless
* Kinesis for monitoring
* API Gateway

#### Trends in the Enterprise
* Lambda needs to support
* Stateful (containers) or stateless (serverless)
* Response time and memory - limitations on lambda

#### Real Time Scenario
* Capabilities of a Modern Application: Secure, Resilient, Elastic, Modular, Automated, Interoperable
* Small, cross-functional teams focused on a specific service
* Setup of cloud-based develpment environment
* Continuous integration and testing environments
* Service ownership culture
* Centralized monitoring and management
* Automation is not a phase
* Agility is a fundamental goal
* Route 53
* Amazon Cloudfront -> Amazon S3
* Amazon Cognito - anonymous ID with permission to call API
* API Gateway -> AWS Lambda (votes) -> Dynamo Db -> AWS Lambda (aggregation) -> Dynamo Db

#### Modern Application Checklist
* Security and compliance across lifecycle
* Structure apps as collections of microservices
* Build with serverless technologies as much as possible
* Use code to model applications and infrastructure

#### Takeaways
* Wild rides workshop