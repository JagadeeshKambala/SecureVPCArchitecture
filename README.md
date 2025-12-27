#Secure Multi-AZ AWS VPC Architecture for Internet-Facing and Internal Workloads

##1. Project Overview
   This project demonstrates the design and implementation of a secure, production-grade AWS Virtual Private Cloud (VPC) architecture intended for real-world enterprise workloads. The solution focuses on network isolation, least-privilege security, controlled traffic flow, and operational visibility, which form the foundation of nearly all production AWS environments.
   Rather than deploying a simple flat network, this architecture deliberately separates workloads into public, private, and isolated tiers across multiple Availability Zones. This approach mirrors how organizations design secure cloud environments to protect internal systems while safely exposing only required services to the internet.
   The project emphasizes hands-on implementation, validation, and documentation. Every component exists for a reason and is explained in detail to demonstrate not only how the architecture was built, but why each decision was made.

##2. Architecture Goals
   The primary goals of this project are:
   Design a secure AWS network aligned with the AWS Well-Architected Framework
   Enforce strict separation between internet-facing and internal workloads
   Prevent accidental public exposure of sensitive systems
   Enable controlled outbound access for private workloads
   Provide centralized logging, monitoring, and auditability
   Create documentation suitable for technical reviews and interviews
   This project intentionally avoids shortcuts and defaults in favor of explicit configuration and validation.

##3. High-Level Architecture Description
   At a high level, the architecture consists of:
   A custom VPC spanning two Availability Zones
   Public subnets for internet-facing workloads
   Private subnets for application workloads
   Isolated subnets for database workloads
   Internet Gateway for controlled inbound and outbound internet access
   NAT Gateway for private subnet outbound connectivity
   Dedicated route tables per subnet tier
   Security Groups and Network ACLs implementing layered security
   Centralized logging and monitoring using CloudTrail, VPC Flow Logs, and CloudWatch
   Each tier is designed to have a clear responsibility and trust boundary, ensuring that compromise in one tier does not automatically expose others.

##4. Key AWS Services Used
   Amazon VPC – Network isolation and traffic control
   Subnets & Route Tables – Tier separation and routing enforcement
   Internet Gateway – Controlled internet access for public workloads
   NAT Gateway – Secure outbound internet access for private workloads
   Amazon EC2 – Compute resources for validation and demonstration
   Security Groups – Stateful instance-level firewall
   Network ACLs – Stateless subnet-level protection
   AWS CloudTrail – API-level auditing and compliance
   VPC Flow Logs – Network traffic visibility
   Amazon CloudWatch – Metrics, alarms, and operational monitoring

##5. Security Principles Applied
   This architecture follows several core security principles:
   Least Privilege – Only required traffic is allowed at every layer
   Defense in Depth – Security Groups and NACLs are used together
   Explicit Routing – No implicit internet access
   Isolation by Design – Database tier has zero internet connectivity
   Auditability – All actions and network flows are logged
   These principles reflect how secure systems are designed and reviewed in production environments.

##6. Validation and Evidence
   All components of this architecture were validated through direct testing. Traffic flow, access restrictions, and logging behavior were verified and documented. Screenshots and validation results are included in this repository to provide verifiable proof of implementation.
