Traffic Flow and Access Patterns

1. Inbound Traffic Flow
   User traffic enters the environment through the Internet Gateway and is directed only to the public subnet tier. Only required ports are open.
2. Internal Application Flow
   Public-facing workloads forward requests to application workloads in private subnets. Application workloads communicate with database workloads in isolated subnets.
3. Outbound Traffic Flow
   Private workloads access the internet via the NAT Gateway for updates and external integrations. Isolated workloads have no outbound internet access.
4. Blocked Traffic Paths
   Direct access from the internet to private or isolated subnets is blocked. Database workloads cannot initiate internet connections.
   These restrictions are enforced by routing, security groups, and NACLs.
