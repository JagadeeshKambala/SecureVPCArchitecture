Design Decisions and Architectural Rationale

1. Purpose of This Document
   This document explains the reasoning behind every major architectural decision in this project. The intent is to demonstrate deliberate design choices rather than default or convenience-based configurations.
2. VPC and IP Addressing Strategy
   Decision
   A single custom VPC with CIDR block 10.0.0.0/16 was created.
   Rationale
   A /16 CIDR block provides sufficient address space for:
   Multiple subnet tiers
   Future expansion
   Additional services such as load balancers or managed databases
   This CIDR size aligns with common enterprise standards and avoids early IP exhaustion.
3. Multi–Availability Zone Design
   Decision
   All subnet tiers were deployed across two Availability Zones.
   Rationale
   Improves fault tolerance
   Reduces blast radius of AZ failures
   Aligns with AWS Well-Architected reliability best practices
   Even though this project uses a limited number of EC2 instances, the network design itself is production-ready.
4. Subnet Tiering Strategy
   Decision
   Three subnet tiers were implemented:
   Public
   Private
   Isolated
   Rationale
   Subnet tiering enforces clear trust boundaries:
   Public subnets host internet-facing components
   Private subnets host internal application logic
   Isolated subnets host sensitive data workloads
   This prevents accidental exposure and simplifies security reviews.
5. Routing Design
   Decision
   Separate route tables were created and associated with each subnet tier.
   Routing Logic
   Public subnets route 0.0.0.0/0 to the Internet Gateway
   Private subnets route 0.0.0.0/0 to the NAT Gateway
   Isolated subnets have no internet route
   Rationale
   Explicit routing ensures:
   No hidden internet access
   Predictable traffic behavior
   Easier troubleshooting
6. Compute Placement Decisions
   EC2 instances were deployed in each tier to validate:
   Routing behavior
   Security group enforcement
   Network ACL behavior
   In production environments, these instances would typically be replaced with managed services, but EC2 provides the clearest validation surface for learning and demonstration.
