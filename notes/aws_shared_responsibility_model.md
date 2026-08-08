# AWS Shared Responsibility Model

## What is the Shared Responsibility Model?

The AWS Shared Responsibility Model explains how security responsibilities are divided between AWS and the customer.

When using cloud services, security is not handled entirely by AWS and it is not handled entirely by the customer. Each side has specific responsibilities depending on the part of the infrastructure they control.

The main idea is:

- AWS is responsible for **security of the cloud**.
- The customer is responsible for **security in the cloud**.

---

# Security of the Cloud (AWS Responsibility)

AWS is responsible for protecting the infrastructure that runs all AWS services.

This includes:

- Physical data centers
- Servers and hardware
- Networking infrastructure
- Storage systems
- The virtualization layer

AWS ensures that the cloud platform itself is secure, reliable, and available.

For example, if a company runs an application on Amazon EC2, AWS is responsible for the physical server where the EC2 instance is running.

The customer does not need to manage:
- Data center security
- Hardware maintenance
- Physical access control

---

# Security in the Cloud (Customer Responsibility)

The customer is responsible for securing everything they create and configure inside AWS.

This includes:

- Identity and access management
- Data protection
- Operating system configuration
- Network security
- Application security

For example, when using an EC2 instance, the customer is responsible for:

- Creating secure IAM permissions
- Configuring Security Groups correctly
- Updating the operating system
- Protecting application credentials
- Encrypting sensitive data

AWS provides the tools, but the customer must configure them correctly.

---

# Responsibility Depends on the AWS Service

The level of responsibility changes depending on the type of service used.

## Infrastructure Services (IaaS)

Example:

- Amazon EC2

The customer has more responsibilities because they manage the operating system and applications.

```
AWS:
- Hardware
- Data center
- Network
- Virtualization

Customer:
- Operating system
- Applications
- Data
- IAM
- Security configuration
```

---

## Managed Services (PaaS)

Example:

- Amazon RDS

AWS manages more components because it manages the database infrastructure.

```
AWS:
- Hardware
- Database software
- Patching
- Infrastructure

Customer:
- Database access control
- User permissions
- Data protection
- Application configuration
```

---

## Software Services (SaaS)

Example:

- Amazon S3

AWS manages most of the infrastructure, but customers are still responsible for how they use the service.

```
AWS:
- Infrastructure
- Service availability

Customer:
- Permissions
- Data
- Encryption settings
```

---

# Example: Web Application on AWS

Imagine a web application running on:

- EC2 for the application
- RDS for the database
- S3 for file storage

The responsibilities are divided:

```
                 AWS Responsibility

        Physical Infrastructure
        Data Centers
        Hardware
        Networking
        Managed Services


              Customer Responsibility

        IAM Permissions
        Application Security
        Data Protection
        Security Groups
        Database Access
```

---

# Why is this Model Important?

Understanding this model prevents security mistakes.

A common misunderstanding is:

"Everything is managed by AWS, so I don't need to worry about security."

This is incorrect.

AWS protects the infrastructure, but customers must properly configure their resources.

For example:

- AWS secures the S3 infrastructure.
- The customer must make sure the S3 bucket permissions are not publicly exposed.

---

# Security Best Practices

Based on the Shared Responsibility Model, customers should:

- Apply the principle of least privilege with IAM.
- Encrypt sensitive data.
- Regularly review permissions.
- Secure network access using Security Groups.
- Monitor activities using services like CloudTrail.
- Keep applications and operating systems updated.

---

# Important Points I Learned

- Cloud security is a shared responsibility between AWS and the customer.
- AWS secures the infrastructure, while customers secure their workloads.
- The more control a customer has over a service, the more security responsibilities they have.
- Using managed services reduces operational responsibilities but does not remove the need for proper security configuration.
- Understanding this model is essential for designing secure cloud architectures.