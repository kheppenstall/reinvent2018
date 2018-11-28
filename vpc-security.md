### VPC (Virtual Private Cloud) - Security at the Speed of Light

#### What is VPC
* Virtual private cloud
* Abstraction (software-defined)
* Virtual data center
* Get a box you can launch things into
    * EC2 instances, containers, relational databases, load balancer, elasticache instances
* Built-in DHCP (provide ip address) and DNS service, including private DNS
* Two built-in firewalls: Network ACLs and Security groups 
* Packet size up to 9000 bytes
* Always free
* Useful for dev, beta, pre-prod, test, and repro networks
* Multi-vpc architectures
* Immutable infrastructure patterns
* Can do in minutes what would take weeks

#### What role modern and secure APIs plays
* Only way to launch an instance inside a VPC is to call a secure web service API
* No plugging in - creates a trace of who did what and when
* CloudTrail, CloudWatch, Config, CloudFormation
* Easy to audit

#### How traffic gets to/from VPCs securely and quickly
* Direct connect gateway
* VPN
* Full support for IPv6
* Hide hundreds of instances / containers behind a few IPs
* Traffic comes into VPC through global AWS backbone
* Direct connect or through internet (public api, vpn)
* Built in to backbone edge networks - DDOS mitigation structure and AWS Shield
* Global accelerator - high-availability and performance across regions
    * Gets traffic to global backbone much faster
    * Traversing a network where traffic can be spooked or intercepted
* AWS Transit Gateway - build your own flexible border network
    * Connect multiple VPCs
    * Build DMZs

#### How packet-level security works
* VPC on the wire
* Physical server running the virtualization
* Embedded router physically attached to the physical box (annapurna labs)
    * Translation from virtual network to something that can go on the wire and be routeable
    * VPC encapsulation
    * Novice protocol
    * Then IP on the physical network
* Take encapsulation off when moving outside the VPC (blackfood edge device)
* Encapsulation
    * Outer-most IP destination identifies the target physical host
    * Encapsulation marks each packet with the VPC and the Elastic Network Interface
    * How does the sender know? The mapping service...
        * Nano to micro seconds to determine destinations
        * Mapping is proactively cached and invalidated
        * Validates the origin is correct as well for security
    * Encapsulation and separate protocols add security so it can't be spoofed

#### How VPC connection-level security works
* Security groups include stateful connection tracking
* Flow logs give per-flow aggregrated audit data
* Network load balancer can load balance flows natively and transparently in the VPC network
* NAT gateway brings per-flow stateful NAT to VPC (for outbound traffic)
* Also happens on embedded routers
* TCP and UDP stateful tracking
* Hyperplane and shuffle sharding shelters customers from each other in DDOS attack


#### Key Takeaways
* Should we use AWS Global Accelerator?
