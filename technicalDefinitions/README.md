##  Target Group in AWS

>A Target Group in AWS is a logical group of resources (targets) that a Load Balancer sends traffic to.

Think of it as the backend pool behind your Load Balancer.

Example:

              Users
                |
                ↓
      Application Load Balancer
                |
                ↓
          Target Group
                |
       -------------------
       |        |        |
      EC2-1   EC2-2    EC2-3

The Load Balancer does not send traffic directly to individual EC2 instances. It sends traffic to a Target Group, and the Target Group contains the instances that should receive the traffic.

##  Launch Template in AWS

>A Launch Template is an AWS resource that contains the configuration parameters required to launch and configure EC2 instances. It provides a reusable and versioned definition of an EC2 instance configuration, including the AMI, instance type, network settings, security groups, storage configuration, IAM role, key pair, and user data scripts.

It allows AWS services (especially EC2 Auto Scaling Groups) to automatically create EC2 instances with a consistent and predefined configuration.

> #### Most common use case: EC2 Auto Scaling Group

The most common use of a Launch Template is with an Auto Scaling Group (ASG) to automatically launch, replace, and scale EC2 instances.

Architecture:

                    Users
                      |
                      ↓
            Application Load Balancer
                      |
                      ↓
               Target Group
                      |
                      ↓
            Auto Scaling Group
                      |
                      ↓
             Launch Template
                      |
        --------------------------------
        |              |               |
      EC2-1          EC2-2           EC2-
      
##  Key Pair in AWS
A key pair in AWS is a set of cryptographic keys used to securely authenticate access to an EC2 instance.

It consists of two parts:

>Key Pair
>
>     Private Key  🔑  (kept by you) 
>                   | 
>                   |
>                   ↓
>     Public Key  🔓  (stored by AWS on the EC2 instance)

AWS uses asymmetric encryption (public key cryptography).

## Scaling Policy

>A Scaling Policy is a configuration attached to an Auto Scaling Group that automatically adds (scale out) or removes (scale in) EC2 instances based on metrics, schedules, or specific conditions.
## AWS CloudTrail 

>AWS CloudTrail is a governance, compliance, and auditing service that records AWS API activity, including who performed an action, when it happened, from where, and what resources were affected.

##### In simple words:

>CloudTrail is like a security camera for your AWS account. It keeps a history of everything that happens.

## AWS Certificate Manager (ACM)
>AWS Certificate Manager (ACM) is a managed AWS service that provisions, stores, manages, and renews public and private SSL/TLS certificates used to secure network communications and establish encrypted HTTPS/TLS connections for AWS resources and applications.

## Amazon Route 53

>Amazon Route 53 is a managed, highly available and scalable Domain Name System (DNS) web service provided by AWS. It translates domain names into IP addresses or AWS resource endpoints and can also perform DNS-based traffic routing and health checking.

Example

When a user accesses:

https://www.example.com

Route 53 can resolve:

        www.example.com
              ↓
          203.0.113.10

The browser can then connect to the server at that address.

## AWS Lambda

>AWS Lambda is a serverless, event-driven compute service that executes application code in response to events without requiring the user to provision or manage servers.

You upload your code as a Lambda function, and AWS automatically handles the underlying compute infrastructure, including provisioning, scaling, and availability.

How it works
  ```text
Event
  │
  ▼
AWS Lambda
  │
  ├── Execute function
  │
  └── Return result / perform action
```
## Amazon RDS

>Amazon RDS (Relational Database Service) is a managed AWS service that simplifies the deployment, operation, scaling, and maintenance of relational databases in the cloud.

RDS supports database engines such as PostgreSQL, MySQL, MariaDB, Oracle, and SQL Server.

###### How it works
 ```text
 Instead of installing and managing a database server yourself:

Traditional approach

EC2
 └── Install PostgreSQL
      ├── Configure database
      ├── Manage updates
      ├── Manage backups
      └── Manage availability

With RDS:

Application
     │
     ▼
Amazon RDS
     │
     └── PostgreSQL / MySQL / etc.

AWS manages much of the underlying infrastructure and database administration.
```
## AWS Trusted Advisor

>AWS Trusted Advisor peut fournir des recommandations qui peuvent être utiles avant ou pendant une migration, par exemple :
 ```text
Cost Optimization → identifier les ressources coûteuses ou sous-utilisées.
. Security → détecter certaines mauvaises configurations.
. Fault Tolerance → vérifier certains problèmes de résilience.
. Performance → identifier des problèmes de performance.
. Service Quotas → vérifier si les limites AWS risquent d'être atteintes.
```

## AWS VPC Endpoint
```text
An AWS VPC Endpoint is a networking feature that allows resources inside a VPC to communicate with supported AWS services or endpoint services without sending traffic through the public Internet.

Why use it?

The main benefits are:

+ Improved security — traffic can stay within the AWS network.
+ No Internet Gateway/NAT required for the endpoint connection.
+ Can reduce NAT Gateway data-processing costs in some architectures.
+ Allows you to control access to supported AWS services using endpoint policies.
Main types
```