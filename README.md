https://www.youtube.com/watch?v=Rnr5hp4njq0

- Resources
    
    https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbUYzNUZPdVZuUVE0X3J1aEQzanE4OVI4WmJzZ3xBQ3Jtc0tuYXhGa3VxMUZpTFFncTBEZzRBZ2ZobWNBTlRldW8xdmxVUWZvdHZUZDlkMWppVEluU3BaMzQ1eGkzYTFmTERIMUprWGhfd0VZQWdYc1ZKRlE1Zlo2alluWjVwbGJBT3ZUSGZoOUFqendldzczWmFzaw&q=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Faws-certified-solutions-architect-associate-saa-c03%2F%3Fdeal_code%3DUDEAFNULP0324%26utm_term%3DHomepage%26utm_content%3DTextlink%26utm_campaign%3DNewUserLP0324%26utm_source%3Daff-campaign%26utm_medium%3Dudemyads%26LSNPUBID%3Dznpz0s2okgU%26ranMID%3D47901%26ranEAID%3Dznpz0s2okgU%26ranSiteID%3Dznpz0s2okgU-hXF7jTQhcT8LsgomWJDo7g%26gad_source%3D1&v=Rnr5hp4njq0
    
    https://www.udemy.com/course/practice-test-aws-certified-solutions-architect-associate/
    
    Mock test: https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbTQ0b1ctczM3Q0E0NFBmMkJFSmh4eTk3NTlwQXxBQ3Jtc0tsYmhYcW41Wk5wNlRXYXJReF85dDJXRG1RRzByYnVXbUp5V0owOFlpWXR1TmVxYTU0cjRxMk9HejNOYVNwaEVidWJ1aFFNeWcwclM0OGxoUVA1QXYyMHJEcnhFUmlfNGxxaDVSU0xUZWliUzRPSGdjaw&q=https%3A%2F%2Fportal.tutorialsdojo.com%2Fproduct%2Faws-certified-solutions-architect-associate-practice-exams%2F&v=Rnr5hp4njq0
    
- Weightage
    
    Domain 1: Design Secure Architecture (20 Q’s)
    
    Domain 2: Design Resilient Architecture (17 Q’s)
    
    Domain 3: Design High performing Architecture (16 Q’s)
    
    Domain 4: Cost optimised Architecture (13 Q’s)
    

AWS Cloud Use Cases

- Used to build scalable applications
- Backup & Storage, Big Data Analytics
- host website, Mobile & Social Apps
- Gaming servers

**AWS GLOBAL INFRASTRUTURE**: https://infrastructure.aws/

- AWS Regions
- AWS Availability Zones
- AWS Data Centres
- AWS Edge Locations/ Points of Presence

## AWS REGION

- AWS Regions are geographical areas around the world where Amazon Web Services (AWS) hosts its data centres.
- Each **Region** is in a **different country or area**
    
    Examples:
    
    - `us-east-1` → North Virginia
    - `ap-south-1` → Mumbai
    - `eu-west-1` → Ireland
- Each Region contains **multiple Availability Zones (AZs)**
    - AZs are **separate data centres**
    - Designed to prevent failure if one data centre goes down
- Data stays in the region you choose
- **Choose region closer to users** → lower latency (faster apps)
    
    ## **How to choose an AWS Region?**
    
    - **Legal/data rules** → some countries require data to stay local
    - **Closest to users** → faster performance
    - **Service availability** → not all AWS services exist in every Region
    - **Cost** → pricing differs by Region

## AWS Availability Zones

Independent Data Centres inside a AWS Region.

- Each regions has many availability Zones.
    - min: 3
    - max: 6
- Each AZ have independent power/ network.
- They’re separate from each other, so that they’re isolated from disasters.
- They’re connected with high bandwidth, ultra-low latency networking.

## AWS Edge Locations

These are AWS sites placed close to end users **to deliver content faster.**

They are mainly used by:

- **CloudFront (CDN)**
- Route 53
- AWS Shield / WAF

They **do NOT run your EC2 servers or databases.** They only **cache and serve content.**

## What do Edge Locations do?

They store **copies of your static content**, like:

✅ Images

✅ Videos

✅ CSS / JS files

✅ HTML pages

So users don’t need to go all the way to your main Region every time.

**benefits:** Much faster loading, Lower latency, Reduced load on main servers

> Short note:
> 
- **Region** → City (where your app servers live)
- **AZ** → Data centres in that city
- **Edge Location** → Nearby delivery points for users

## IAM : Identity and Access Management

- IAM allows you to **create users, roles, and permissions** to securely control access to AWS services and resources.
- Root account is created by default, it shouldn’t be shared or used.
- Create users in IAM & users can be grouped.

### **IAM USERS**

- A **person or application** that needs access to AWS.
    
    **Example**:
    
    - You (developer)
    - Admin user
    - Application user
    
    Each user can have:
    
    - Username & password (AWS Console)
        - Access keys (API / CLI)

### IAM Groups

- A **collection of users** with the same permissions.
    
    Example:
    
    - `Admins`
    - `Developers`
    - `ReadOnlyUsers`
    
     Instead of giving permissions to users one by one, you add users to a group.
    
    - Group only contains users, not other groups.
    - one user can belong to multiple groups.

### IAM Policies

- Users or groups can be assigned JSON documents called **Policies**.
- These policies define the permissions of the user.
- They answer:
    - What action? (`s3:GetObject`)
        - On which resource? (bucket, EC2, etc.)
        - Allowed or denied?
- Policies are written in **JSON**.
    
    Example:
    
    ```json
    	{
    "Effect":"Allow",
    "Action":"s3:ListBucket",
    "Resource":"*"
    }
    ```
    

### IAM Policy Inheritance

 permissions defined at a higher level in a hierarchy (organisation, folder, group) automatically apply to lower-level entities (projects, resources, users).

### IAM Policy Structure (JSON)

