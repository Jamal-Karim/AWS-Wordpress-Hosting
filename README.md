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

## Project Setup
### 1. Set up the VPC
  - Go to the AWS console and create a VPC
  - Use all default settings for "VPC only" but add a name tag (mine is MyVPC) and change the IPV4 CIDR to 10.0.0.0/16
  - After it is created, select it, go to "Actions", click "Edit VPC settings" and make sure both DNS settings are enabled
### 2. Set up an Internet Gateway
  - Go to the Internet gateway section and create an Internet gateway
  - Add a name tag (mine is myInternetGateway)
  - After it is created, select it, go to the "Actions" dropdown select "Attach to VPC" and attach it to the VPC we just made
