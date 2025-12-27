Security Model and Controls

1. Security Philosophy
   The security model follows least privilege and defense in depth, ensuring that no single misconfiguration leads to full system compromise.
2. Security Group Design
   Security Groups act as the primary security mechanism.
   Tier-Based Security Groups
   Public tier allows inbound HTTP/HTTPS from the internet
   Application tier allows inbound traffic only from the public tier
   Database tier allows inbound traffic only from the application tier
   Security group references are used instead of CIDR blocks to improve scalability and reduce risk.
3. Network ACL Design
   Network ACLs provide secondary protection at the subnet level.
   Public NACL allows HTTP/HTTPS and ephemeral ports
   Private NACL allows internal traffic and outbound access
   Isolated NACL allows only application-tier traffic
   NACLs help prevent accidental exposure due to security group misconfiguration.
4. IAM and Credential Security
   No static credentials stored on instances
   IAM roles used for permissions
   Root account not used for daily operations
   This reduces credential leakage risk and supports auditing.
5. Audit and Compliance
   AWS CloudTrail captures:
   API calls
   Configuration changes
   Access attempts
   This enables security reviews and forensic analysis.