An **IAM policy** is a **JSON document** that defines **permissions**

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:ListBucket"
      ],
      "Resource": [
        "arn:aws:s3:::company-data",
        "arn:aws:s3:::company-data/*"
      ]
    }
  ]
}
```

- Version: Policy language version
- Statement: One policy can have multiple statements
    - Effect: Two values (Allow/ Deny)
    - Action: Defines **what action is allowed/denied**.
    - Resource: Defines **which resource** the action applies to.

## IAM - Multi Factor Authentication

- Password + security device you own
- protect Root account and IAM users
- MFA device options:
    - Virtual MFA device
    - Universal 2nd Factor security key (physical key)

## Different ways to access AWS

- AWS Management Console : protected by password+ MFA
- AWS Command line Interface (CLI) : protected by access keys
- AWS Software developer kit (SDK)- for code : protected by access keys
    
    Access keys generated by AWS Console
    
    - Access key ID: username
    - Secret access key: password
    
    ## AWS CLI (Command Line Interface)
    
    - A tool that enables you to **interact with AWS services using commands** in command line shell/ terminal.
    - direct access to public APIs of AWS services
    - best for admin tasks.
    - faster than web console.
    - easy to automate tasks.
        
        ### What can you do with it?
        
        Using simple commands, you can:
        
        - List S3 buckets
        - Start / stop EC2 instances
        - Upload files to S3
        - Create IAM users
        - Check logs, configs, and more.
        
        ### Working of CLI
        
        - install CLI in system
        - Type command
        - CLI sends a request to AWS APIs
        - AWS checks IAM permissions
        - AWS returns results.
    
    ## AWS SDK
    
    - AWS SDK lets you **access AWS services directly from your code** (Java, Python, JavaScript, etc.) instead of typing command.
    - best for application development.
        
        ### How AWS SDK works (flow)
        
        1. Your code calls AWS SDK
        2. SDK signs the request using credentials
        3. AWS checks **IAM permissions**
        4. AWS returns response (JSON/object)

## IAM Roles

- A temporary password set that AWS services or users can assume to access AWS resources without using username/password or access keys.
- Best for **EC2, Lambda, ECS, SDK usage.**
    
    example: An EC2 instance needs to read files from S3.
    
    Bad way: Store access key + secret key on EC2
    
    Correct way:
    
    - Attach **IAM Role** to EC2
    - Role has **S3 read permission**
    - EC2 automatically gets temporary credentials

## IAM Security Tools

### IAM Credentials Report (account level)

- A report that list all the account’s users and the status of their various credentials.

### IAM Access Advisor (user level)

- shows the service permissions granted for a particular user and when those services were last accessed.

## Amazon Elastic Compute Cloud  (EC2)

- It is an AWS service that lets you **rent virtual computers (servers)** in the cloud to run your applications.
- Instead of buying a physical server, you **launch a virtual machine** on AWS and pay **only for the time you use it.**

### What you can do with EC2

- Host **websites & backend APIs**
- Run **applications** (Java, Python, Node.js, etc.)
- Deploy **microservices**
- EC2 consists in the capability of :
    - Renting virtual servers (EC2)
    - store volumes of data on virtual drives (EBS- Elastic Block Store)
    - distributing load across machines (ELB- Elastic Load Balance)
    - scaling the services using an auto-scaling group (ASG- Auto Scaling Group).

### EC2 sizing and configuration options

- Operating System (OS): Linux, Windows, mac OS
- How much compute power & cores (CPU)?
- How much RAM?
- How much storage space:
    - Network-attached (EBS & EFS)
    - hardware (EC2 instance store)
- Network card: speed of the card, public IP address
- Firewall rules: security group
- Bootstrap script (configure at first launch) : EC2 user data

### **EC2 User Data**

It is a feature of **Amazon EC2** that lets you **run a script automatically when an EC2 instance starts for the first time**. 

(startup instructions for the server ~bootstrap script)

- It runs on first launch.
- executes as root user.
- used to install software(Apache, Docker, Node.js,….), update OS packages, start services etc

### EC2 Instance Type

In **Amazon EC2**, an **instance type** defines **how much CPU, memory (RAM), storage, and networking power** your virtual server gets.

Naming convention for the instance types:

ex: m5.2xlarge (API name)

- m : instance family
- 5 : generation
- 2xlarge : instance size

**Instance Family:**

| Letter | Type |
| --- | --- |
| `t`, `m` | General Purpose |
| `c` | Compute Optimised |
| `r`, `x`, `z` | Memory Optimised |
| `i`, `d`, `h` | Storage Optimised |
| `p`, `g`, `inf`, `trn` | Accelerated / ML |

**Instance Size:**

| Size | Relative capacity |
| --- | --- |
| `nano` | smallest |
| `micro` | very small |
| `small` | small |
| `medium` | medium |
| `large` | large |
| `xlarge` | very large |
| `2xlarge`, `4xlarge` | very high |

**EC2 Instance Type categories:**

1. General Purpose
2. Compute Optimised
3. Memory Optimised
4. Accelerated Optimised
5. Storage Optimised
6. Instance Features
7. Measuring Instance Performance

| **Category** | **When Used** | **Best For** | **Example Instance Types** |
| --- | --- | --- | --- |
| **General Purpose** | Balanced CPU + RAM | Web servers, backend APIs, dev/test environments | `t3.micro`, `t3.small`, `m5.large`, `m6g.large` |
| **Compute Optimised** | High CPU performance | Batch processing, high-performance APIs, scientific calculations | `c5.large`, `c6g.large`, `c5n.large` |
| **Memory Optimised** | Applications need large RAM | Databases, in-memory caching (Redis), big data processing | `r5.large`, `r6g.xlarge`, `x1.large` |
| **Storage Optimised** | High disk I/O & low latency storage | Data warehousing, log processing, NoSQL databases | `i3.large`, `i4i.large`, `d2.xlarge` |
| **Accelerated Computing** | Need GPUs or ML accelerators | Machine learning, AI training, video rendering | `p3.2xlarge`, `g4dn.xlarge`, `inf1.xlarge` |

### Security Groups

In **Amazon EC2**, **Security Groups** act as a **virtual firewall** that controls **who can access your EC2 instances**.

They decide **which traffic is allowed IN and OUT** of your instance.

### What Security Groups do

- Control **Inbound traffic** (who can come in)
- Control **Outbound traffic** (where traffic can go)
- Authorised IP ranges - IPv4 & IPv6
- Access ports

**Common ports to remember:**

| Port | Use |
| --- | --- |
| 22 | SSH (Linux login) |
| 3389 | RDP-remote desktop protocol (Windows login) |
| 80 | HTTP (access unsecured websites) |
| 443 | HTTPS (access secured websites) |
| 3306 | MySQL |
| 5432 | PostgreSQL |
| 21 | FTP (upload files to file share) |
| 22 | SFTP (upload files using SSH) |

### SSH Connection Table:

|  | SSH | Putty | EC2 Instance Connect |
| --- | --- | --- | --- |
| Mac |             ✅ |  |                  ✅ |
| Linux |             ✅ |  |                  ✅ |
| Windows<10 |  |            ✅ |                  ✅ |
| Windows≥10 |             ✅ |            ✅ |                  ✅ |

**EC2 Instance Connect (EIC): connect to a Linux EC2 instance using SSH without managing permanent key pairs** in advance.

| **Method** | **Used On** | **How it Works** | **Best For** | **Key Needed** |
| --- | --- | --- | --- | --- |
| **SSH** | Linux / macOS | Terminal → `ssh -i key.pem user@ip` | Developers, automation | `.pem` key |
| **PuTTY** | Windows | GUI tool → converts `.pem` to `.ppk` | Windows users | `.ppk` key |
| **EC2 Instance Connect** | Any OS (browser) | AWS Console → temporary SSH key | Quick, secure access | ❌ No permanent key |

### EC2 Instance Purchasing Options

1. **On-Demand Instance**
    - Pay for what you use
    - Linux/ Windows : after the first minute billing starts per seconds.
    - no long-term commitment
    - recommend for short term and uninterrupted workloads
    
2. **EC2 Reserved Instance**
    - up to 72% discount compared to On-Demand
    - reserve a specific attributes like Instance type, region, tenancy, OS etc
    - more reservation period gets more discount.
    - reserved instance scope: region or zonal.
    - buy & sell in the reserved instance marketplace.
    - Convertible reserved instance
        - can change the Instance type, region, tenancy, OS
        - upto 66% discount
    - recommend for steady usage application

1. **EC2 Savings Plan**
    - get discount based on long-term usage. (upto 72%)
    - commit to a certain type of usage ($10/hr for 1 or 3 yrs)
    - usage beyond EC2 Savings plan is billed at the on-demand price
    - fixed to specific instance type or AWS region

1. **EC2 Spot Instances**
    - can get a discount upto 90% compared to on-demand.
    - instance that you can lose at any point of time if your max price < current spot price.
    
2. **EC2 Dedicated Host**
    - gives you a **physical server fully dedicated to your use** in **Amazon EC2**.
    - Purchasing options:
        - reserved: 1-3year
    - used for the software that has complicated licensing model

1. **EC2 Dedicated Instance**
    - instances run on hardware that’s dedicated to you.
    - may share the hardware with other instances in same account.

1. **EC2 Capacity Reservations**
    - reserve on-demand instances capacity in specific AZ for any duration.
    - always have the access to EC2 capacity when you need it.
    - no time commitment (create/ cancel anytime), no billing discounts.
    - suitable for short term, uninterrupted workload that need to be in a specific AZ.

### EC2 Spot Instances

- **ask AWS for unused EC2 capacity at a very low price** in **Amazon EC2**.

- these instances can be interrupted by AWS with a 2-minute notice when capacity is needed
- Types:
    - **One-time**: runs once and ends when stopped/terminated
    - **Persistent**: Re-launches automatically after interruption.
- Interruption Behaviour:
    - **Stop**: Instance stops
    - **Delete**: Instance is deleted
    - **Hibernate**: state saved to EBS.
- Spot Blocks: **block** the spot instance for a specific time frame (1-6hrs) without any interruption.

### Spot Fleets

- **request and manage a group of Spot Instances** to meet a **target capacity** at the **lowest possible cost** in **Amazon EC2**.
- It is a set of spot instancs and on-demand instances.
    
    **Allocation Strategies:**
    
    | **Strategy** | **How it works** | **Best for** |
    | --- | --- | --- |
    | **lowestPrice** | Chooses cheapest Spot pools | short workloads, cost optimisation |
    | **diversified** | Spreads across many pools | High availability, long workloads |
    | **capacityOptimized** | Picks pools with most capacity | Fewer interruptions |
    | **capacityOptimizedPrioritized** | Capacity + priority order | Controlled resilience |
- Spot fleets allows us to automatically request Spot instances with the lowest price.

### Public & Private IP

IP: An **IP address (Internet Protocol address)** is a unique number assigned to every device connected to a network.

Networking has 2 sorts of IPs:

- IPv4 : most common format used online.
    - written in dotted decimal format.
    - format: [0-255].[0-255].[0-255].[0-255]
    - example: `198:132:5:1`
- IPv6 : newer and solves problem for IOT.
    - written in hexadecimal format.
    - format: xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx
    - example: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`

