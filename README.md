# AWS-Wordpress-Hosting

In this project, we are deploying a Wordpress website on AWS. We use some core AWS technologies and design an architecture to display how these tools work with each other.

## AWS Technologies
<details>
  <summary>Click to expand</summary>

##
  
  - VPC 
  - EC2 
  - RDS Database
  - Internet Gateway
  - Amazon Route 53
  - NAT Gateway
  - Application Load Balancer
  - Auto Scaling Group
  - S3 Bucket
  - IAM

</details>

## Architecture Diagram

![Architecture](./Architecture_Diagram.png)

### Explanation of Diagram
- We use 2 availability zones for high availability and fault tolerance
- EC2 instances are protected in the private subnets and can be accessed via the NAT gateways for protected internet connection
- User requests and responses follow the internet gateway, to the ALB, to the instances, and the master DB and back.
- We have 1 master DB and 1 standby DB, the master DB handles all main operations while the standby is synchronized.
