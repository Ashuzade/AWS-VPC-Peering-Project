**AWS VPC Peering Project**

**Project Overview**

This project demonstrates secure communication between two Amazon Virtual Private Clouds (VPCs) using VPC Peering in the AWS Mumbai Region ("ap-south-1").

**Objectives**

- Create two separate VPCs with non-overlapping CIDR blocks.
- Configure public and private subnets.
- Launch a Bastion Host and two private EC2 instances.
- Configure route tables and security groups.
- Establish VPC Peering between the two VPCs.
- Verify connectivity using ICMP ping and SSH.
- Perform a controlled failure test and restore connectivity.

**AWS Services Used**

- Amazon VPC
- Amazon EC2
- VPC Peering
- Route Tables
- Internet Gateway
- Security Groups
- Amazon Linux

**Network Configuration**

Resource| CIDR / Private IP
VPC A| "10.10.0.0/16"
VPC A Public Subnet| "10.10.1.0/24"
VPC A Private Subnet| "10.10.2.0/24"
VPC B| "10.20.0.0/16"
VPC B Private Subnet| "10.20.1.0/24"
Bastion Host| "10.10.1.202"
PrivateEC2-A| "10.10.2.243"
PrivateEC2-B| "10.20.1.10"

**Implementation**

1. Created VPC A and VPC B in the AWS Mumbai Region.
2. Configured subnets, route tables, and an Internet Gateway for public access to the Bastion Host.
3. Launched a Bastion Host and two private EC2 instances.
4. Configured security groups to restrict SSH and ICMP traffic.
5. Created and accepted the VPC Peering connection.
6. Added routes between the VPC CIDR blocks.
7. Tested connectivity between PrivateEC2-A and PrivateEC2-B.
8. Removed an ICMP rule temporarily to test failure, then restored the rule and verified connectivity again.

**Testing Results**

- PrivateEC2-A to PrivateEC2-B ping: Successful, 0% packet loss.
- PrivateEC2-B to PrivateEC2-A ping: Successful, 0% packet loss.
- Controlled ICMP failure test: Completed.
- Connectivity recovery after restoring the ICMP rule: Completed.

**Security Considerations**

- Private application instances do not require public IPv4 addresses.
- SSH access is restricted to the Bastion Host and authorized administrator IP.
- ICMP rules are limited to the relevant private instance IP addresses.
- Private SSH key files and AWS credentials must never be committed to GitHub.

Screenshots

See the "screenshots/" directory for configuration and connectivity evidence.

Conclusion

This project demonstrates how VPC Peering enables private network communication between two VPCs through appropriate routing and security group configuration.