### Public IP

- Used to access the instance from the internet.
- Assigned by AWS
- Changes when instance is stopped or started
- Only works if:
    - Instance is in a **public subnet**
    - Route table has **Internet Gateway**
    - Security Group allows traffic
- Example: `54.210.34.12`

### Private IP

- **Used for internal communication inside AWS**
- machines can only be identified on private network only.
- Assigned from the **VPC subnet range**
- Used for **instance-to-instance** communication
- best for : backend servers, databases, internal APIs, App-DB communication.

### Elastic IP (EIP)

- A **static public IP** that **does not change**
- fixed public access
- free when attached, charged when unused.
- account can have only 5 elastic IPs (ask AWS to increase)

### Placement Groups

**Placement Groups** control **how EC2 instances physically placed on hardware** inside AWS data centres to meet **performance, availability, or fault-tolerance** needs.

- decide **where** your instances live physically—not what size they are.

Types:

- **Cluster**: Instance are placed in same AZs.
    - **goal** : low latency, high throughput
    - cluster instances into a low latency group in a single availability zones.
    - If AZ fails → all impacted
    - great network : 10Gbps bandwidth between instances
    - **cons**: if one rack fails, all  instances fails at the same time.
- **Spread**: Instances placed on distinct hardware
    - goal: Maximum fault tolerance
    - limit: Max 7 instances per AZ (per group)
    - can spread across different AZs
    - reduced risk of simultaneous failure.
- **Partitions**: Instances split into isolated partitions in multiple AZs. each partitions can have multiple EC2 instances.
    - goal: Balance **scale + fault isolation**
    - scale: Hundreds of instances per group
    - can span across multiple AZs in the same region
    - The instance in the partition does not share rack with the instances in the other partitions
    - A partition failure can affect many EC2 but won’t affect other partition.
    - EC2 instances get access to the partition information as metadata.

### **Elastic Network Interface (ENI)**

**It is virtual network card** that is attached to an EC2 instance in **Amazon EC2**.

An ENI comes with:

- **Primary private IPv4**
- **Secondary private IPv4s** (optional)
- **Elastic IPv4(s)** (optional)
- **MAC address**
- **Security Group(s)**
- **Subnet information**

create ENI independently and attach them on the fly(move them) on EC2 instances for failover.

| ENI Type | Description |
| --- | --- |
| **Primary ENI** | Created automatically at instance launch |
| **Secondary ENI** | Manually attached/detached |

### Why ENIs are useful

- High availability / failover
    - Detach ENI from a failed instance
    - Attach it to a healthy instance
    - **IP address stays the same**
- Multiple network interfaces
    - One instance can have **multiple ENIs**
    - Separate traffic (public vs backend)
- Security separation
    - Different **security groups per ENI**
    - Isolate traffic types

### **EC2 Hibernation**

**EC2 Hibernation** lets you **pause an EC2 instance and later resume it exactly where it left off** by **saving the contents of RAM to the root EBS volume** in **Amazon EC2**.

| Action | What happens | RAM | EBS | Instance ID |
| --- | --- | --- | --- | --- |
| **Stop** | Instance shuts down | ❌ Lost | ✅ Kept | ✅ Same |
| **Terminate** | Instance deleted | ❌ Lost | ❌ Deleted | ❌ New |
| **Hibernate** | RAM saved to EBS | ✅ Saved | ✅ Kept | ✅ Same |

### When should you use hibernation?

- Long startup applications
- In-memory workloads you don’t want to re-initialise
- Development / testing environments
- Spot Instances that support **hibernate on interruption**

- An instance can be hibernated more than 60 days
- Root volume- must be EBS, encrypted, not instance store
- instant RAM Size: must be less than 150gb

### EBS Volume

(network drive ~virtual hard disk)

An **EBS volume (Elastic Block Store volume)** is a **persistent block storage device in AWS** that you can attach to an EC2 instance, just like a hard disk to store the files, OS, applications, databases. (virtual hard drive) 

