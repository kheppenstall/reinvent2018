### Best Practices for Running SQL Server in RDS

#### Introduction
* Managed relational database service
* Easy to administer
* Performant and scalable
* Available and durable
* RDS Manages
    * Provisioning
    * Installation and patching
    * Automated backups
    * Restors - snapshots and point-in-time
    * High availability
    * Monitoring

#### Availability
* Concepts
    * Regions and AZs
    * Single-AZ
    * Multi-AZ
        * Failover -> Address Apply Debt -> Promote to Primary-> Change DNS endpoint -> Provision new secondary (1 minute downtime)
* Best practices
    * Set 'recover interval' in parameter group
    * Alter database set target_recovery_time
    * Indirect checkpoints vs. automatic checkpoints
* Configure apps to have retry logic on connection failure
* Set client DNS TTL to <30 seconds
* Use always on AG listener for quick failover

#### Security
* Use IAM accounts to control Amazon RDS API actions
* Restrict accessibility
* Avoid enabling public access
* Avoid using port 1433
* Audit access (compression by default)
* Enable storage encryption - AWS Key Management Services (KMS)
* Encrypt data in transit by setting `rds.force_ssl`

#### Data Migration
* Native backup / restore
* AWS database migration service
* Import / export and bulk copy
* AWS marketplace

#### AllState's Journey

#### Key Takeaways
* Encryption at rest and in transit