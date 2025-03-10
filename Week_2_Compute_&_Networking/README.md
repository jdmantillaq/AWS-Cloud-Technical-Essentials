# Compute & Networking


## 1. Compute as a Service on AWS

Servers handle HTTP requests and responses, functioning within the client-server model. A client can be a person or computer that sends requests, while a server is a computer or collection of computers serving websites.

Common HTTP servers include:
- **Windows**: Internet Information Services (IIS)
- **Linux**: Apache HTTP Web Server, Nginx, Apache Tomcat

To run an HTTP server on AWS, you need to select a service that provides compute power. There are three main types of compute options in AWS:
1. **Virtual Machines**: Emulate physical servers. In AWS, these virtual machines are called **Amazon Elastic Compute Cloud** or **Amazon EC2**.
2. **Container Services**
3. **Serverless Computing**

Understanding Amazon EC2 is essential as it serves as the foundation for many AWS compute services.

### Amazon Elastic Compute Cloud (EC2)

Amazon EC2 (Elastic Compute Cloud) is a web service that provides secure and resizable compute capacity in the cloud, allowing users to provision virtual servers known as EC2 instances.

Users can create and manage EC2 instances through various interfaces, including the AWS Management Console and Command Line Interface (CLI).

To launch an EC2 instance, you need to define:

- **Hardware specifications**: CPU, memory, network, and storage.
- **Logical configurations**: Networking location, firewall rules, authentication, and operating system.
- **Amazon Machine Image (AMI)**: This is a pre-configured template that includes the operating system and software needed to launch an EC2 instance. It simplifies the server setup process.

The relationship between AMIs and EC2 instances is similar to a recipe and a cake; the AMI defines the instance, while the EC2 instance is the live version you interact with.

<p align="center">
    <img src="images/AMI.png" width="500px">
</p>

AMIs can be reused to create new instances with the same configurations, saving time and reducing errors. AMIs can be found in various categories, including:

- **Quick Start AMIs**
- **AWS Marketplace AMIs**
- **My AMIs**
- **Community AMIs**

### Amazon EC2 Instance Lifecycle

<p align="center">
    <img src="images/Instance_lifecycle.png" width="600px">
</p>

#### EC2 Instance Configuration

When creating an EC2 instance, you need to select the operating system, instance type, network, and storage based on your application’s needs.

#### Instance Types

EC2 instances are categorized into families based on their optimization for specific workloads, such as:

- **General Purpose**: Balanced resources for various workloads.
- **Compute Optimized**: High-performance processors for compute-bound applications.
- **Memory Optimized**: Fast performance for memory-intensive applications.
- **Accelerated Computing**: Uses hardware accelerators for specific tasks.
- **Storage Optimized**: Designed for high I/O operations.

#### Availability Zones

EC2 instances reside in Availability Zones within a Virtual Private Cloud (VPC), which helps in architecting for high availability.

#### Instance Lifecycle

Instances transition through states (pending, running, stopped, terminated) and can be rebooted, stopped, or terminated based on your needs.

#### Pricing Options

EC2 offers various pricing models, including:
- **On-Demand Instances**: Pay for what you use without long-term commitments.
- **Reserved Instances**: Commit to a term for a discount.
- **Spot Instances**: Purchase unused capacity at a lower price.

### Container Services on AWS

**Containers:** A container is a standardized unit that packages code and its dependencies, allowing it to run reliably across different environments. This technology has evolved from the 1970s and addresses issues of software reliability during transitions between environments.

**Docker:** A popular container runtime that simplifies the management of containers, making it easy to create, package, deploy, and run them.

**Containers vs. Virtual Machines (VMs):** Containers share the host OS and kernel, making them lightweight and faster to start compared to VMs, which require a full OS copy.

**Orchestration:** Containers on AWS run on EC2 instances, and managing them at scale requires orchestration services like Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS).

**Amazon ECS:** An end-to-end service for managing containers, requiring the installation of the Amazon ECS Container Agent on EC2 instances.

**Amazon EKS:** A service for managing Kubernetes workloads in the AWS Cloud, providing advanced orchestration capabilities.

<p align="center">
    <img src="images/Containers.png" width="500px">
</p>

### Serverless Services

<p align="center">
    <img src="images/EC2_Lambda.png" width="500px">
</p>

- **Serverless Computing:** Serverless services, like AWS Lambda, abstract the underlying infrastructure, meaning you don't manage the servers directly. This allows you to focus on your application rather than operational tasks like scaling and maintenance.

- **Shared Responsibility Model:** With serverless offerings, AWS takes on more responsibility for the underlying infrastructure, while you remain responsible for aspects like data encryption and access management.

#### AWS Fargate

<p align="center">
    <img src="images/AWS_Fargate.png" width="500px">
</p>

**AWS Fargate**, a serverless compute platform for containers that works with ECS (Elastic Container Service) and EKS (Elastic Kubernetes Service). Here are the key points:

- **Container Orchestration:** ECS or EKS manages the lifecycle of containers.
- **Compute Platform:** Fargate allows you to run containers without managing the underlying infrastructure.
- **No Provisioning Required:** You don't need to worry about provisioning, patching, or managing servers.
- **Cost Structure:** You pay only for the resources (vCPU, memory, storage) consumed by your applications.
- **Use Cases:** Fargate is suitable for microservices, batch processing, machine learning applications, and migrating on-premises applications to the cloud.

#### AWS Lambda

<p align="center">
    <img src="images/Lambda_Function.png" width="500px">
</p>

- **AWS Lambda** is a serverless compute service that allows you to run code in response to triggers without managing servers.
- You create a **Lambda function** by uploading your code, which runs when a specified trigger occurs (e.g., HTTP requests, file uploads to Amazon S3).
- Lambda functions operate in a managed environment that is **scalable** and **highly available**.
- You can choose the programming language, memory, CPU allocation, and permissions for your function.
- Lambda is designed for short tasks (under 15 minutes) and is not suitable for long-running processes.
- You are billed only for the compute time used, rounded to the nearest millisecond.

An example use case is resizing images uploaded to S3, where a Lambda function is triggered upon a new upload to process the image.

## 2. Networking on AWS

Networking Definition: Networking connects computers globally, allowing them to communicate. An example is the AWS global infrastructure, which uses data centers, Availability Zones, and Regions.

Networking Basics: Similar to sending a letter, networking requires:

- **Payload**: The message itself.
- **Sender's Address**: Information about the sender.
- **Recipient's Address**: Information about the recipient.
- **IP Addresses**: Each computer has a unique IP address, similar to a home address, which is represented in binary format (0s and 1s).

**IPv4 Notation**: IP addresses are typically shown in decimal format, divided into four octets (8 bits each), separated by periods.

**CIDR Notation**: This notation specifies a range of IP addresses. It starts with an IP address followed by a slash and a number indicating how many bits are fixed. For example, 192.168.1.0/24 indicates a range of 256 IP addresses.

**AWS Network Sizing**: In AWS, the smallest IP range is /28 (16 IP addresses) and the largest is /16 (65,536 IP addresses).


### Amazon VPC

- **VPC (Virtual Private Cloud):** An isolated network in the AWS cloud, similar to a traditional data center network. When creating a VPC, you need to choose:
    - A name for your VPC.
    - A Region where the VPC will reside, spanning multiple Availability Zones.
    - An IP range in CIDR notation, determining the network size (up to four /16 IP ranges).

* **Subnets:** Smaller networks within a VPC, used for high availability and connectivity options. When creating a subnet, you need to select:
    - The VPC it belongs to.
    - The Availability Zone.
    - A CIDR block that is a subset of the VPC's CIDR block.
* **High Availability:** It's important to create at least two subnets in different Availability Zones for redundancy.

- **Reserved IPs:** AWS reserves five IP addresses in each subnet for routing and management, impacting network design.

- **Gateways:**
    - Internet Gateway: Connects your VPC to the internet, similar to a modem, and is highly available.
    - Virtual Private Gateway: Connects your VPC to another private network, allowing for an encrypted VPN connection

<p align="center">
    <img src="images/AWS_VPC.png" width="500px">
</p>

### Amazon VPC

- The VPC has an **internet gateway** and four subnets (two public and two private) across two availability zones.
-** Route tables** are essential for directing internet traffic to the correct subnets. They contain rules (routes) that determine where network traffic is directed. The route table acts like a set of instructions that tells traffic (data) how to get to the right place inside that room.
- When a new VPC is created, AWS automatically generates a **main route table** that allows local traffic between subnets.
- To provide public access to a subnet, a custom route table must be created with a route to the internet gateway.

<p align="center">
    <img src="images/VPC_Routing.png" width="650px">
</p> 

### Secure Your Network with Amazon VPC Security

#### Network ACLs:

Network ACLs are like the security gates at the entrance of a neighborhood. They control what kind of traffic can come in and go out of your subnet, which is a smaller section of your VPC. By default, these gates are wide open, allowing all traffic. However, you can customize them to only allow specific types of traffic, like HTTPS, which is used for secure web browsing. Just remember, if you let traffic in, you also need to allow the corresponding traffic out, because these gates don’t remember past actions—they treat each request independently.
- Act as a firewall at the subnet level.
- Control what traffic can enter and leave the subnet.
- By default, they allow all traffic but can be customized to restrict specific types (e.g., only allowing HTTPS).
- They are **stateless**, meaning you must set rules for both inbound and outbound traffic.
#### Security Groups:
Security Groups are like the security guards at the front door of a specific house (or EC2 instance). They are more flexible and remember if a connection was initiated from inside or outside. By default, they block all incoming traffic but allow all outgoing traffic. If you want your house (EC2 instance) to accept visitors (like web traffic), you need to tell the guard to let them in by opening specific doors (inbound ports) for HTTP and HTTPS traffic.
- Function as firewalls at the EC2 instance level.
- Block all inbound traffic by default but allow all outbound traffic.
- You must create inbound rules to allow specific traffic (e.g., HTTP and HTTPS).
T- hey are **stateful**, meaning they remember the connection and allow responses without needing additional rules.


<p align="center">
    <img src="images/Security_VPC.png" width="650px">
</p> 