- EBS can only be mounted to one instance at a time.
- Data remains safe even if the instance is stopped.
- Can attach/detach volumes anytime
- Its locked to specific AZ zone
an EBS volume in us-east-1a cannot be attached to us-east-1b
To move data across, you need to create a snapshot of it (backup).
    
    ### **EBS SNAPSHOTS**
    
    An **EBS Snapshot** is a **backup** of an EBS volume at a **point-in-time.**
    
    use this snapshot to:
    - Restore data
    - Create a new volume
    - Recover from failures
    
    - Snapshots are stored in Amazon S3
    - Snapshots are stored at **region level** (not AZ)
    - Supports encryption
    
    ### EBS Snapshot Features
    
    - **EBS Snapshot Archive**
        - It is a **low-cost storage tier** for snapshots that are 75% cheaper.
        - retrieval takes hours (slow retrieval)
        - take within 24-72 hrs for restoring the archive.
    - **Recycle Bin for EBS Snapshots**
        - A safety feature that **prevents accidental deletion** of snapshots.
        - setup rules to maintain the deleted snapshots to recover them after an accidental deletion.
        - specify retention (1 day -1 year)
        - Can **restore snapshot easily**
    - **Fast Snapshot Restore (FSR)**
        - allows volumes created from snapshots to be **instantly usable with full performance**.
        - Costs extra 💸
        - Best for **performance-critical apps**

### AMI (Amazon Machine Image)

An **AMI** is a **pre-configured template** used to launch EC2 instances in AWS. or

A **ready-made OS + software package** that you use to create virtual machines.

It contains everything needed to launch an instance:

- Operating System (Linux/Windows)
- Application software
- Configuration settings

AMI are built to specific region(and can be copied across regions)
Uses **EBS snapshots** internally
AMI is created from EBS snapshots

Type of AMI to launch EC2 instances:

| Type | Description |
| --- | --- |
| **Public AMI** | Available to everyone |
| **Private AMI** | Only your account |
| **Marketplace AMI** | Paid AMIs from AWS Marketplace (someone else made and sells) |

AMI process(from an EC2 instance)

- Start an EC2 instance and customise it.
- Stop the instance (for data integrity)
- Build an AMI- this will also create EBS snapshots
- Launch instances from other AMIs.

### EC2 Instance Store

An **EC2 Instance Store** is a **temporary (ephemeral) block storage** that is physically attached to the host machine running your EC2 instance.

 A **local hard disk of the server** (not network storage like EBS)

- very fast but data is lost when the instance stops/ terminates.
- High performance- very low latency.
- High IOPS (input/output operations per second).
- cannot take backups like EBS snapshots.
- If instance moves to another host → data gone
    
    ### Suitable For:
    
    - Cache (Redis, Memcached)
    - Big data processing

### EC2 volume types (check in office laptop)

### EFS (Elastic File System)

allows multiple EC2 instances to access the same file system at the same time

- highly available, scalable, expensive, pay per use
- data is stored across multiple Availability Zones
- no need to manage servers or storage
    
    **How It Works (Step-by-Step)**
    
    1. Create an EFS file system in AWS
    2. Attach it to EC2 instances using **NFS protocol**
    3. EC2 instances access it like a local directory
    4. All instances see the same files in real-time

| Feature | EFS | EBS | S3 |
| --- | --- | --- | --- |
| Type | File storage | Block storage | Object storage |
| Access | Multiple instances | One instance (mostly) | Via API |
| Scaling | Automatic | Manual | Automatic |
| Use case | Shared file systems | OS/Database storage | Backup, static files |

### **EFS- Performance & Storage classes**

- **EFS Scale:**
    - 1000s of concurrent NFS clients, 10 GB+ /s throughput
    - Grow to petabyte scale network file system, automatically.
- **Perfomance mode:**
    - higher latency, throughput, highly parallel
- **Throughput mode:**
    - bursting - 1 TB = 50MiB/s + burst of up to 100MiB/s
    - set the throughput regardless of storage size
    - automatically scales throughput up or down based on your workloads

### EFS - Storage Classes

- **Storage Tiers** (lifecycle management feature- move files after N days)
    - **Standard**: for frequently accessed files
        - fast access, high throughput
    - **Infrequent access (EFS-IA)**: files accessed less often.
        - cost to retrieve files, lower price to store.
    - **Archive**: rarely accessed data, 50% cheaper.
    - Implement lifecycle policies to move files between storage tiers.
- **Availability and durability**
    - **Standard**: Multi-AZ, great for prod
    - **One zone**: One AZ, great for dev, backup enabled by default

example: 

- If file is not accessed for 30days → move to Infrequent access.
- If file is not accessed for 90days→ move to archive.

### LOAD BALANCING

 **automatically distributing incoming traffic across multiple servers** so that:

- No single server is overloaded
- Your app stays **fast**, **available**, and **fault-tolerant**
    
    ## Why do we need Load Balancing?
    
    Imagine 10,000 users hitting your app at once:
    
    - ❌ Without load balancing → server crash
    - ✅ With load balancing → traffic is shared → app keeps running

### **What is Elastic Load Balancing (ELB)?**

**Automatically distributes incoming traffic across multiple targets (EC2, containers, IPs)**

to keep your application **highly available, scalable, and fault-tolerant**

### Health Checks

It is a mechanisms to monitor the availability of resources by sending periodic requests, allowing Elastic Load Balancing (ELB), Route 53, and Auto Scaling to detect failures and redirect traffic or replace unhealthy nodes.

If the response is not 200(OK), then the instance is unhealthy.

### Types of Load Balancers

### 1️⃣ Application Load Balancer (ALB)

**Layer:** 7 (HTTP / HTTPS)

**Best for**

- Web applications
- REST APIs
- Microservices

**Key features**

- Path-based routing (`/login`, `/orders`)
- Host-based routing (`api.example.com`)
- Works with containers (ECS, EKS)
- Supports WebSockets

### Target Groups:

-logical groupings of backend resources that receive routed traffic based on rules

- EC2 instances (can be managed by an Auto Scaling)- HTTP
- EC2 tasks (managed by ECS itself) - HTTP
- Lambda Functions- HTTP request is translated into a JSON event
- IP addresses- must be private IPs
- ALB can route to multiple target groups

---

### 2️⃣ Network Load Balancer (NLB)

**Layer:** 4 (TCP / UDP)

**Best for**

- Ultra-high performance
- Low latency apps
- Millions of requests per second

**Key features**

- Handles TCP/UDP traffic
- Static IP support

---

### 3️⃣ Gateway Load Balancer (GWLB)

**Layer:** 3/4

Deploy, Scale and Manage a fleet of 3rd party network virtual appliances in AWS.

Combines the following functions:

- Transparent Network Gateway: single entry/exit for all traffic.
- Load Balancer: distributes traffic to virtual appliances.

Uses the GENEVE protocol on port 6081

**Best for**

- Security appliances
- Firewalls, IDS/IPS

**Used mainly in**

- Advanced network/security architectures

GLB Target groups:

- EC2 instances
- IP addresses

---

### 4️⃣ Classic Load Balancer (CLB)

- Supports TCP(Layer 4) , HTTP & HTTPS(Layer 7)
- Old generation/ version
- Used only in **legacy systems**
- Not recommended for new apps

### Security groups

It act as a virtual firewall for your load balancer, controlling both the inbound traffic it accepts from clients and the outbound traffic it sends to backend targets.

- **Load Balancer security group:** accepts request from anywhere.
- **EC2 load balancer security groups:** accepts requests only from the ec2 load balancer security group.

### Network Load Balancer

It distributes traffic at the **Transport Layer (Layer 4)** of the OSI model.

It handles **TCP, UDP, and TLS** traffic and is designed for **high performance and low latency**.

- NLB allows to forward TCP & UDP traffic to instances
- NLB handles **millions of requests** per seconds
- NLB has less latency ~100 ms
- NLB has one static IP per AZ, and supports  Elastic IP(helpful for whitelisting specific IP)

NLB Target Groups:

- EC2 instances
- IP addresses
- application Load Balancer
- Health checks support the TCP HTTP and HTTPS protocol.

### STICKY SESSIONS (Session Affinity)

 user’s requests are always sent to the **same backend server** for a period of time.

Instead of distributing each request randomly, the load balancer “sticks” the user to **one instance**.

This works for ALB & CLB.

### How Sticky Sessions Work

1. User sends first request.
2. Load balancer forwards it to **Instance A**.
3. Load balancer creates a **cookie**.
4. For next requests, the cookie ensures traffic goes to **Instance A** again.

### Why Sticky Sessions Are Needed?

   Used when application stores:

- Login session in memory
- Shopping cart data
- Temporary user data

Without sticky sessions:

- Request 1 → Server A
- Request 2 → Server B
- Session lost ❌

⚠ Not recommended for highly scalable systems because:

- Uneven traffic distribution
- Harder auto scaling
- If instance fails → session lost

### Cookies - Sticky Sessions

In sticky sessions, the load balance**r creates or uses a cookie** to remember which backend server handled the first request.

So next time:

- User sends request
- Browser automatically sends cookie
- ALB reads cookie
- ALB routes request to the same instance

### Types of Cookies:

- **Application based Cookies**
    - Custom Cookie:
        - Generated by target.
        - Cookie name must be specified individually for each target group.
    - Application Cookie:
        - generated by the load balancer.
        - cookie name is AWSALBAPP.
- **Duration based Cookies**
    - generated by the load balancer.
    - cookie name is AWSALB for ALB, AWSELB for CLB
        
        **How it works:**
        
        1. Client → ALB
        2. ALB → Instance A
        3. ALB sends cookie: `AWSALB=xyz`
        4. For the configured duration (e.g., 1 hour), all requests go to Instance A.

### CROSS-ZONE LOAD BALANCING

The load balancer distributes traffic **equally across all registered targets in all Availability Zones**, regardless of which AZ the request came from.

**Scenario**

Lets consider;

- **AZ-A** has 2 EC2 instances
- **AZ-B** has 4 EC2 instances

Total = **6 instances**

Traffic is coming equally into both AZs.

---

**❌ WITHOUT Cross-Zone Load Balancing**

Note: Each AZ handles **only its own traffic**

So:

- Traffic entering AZ-A → goes only to its 2 instances
- Traffic entering AZ-B → goes only to its 4 instances

### Example numbers:

Assume:

- 1000 requests come to AZ-A
- 100 requests come to AZ-B

Now:

- AZ-A: 1000 ÷ 2 = **500 requests per instance**
- AZ-B: 100 ÷ 4 = **25 requests per instance**

⚠ Problem:

Instances in AZ-A are overloaded.

Load is not evenly distributed.

---

**✅ WITH Cross-Zone Load Balancing**

Note: Traffic is shared across ALL instances in ALL AZs.

Now:

Total instances = 6

Total requests = 2000

Each instance gets:

2000 ÷ 6 = **~333 requests per instance**

✔ Even load

✔ No overload

✔ Better performance

| Load Balancer | CZLB Supported? | Default Setting | Can Disable? | Notes |
| --- | --- | --- | --- | --- |
| AWS Application Load Balancer | ✅ Yes | ✅ Enabled | ❌ No | Always distributes traffic evenly across all AZs |
| AWS Classic Load Balancer | ✅ Yes | ❌ Disabled
  • no charges if enabled | ✅ Yes | Must manually enable |
| AWS Network Load Balancer | ✅ Yes | ❌ Disabled
  • pay charges if enabled | ✅ Yes | Enabling may incur cross-AZ data charges |
| AWS Gateway Load Balancer | ✅ Yes | ❌ Disabled
• pay charges if enabled | ✅ Yes | Used mainly for network appliances |

### SSL/TLS

**SSL (Secure Sockets Layer)** and **TLS (Transport Layer Security)** are protocols used to:

- Encrypt data between client and server.

Today, **TLS** is used (SSL is outdated).

- SSL: encrypt connections.
- TLS: encrypt connections (newer version)

### Why We Need SSL/TLS?

Without SSL/TLS:

- Data travels in **plain text**
- Hackers can read passwords, card numbers
- ex: [http://mybank.com](http://mybank.com/)

With SSL/TLS:

- Data is **encrypted**
- Secure communication
- HTTPS instead of HTTP
- ex: [https://mybank.com](http://mybank.com/)
    
    
    | Load Balancer | SSL/TLS Support |
    | --- | --- |
    | ALB | ✅ HTTPS (Layer 7) |
    | NLB | ✅ TLS (Layer 4) |
    | CLB | ✅ Supported |
    | GLB | ❌ No TLS termination |

**TLS Termination:** Load Balancer decrypts traffic before sending to backend servers.

### Load Balancer - SSL Certificates

- load balancer uses an X.509 certificate (SSL/TLS server certificate)
- manage certificates using ACM (AWS certificate manager)

### SSL- SNI (Server Name Indication)

SNI allows one load balancer to host multiple SSL certificates for different domain names on the same IP address.

- only works for ALB & NLB
- server will find the correct certificate and return the default one.
    
    ### Why SNI is Needed?
    
    Normally:
    
    - 1 IP address → 1 SSL certificate → 1 domain
    
    But what if you want:
    
    - `app1.com`
    - `app2.com`
    - `app3.com`
    
    On the **same Load Balancer + same IP?** 
    
    **Step 1️⃣ Client Hello**
    
    Client says:
    
    > I want to connect to **app1.com**
    > 
    
    (The domain name is sent during TLS handshake.)
    
    **Step 2️⃣ Load Balancer Checks Domain**
    
    Load balancer sees the requested domain name.
    
    **Step 3️⃣ Correct Certificate Selected**
    
    Load balancer sends the correct certificate for **app1.com**.
    
    **Step 4️⃣ Secure Connection Established**
    

### Elastic Load Balancer - SSL Certificates

Configuring HTTPS on an AWS load balancer using an SSL/TLS certificate.

| Feature | CLB | ALB | NLB |
| --- | --- | --- | --- |
| Layer | 4 & 7 | 7 | 4 |
| HTTPS Support | ✅ Yes | ✅ Yes | ❌ (Uses TLS listener) |
| TLS Listener | ✅ Yes | ❌ (Uses HTTPS) | ✅ Yes |
| TLS Termination | ✅ Yes | ✅ Yes | ✅ Yes |
| SNI Support | Limited | ✅ Yes | ✅ Yes |
| Certificate Source | ACM / IAM | ACM | ACM |
| Best For | Legacy apps | Modern web apps | High performance TCP apps |

### Connection Draining

When a target (EC2 instance) is being removed or stopped, the load balancer waits for existing requests to finish before fully removing it.

Feature naming:

- **Connection Draining:** for CLB
- **De-registration Delay:** for ALB & NLB
    
    ### Why Is It Needed?
    
    Imagine:
    
    - User is downloading a file
    - Suddenly EC2 instance is terminated
    - Download fails ❌
    
    With connection draining:
    
    - Load balancer stops sending **new requests**
    - Allows **existing requests to complete**
    - Then safely removes the instance ✅
    
    | Load Balancer | Default Timeout |
    | --- | --- |
    | CLB | 300 seconds (5 min) |
    | ALB | 300 seconds |
    | NLB | 300 seconds |
    
    You can configure:
    
    - Minimum: 0 seconds
    - Maximum: 3600 seconds
    
    **Flow for Connection Draining & De-registration Delay**
    
    1️⃣ Instance marked for removal
    
    2️⃣ Load balancer stops sending new traffic
    
    3️⃣ Existing connections continue
    
    4️⃣ After timeout, instance is removed
    
    **De-registration Delay:**
    
    - **Default:** 300 seconds (5 minutes)
    - **Minimum:** 0 seconds
    - **Maximum:** 3600 seconds
    
    Configured at:
    
    👉 **Target Group level**
    
    ### Why It Is Important?
    
    Without de-registration delay:
    
    User uploading file → instance removed → upload fails ❌
    
    With deregistration delay:
    
    Upload completes → instance removed safely ✅
    

### Auto Scaling Group

automatically manages a group of EC2 instances to ensure:

- ✅ High availability
- ✅ Fault tolerance
- ✅ Cost optimization
- ✅ Automatic scaling based on demand

It works with **EC2 instances** and distributes traffic using a Load Balancer.

The goal of ASG is to:

- Scale Out (add EC2 instance) to match increase in load.
- Scale In (remove EC2 instance) to match decrease in load.
- ensure to have min and max number of EC2 instances running.
- recreate an instance in case a previous instance is terminated/failed.

**Step-by-step flow:**

1. You define a **Launch Template** (AMI, instance type, security group, key pair).
2. Create an **Auto Scaling Group**.
3. Attach it to:
    - Subnets (usually across multiple AZs)
    - Load Balancer (ALB/NLB)
4. Define:
    - Minimum instances
    - Desired capacity
    - Maximum instances
5. Configure scaling policies.

Now AWS automatically:

- Launches new EC2 instances when load increases.
- Terminates instances when load decreases.
- Replaces unhealthy instances automatically.
    
    ### Launch Template
    
    It defines all the configuration details required to create an instance, so you don’t need to manually configure settings each time. **(blueprint to launch EC2 instance)**
    
    A Launch Template can include:
    
    1. **AMI (Amazon Machine Image)**
        
        → OS like Amazon Linux, Ubuntu
        
    2. **Instance Type**
        
        → t2.micro, t3.medium, etc.
        
    3. **Key Pair**
        
        → For SSH login
        
    4. **Security Groups**
        
        → Firewall rules
        
    5. **IAM Role**
    6. **User Data Script**
        
        → Commands that run when instance starts
        
    7. **Storage configuration**
        
        → EBS volume size
        
    8. **Network settings**
        
        ### Desired Capacity
        
        Number of EC2 instances you want running.
        
        Example:
        
        - Min = 2
        - Desired = 3
        - Max = 6
        
        **Why Do We Need Launch Template?**
        
        Because when using:
        
        - Auto Scaling Group
        - Amazon EC2
        - EC2 Fleet
        
        AWS needs a **standard configuration** to launch new instances automatically.
        
        ASG cannot manually configure instances — it must follow a predefined template.
        
        ---
        
        **🔹 Example (Real-Time Scenario)**
        
        Imagine you are running a website:
        
        You configure:
        
        - Ubuntu AMI
        - t3.micro
        - Port 80 open
        - 20GB storage
        - Nginx installation script
        
        Instead of repeating this setup every time,
        
        👉 You create a Launch Template.
        
        Now whenever traffic increases:
        
        👉 Auto Scaling Group launches new identical servers using this template.
        
        ### **CloudWatch Alarm**
        
        A **CloudWatch Alarm** monitors a specific metric and takes action when it crosses a threshold.
        
        It works with:
        
        - Amazon CloudWatch
        - Amazon EC2
        - Auto Scaling Group
        
        **Step-by-step Flow:**
        
        EC2 sends metrics to **CloudWatch**.
        
        You create an Alarm:
        
        - Example: CPU > 70% (CPU utilisation >70%)
        
        If threshold is breached:
        
        - Alarm state becomes **ALARM**
        
        Alarm triggers an action:
        
        - Send notification (SNS)
        - Trigger Auto Scaling
        - Based on the alarm we can create :
            - **Scale-out policies** (increase number of instances)
            - **Scale-in policies** (decrease number of instances)
        
        **Example:**
        
        Imagine your website:
        
        Normal traffic → 2 instances
        Evening traffic spike → CPU goes 75%
        CloudWatch alarm triggers → ASG launches 2 more instances
        
        At night → CPU drops to 20%
        Scale-in policy removes extra instances
        
        💰 You pay only for required resources.
        
        ### **Dynamic Scaling Policies**
        
        Dynamic Scaling automatically adjusts the number of EC2 instances in an Auto Scaling Group based on real-time demand.
        
        It works using:
        
        - Amazon CloudWatch
        - Auto Scaling Group
        - Amazon EC2
        
        **Dynamic Scaling:** 
        
        Instead of manually increasing/decreasing instances, AWS automatically scales when a metric changes (like CPU).
        
        Example:
        
        - CPU > 70% → Add instances
        - CPU < 30% → Remove instances
        
        ### **Types of Dynamic Scaling Policies**
        
        - **Simple Scaling (Older method)**
            - Adds/removes fixed number of instances.
            - Has cooldown period (wait time before next action).
                
                Example:
                
                > If CPU > 70% → Add 1 instance
                > 
                > 
                > If CPU < 30% → remove 1 instance
                > 
                > Cooldown = 300 seconds
                > 
        - **Step Scaling (Better)**
            
            Scaling depends on how much threshold is crossed.
            
            Example:
            
            | CPU Level | Action |
            | --- | --- |
            | 70–80% | Add 1 instance |
            | 80–90% | Add 2 instances |
            | >90% | Add 3 instances |
            
            ✔ More flexible than simple scaling.
            
        - **Target Tracking Scaling (best)**
            
            You define a target value.
            
            Example:
            
            > Maintain average CPU at 50%
            > 
            > 
            > AWS automatically:
            > 
            > - Adds instances when CPU goes above 50%
            > - Removes instances when CPU goes below 50%
            
            ✔ No need to create multiple alarms
            
            ✔ Most recommended by AWS
            
            ✔ Easy and intelligent
            
        
        ### **Predictive Scaling**
        
        automatically increases capacity **before** traffic increases by using machine learning to forecast future demand.
        
        **Why Do We Need Predictive Scaling?**
        
        Dynamic scaling reacts **after** traffic increases.
        
        But sometimes:
        
        - Scaling takes 2–5 minutes.
        - Users may experience slow response during that time.
        
        Predictive Scaling solves this by:
        
        > 📈 Predicting traffic patterns in advance
        > 
        > 
        > 🚀 Launching instances before the spike happens
        > 
        
        **Step-by-step Flow:**
        
        CloudWatch collects historical metrics (CPU, load, request count).
        
        AWS analyzes patterns (daily, weekly traffic trends).
        
        AWS creates a traffic forecast.
        
        ASG launches required instances in advance.
        
        **Example** 
        
        Imagine you run a food delivery app:
        
        - Every day at 8 PM → traffic increases.
        - Every weekend → 2x traffic.
        - Every festival → massive spike.
        
        Predictive scaling learns this pattern and:
        
        👉 At 7:45 PM → launches extra instances
        
        👉 At midnight → scales down.
        
        ### **Scaling Cooldown**
        
        It is a **waiting period** after a scaling activity completes, during which the ASG temporarily **pauses additional scaling actions**.
        
                                                                   **default period :** 300 seconds.
        
        **Why Do We Need Cooldown?**
        
        Without cooldown:
        
        - CPU rises → Add instance
        - CPU still high (because instance not ready yet) → Add another instance
        - Over-scaling happens ❌
        
        Cooldown prevents this by:
        
        > ⏳ Waiting for the new instance to fully start and stabilise before making another scaling decision.
        > 
        
        **Step-by-step Example:**
        
        1. CPU > 70%
        2. CloudWatch triggers scaling policy
        3. ASG launches 1 new instance
        4. Cooldown period starts (e.g., 300 seconds)
        5. During cooldown → No additional scaling happens (waiting period)
        
        After cooldown ends → ASG can scale again if needed.
        

### Amazon CloudFront

**Amazon CloudFront** is a **Content Delivery Network (CDN)** service provided by AWS.

It helps you **deliver content (websites, APIs, videos, images, apps)** to users with:

- 🚀 **Low latency (fast loading)**
- 🌍 **Global availability**
- 🔒 **High security**
- 📈 **High performance**
- 216 point of presence globally.

**Why Do We Need CloudFront?**

Imagine:

- Your server is in **Mumbai (ap-south-1)**
- A user from **USA** opens your website

Without CloudFront:

👉 Request travels all the way to Mumbai → Slow response

With CloudFront:

👉 Content is served from the nearest **Edge Location in USA** → Faster response

### Edge Locations

- Data centers located worldwide
- Store cached copies of content
- Serve users from the nearest location

### Origin

The main source of content. It can be:

- 🗂️ **Amazon S3**
- 🖥️ **Amazon EC2**
- ⚖️ **Elastic Load Balancing**
- Any external HTTP server

**How CloudFront Works (Simple Flow)**

1. User requests website
2. Request goes to nearest **Edge Location**
3. If cached:
    - Served immediately
4. If not cached:
    - Fetch from Origin
    - Store in cache
    - Return to user

**Caching**

- CloudFront stores content for a period called **TTL (Time To Live)**
- After TTL expires → it fetches fresh content

**CloudFront +S3**

If you host a static website in S3:

- Make S3 bucket private
- Allow access only through CloudFront
- Use **Origin Access Control (OAC)**

👉 This increases security.

### CloudFront Geo Restriction

**Geo Restriction (Geo Blocking)** in CloudFront allows you to:

👉 **Allow or block users from specific countries** based on their **IP address location**.

**Why Do We Use It?**

- 🌎 Licensing restrictions (e.g., movies allowed only in India)
- ⚖ Legal compliance
- 🔐 Security reasons
- 🎯 Region-specific content delivery

**How It Works (Simple Flow)**

1. User sends request
2. CloudFront checks user's **IP address**
3. Determines user's **country**
4. Applies rule:
    - ✔ Allowed → Serve content
    - ❌ Blocked → Return 403 Forbidden
    
    ### Types:
    
    - **Allowlist (whitelist):**
        - Only selected countries can access content.
            
            Example:
            
            - Allow: India, USA
            - All other countries → Blocked
    - **Blocklist (blacklist):**
        - Block selected countries.
            
            Example:
            
            - Block: China, Russia
            - All other countries → Allowed
    
    ### CloudFront - Pricing:
    
    CloudFront edge locations all over the world.
    The cost of data out per edge locations varies.
    
    **How CloudFront Charges You?**
    
    CloudFront pricing is mainly based on:
    
    - **Data Transfer Out (DTO) to Internet**
        
        👉 You pay for **data delivered to users**
        
        👉 Price depends on:
        
        - Amount of data (GB/TB)
        - User location (region)
        
        📌 More expensive in:
        
        - South America
        - Australia
        
        📌 Cheaper in:
        
        - US
        - Europe
        - India
        
        **What is Price Class in CloudFront?**
        
        **Price Class** lets you control:
        
        👉 **Which edge locations CloudFront can use**
        
        👉 To reduce cost by limiting expensive regions
        
        More edge locations = Better global performance
        
        Fewer edge locations = Lower cost
        
        CloudFront provides 3 options:
        
        | Price Class | Edge Locations Used | Cost | Performance |
        | --- | --- | --- | --- |
        | **Price Class All** | All global edge locations | Highest | Best worldwide |
        | **Price Class 200** | Most regions (excludes most expensive) | Medium | Good |
        | **Price Class 100** | US, Canada, Europe only | Lowest | Limited global |

### Cache Invalidations

**Cache Invalidation** means:

👉 Removing cached files from CloudFront edge locations

👉 Before their TTL (Time To Live) expires

So users get **updated content immediately**.

**Why Do We Need It?**

Example:

- You update `logo.png` in S3
- CloudFront already cached old version
- Users still see old image

To fix this:

👉 Use **Invalidation**

CloudFront deletes cached copy

Next request → Fetches new file from origin

**How It Works (Simple Flow)**

1. File cached at edge location
2. You update file at origin
3. You create invalidation request
4. CloudFront deletes cached version
5. Next user request → Fetches new content

**How to Invalidate?**

You specify **Path(s)**:

Examples:

- `/index.html`
- `/images/logo.png`
- `/images/*`
- `/*` (invalidate everything)

### Unicast IP

**Unicast** means

👉 One sender → One receiver **(one server holds one IP address)**

It is the **normal IP communication** used on the internet.

**How It Works?**

A client sends request to a **specific server IP**

That request always goes to **that exact server**

Example:

Your EC2 server has IP: `13.x.x.x`

All requests go to that single machine

### Anycast IP

**Anycast** means

👉 One sender → Nearest server (all servers holds same IP address and the client is routed to nearest one).

Multiple servers share **the same IP address**.

Routing automatically sends user to the **closest location**.

### **AWS Global Accelerator (GA)**

It is a networking service that:

👉 Improves performance for global users

👉 Uses **Anycast IP addresses**

👉 Routes traffic through AWS global backbone network

It provides **static IP addresses** that never change.

**Why Do We Need It?**

Problem:

- Your application is hosted in Mumbai (ap-south-1)
- Users from USA access it
- Traffic goes over public internet → Slower

Solution:

👉 Global Accelerator routes traffic via AWS private global network

👉 Reduces latency

👉 Improves reliability

**How It Works (Simple Flow)**

1. AWS provides **2 static Anycast IP addresses**
2. User connects to nearest AWS edge location
3. Traffic enters AWS backbone network
4. Routed to optimal regional endpoint
5. Delivered to your application

Global Accelerator can route traffic to:

- **Amazon EC2**
- **Elastic Load Balancing**
- **Amazon EIP**
- **Application Load Balancer**
- **Network Load Balancer**

- Consistent Performance:
    - intelligent routing to lowest latency and fast regional failover
    - no issue with client cache
- Health Check:
    - Global Accelerator performs a health check for the application.
    - great for the disaster recovery.
    - helps make application global (failover less than 1 minute for unhealthy.)
    - If one region fails
    - Traffic automatically shifts to healthy region

**🔹 Global Accelerator vs CloudFront**

| Feature | Global Accelerator | CloudFront |
| --- | --- | --- |
| Layer | Layer 4 (TCP/UDP) | Layer 7 (HTTP/HTTPS) |
| Caching | ❌ No | ✅ Yes |
| Static IP | ✅ Yes | ❌ No |
| Use Case | APIs, gaming, real-time apps | Static content, websites |
| Anycast | ✅ Yes | ✅ Yes |

**When To Use What?**

📌 Use CloudFront:

Static content

CDN caching

Website acceleration

📌 Use Global Accelerator:

Real-time apps

Gaming

VoIP

API acceleration without caching

Need static IP

### Serverless

**Serverless** means you focus only on your code, and AWS manages the underlying servers, operating systems, and network layer. You don't need to worry about infrastructure management. (**no server management by you**)

👉 You do NOT manage servers

### AWS Lambda

**AWS Lambda** is **a serverless, event-driven compute service that lets you run code without configuring or managing servers**. You simply upload your code (as a ZIP file or container image), and AWS handles all the underlying infrastructure management, including capacity provisioning, automatic scaling, and maintenance.

- Run code without servers
- Run on demand
- Pay per execution time (milliseconds)
- free tier of 1,000,000 AWS Lambda requests and 400,000 GBs compute time.
- easy monitoring using AWS CloudWatch.
- increasing RAM will also increase CPU and network.

**Event-Driven:** Lambda functions run in response to specific events. These events can come from a variety of sources, such as:

- An image file being uploaded to an Amazon S3 bucket.
- An HTTP request made through Amazon API Gateway.
- Changes to data in an Amazon DynamoDB table.
- Scheduled events using Amazon EventBridge.

### **Lambda container image**

It is a package format that allows developers to deploy their AWS Lambda function code and dependencies using standard container tooling like [Docker](https://www.docker.com/), in addition to the traditional ZIP archive method.

### Cloud Front Functions

**CloudFront Functions** is a lightweight serverless feature of **Amazon CloudFront**

It allows you to run **small pieces of JavaScript code at AWS edge locations**.

👉 It runs **before the request reaches your origin server**
👉 Used for **simple request/response modifications**
👉 Extremely fast and low cost

**Where Does It Run?**

It runs at **CloudFront Edge Locations** during:

✅ Viewer Request

✅ Viewer Response

⚠ It does NOT run at origin request/response stage.

**Why Do We Use It?**

To modify:

URL, Headers, Cookies, Redirects, Basic authentication, A/B testing

Without touching:

EC2,ALB, Backend server

**How It Works (Simple Flow)**

User sends request

CloudFront receives it

CloudFront Function executes

Request is modified (if needed)

Forwarded to origin (or served from cache)

| Feature | CloudFront Functions |
| --- | --- |
| Language | JavaScript only |
| Speed | Microseconds |
| Cost | Very low |
| Network calls | ❌ Not allowed |
| AWS service access | ❌ Not allowed |
| Execution time | Very short |

👉 **CloudFront Functions = Lightweight & Ultra Fast**

👉 **Lambda@Edge = Powerful but heavier (deal with origin request & response)**

### **Lambda@Edge**

It is an extension of AWS Lambda that allows you to run code at **CloudFront edge locations**.
It lets you execute logic **closer to users**, before or after content is served.
It works together with Amazon CloudFront.

**Where Can It Run?**
Lambda@Edge can execute at 4 different stages:

| **Stage** | **What It Means** |
| --- | --- |
| Viewer Request | Before CloudFront checks cache |
| Viewer Response | Before response sent to user |
| Origin Request | Before request goes to origin |
| Origin Response | Before response cached |

👉 This gives more flexibility than CloudFront Functions.

**Example Use Case**

**Scenario:**

You want to check user subscription before serving content.

Steps:

1. User requests video
2. Lambda@Edge checks user in DynamoDB
3. If valid → allow
4. If not → return 403

This cannot be done using CloudFront Functions.

| Feature | Lambda@Edge |
| --- | --- |
| Language | Node.js, Python |
| AWS Service Access | ✅ Yes |
| Network Calls | ✅ Yes |
| Modify Origin Request | ✅ Yes |
| Cost | Higher |
| Latency | Slightly more than CF Functions |

| Cloud Front Functions use case | Lambda@Edge use case  |
| --- | --- |
| Cache key normalisation: Transform request attributes (headers, url, cookies, query) to create an optimal cache key. | Longer Execution time |
| Header Manipulation: insert/modify/delete HTTP headers in the request and response. | Adjustable CPU or Memory |
| URL rewrites or redirects | your code depends on 3rd library |
| Request authentication & authorisation: create and validate user created JWT tokens to allow/deny requests. | Network access to use external service for processing |

### Lambda in VPC

Lambda function is connected to your private network so it can **securely access resources inside that VPC** (like databases or internal services).

### AWS ROUTE 53

- **It is a scalable DNS that translates domain names into IP addresses and routes users to the correct servers.**
    - example: If a user types **`www.google.com`**, Route 53 finds the **IP address of the server** where the website is hosted and directs the user there.
    - **Route 53:** routes traffic to correct destination. DNS uses port 53.
- DNS is a collection of rules and records which helps clients understand how to reach a server through URLs.
- In AWS, the most common records are:
    
    
    | Record Type | Purpose |
    | --- | --- |
    | A | Domain → IPv4 |
    | AAAA | Domain → IPv6 |
    | CNAME | Alias to another domain |
    | Alias | URL to AWS resource |
- example: web browser→dns request to Route 53 (A)→ sends back IP to web browser.
- Route 53 can use:
    - public domain names you own (or buy)
    - private domain names that can be resolved by your instance in you VPCs
- Route53 has advance features such as:
    - Load Balancing
    - Health checks
    - Routing policy
- You pay $0.50 per month per hosted zone.
