[https://www.youtube.com/watch?v=Rnr5hp4njq0
- https://github.com/nityaboyapati99/AWS-Handbook/blob/main/AWS_SAA_Handbook.md
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

### EC2 volume types
EBS Volume types 
- 6 types
### SSD backed volumes ( for performance sensitive workloads)
    - gp3 (General Purpose SSD – latest)
      Best default choice for most workloads
      Balanced price + performance
      Baseline performance with ability to provision:
- IOPS (up to 16,000)
- Throughput (up to 1,000 MB/s)

Ideal for:
Web servers
Small/medium databases
Dev/test environments


gp2 : previous generation of gp3
performance tied to volume size
used gp3 instead unless you have legacy setups



- io2 (Provisioned IOPS SSD)
High-performance, mission-critical workloads
Very high durability (99.999%)
Up to 256,000 IOPS (with Block Express)


- io1
older version of io2
less durable and flexible


HDD backed volumes ( for through put focused workloads)

st1
Low cost, high throughput - intensive workloads
(throughput : amount of data successfully transferred with a specific time rate)
designed for frequently accessed.
Good for large, sequential workloads


sc1 (Cold HDD)
Lowest cost option
Designed for infrequently accessed data

NOTE:
gp3 → Default choice for most use cases
io2 → High-performance, critical workloads
st1 → Large sequential workloads
sc1 → Cold/archival data


### EBS Multi attach
- attach the same EBS Volume to multiple EC2 in the same AZ
- each instance has full read & write permissions to the high performance volume
- can attach up to 16 EC2 instance at a time


### EBS Encryption
EBS encryption ensures that data stored in an EBS volume is:

Encrypted at rest
Encrypted in transit between EC2 and EBS
Encrypted in snapshots and backups


Encryption: encrypt an unencrypted EBS volume
- create an EBS snapshot of the volume
- encrypt the EBS snapshot (using copy)
- create new ebs volume from the snapshot (the volume will also be encrypted)
- now you can attach the encrypted volume to the original instance.



### KMS key 
- A KMS key in Amazon EBS is the encryption key used to protect your data when you enable EBS encryption.


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

### Scaling & Availability

**Vertical Scaling** 
- Increase instance size
**Horizontal Scaling**
- Increase number of instances
    - Auto Scaling Group
    - Load Balancers 

**High Availability**
- Run instances for the same applications across multi AZs
    - Auto Scaling group multi AZ
    - Load balance multi AZ
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

If the response is not 200(OK), then the instance is unhealthy and ELB will not send traffic to the instance.

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

 **Cloud Front- Origins**
 - S3 bucket:
     - for distributing files and caching them at the edge
     - for uploading files to S3 through cloudfront
 - VPC origin:
     - for applications hosted in VPC private subnets.
     - private application Load balance/ network load balancer/ ec2 instance.

 
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
Anycast IP sends the traffice directly to Edge location.
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
- scaling is automated
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

### **Amazon RDS**

- RDS : Relational Database Service
- Instead of installing a database on your own server, AWS gives you a ready-to-use database.

Advantage over using RDS VS deploying DB on EC2

- RDS is a managed service:
    - continuous backups and restore to specific timestamps
    - Updates software (patching)
    - Scales storage and performance

**RDS storage auto scaling**

- helps to increase storage on  RDS DB instance dynamically.
- when RDS detects running out of database storage, it scales automatically.(avoid manual scaling)
- useful for application with unpredictable workloads.

**RDS Read Replicas for read scalability**

- copies of the database used to handle more read traffic and improve performance
- have one main database (primary DB).
- AWS creates copies (Read Replicas) of that database. These replicas are used only for reading data.

**Writes** (INSERT, UPDATE, DELETE) → go to the main DB
 **Reads** (SELECT) → go to Read Replicas
- This spreads the load and makes your app faster.

- Supports upto 15 read replicas.
- within AZ, Cross AZ , Cross region.
- Replication is ASYNC, so reads are eventually consistent
**example**: If many users are reading data (like viewing products, posts, etc.), one DB can get slow. Read Replicas handle those reads, so the main DB is not overloaded.
- RDS read replicas within the same region- don’t pay the fee. 
for cross region - fees are applicable

**RDS Multi AZ (Disaster Recovery)**

AWS creates two copies of your database:

- Primary DB (active)
- Standby DB (backup, in another Availability Zone)
- Your app connects only to the primary DB, AWS automatically copies data to the standby DB(synchronously) 
If the primary fails → AWS automatically switches to the standby DB.

**SYNC replication:** Data is written to both primary and standby at the same time.

**ASYNC replication:** Data is written to primary first, then copied later to replicas.

**note**: The Read Replicas be setup as Multi AZ for Disaster Recovery

**RDS from Single AZ to Multi AZ**

Single-AZ → one database in one data centre
 Multi-AZ → one primary DB + one standby DB in another zone

converting Single AZ -> Multi AZ

- Go to RDS Dashboard
- Select your database
- Click Modify
- Enable Multi-AZ deployment:
    - A snapshot is taken
    - A new DB is restored form the snapshot in a new AZ
    - Synchronisation is established between the two DBs.
- Save changes

**RDS Custom**

RDS Custom = Managed database + root/admin access
Normal RDS is fully managed, so You can’t access OS and  can’t install custom software.

RDS Custom can:

- Configure settings
- Access the operating system (SSH or SSH session manager)
- Install custom agents, tools, or patches
- Customise database settings deeply

Supported databases:

- Oracle
- SQL Server

### **Amazon Aurora**

Aurora = faster, more powerful version of MySQL/PostgreSQL in AWS

Key features:

- High performance
- Up to 5× faster than MySQL
- Up to 3× faster than PostgreSQL; Auto scaling storage
- Storage automatically grows (up to 128 TB) - High availability
- Data is copied across multiple Availability Zones
- Supports up to 15 Read Replicas
- Helps handle heavy read traffic
- Continuous backups to S3
- Self-healing storage system

**Aurora High availability and Read scaling**

- 6 copies of your data across 3 AZ:
    - 4 copies out of 6 needed for writes (4/6)
    - 3 copies out of 6 need for read (3/6)
    - self healing with peer to peer replication
    - storage is striped across 100s of volumes
- **One aurora instance takes writes (master)**
- automated failover for master in less than 30 seconds

**Aurora DB Cluster**

- shared storage volume (auto scaling from 16Gb to 256 Tb)
- writer endpoint pointing to the master (WRITES)
- reader endpoint connection load balancing (connected to replicas- READ)

**Aurora Replicas - Auto Scaling**

- automatically adds or removes read replicas based on demand. 
**example**:
    - You have an Aurora database cluster (1 writer + some readers).
    - AWS monitors load (like CPU or connections).
    - If traffic increases : it adds read replicas.
    - If traffic drops : it removes extra replicas.

**Aurora custom endpoints**

- manual grouping of replicas for targeted traffic routing.
- Instead of sending all read traffic to all replicas, you can control where queries go.

**Aurora Serverless**

- version of Amazon Aurora where you don’t manage database instances at all. 
 AWS automatically:
    - Starts the database
    - Scales capacity up/down
    - Can pause when not in use
    - good for infrequent, intermittent or unpredictable workloads
    - pay per second
    
    **RDS Backups**
    
    - automated Backups:
        - daily full backup of the database
        - transaction logs are backed-up by RDS every 5minutes.
        - ability to restore to any piont in time
    - Manual DB snapshots:
        - manually triggered by the user
        - retention of backup for as long as you want.

In a stopped RDS DB, you will still pay for storage.
If you plan on stopping it for long time, then take a snapshot and restore instead.

**Aurora Backups**

- automated backups
    - 1 to 35 days
    - point in time recovery in that timeframe.
- Manual DB snapshots:
    - manually triggered by the user
    - retention of backup for as long as you want.
    
    **RBS & Aurora restore options**
    
    - Restoring a RDS/ Aurora backup or a snapshot creates a new DB.
    - Restoring MySQL RDS DB from S3
        - create a backup of your on-premise database
        - store it on amazon s3
        - restore the backup file onto a new RDS instance running MySQL
    - Restoring MySQL Aurora cluster from S3
        - create a backup of your on-premises database using Percona XtraBackup
        - store the backup file on amazon S3
        - restore the backup file onto a new aurora cluster running MySQL
    
    **Aurora DB cloning**
    
    - create a new copy of an Aurora database cluster very quickly—without copying all the data.
    - faster than snapshot & restore.
    - uses copy-on-write protocol.
    
    **RDS & Aurora Security**
    
    - At rest encryption:
        - DB master & replicas are encrypted using **AWS KMS** - must be defined at launch time.
        - If the master is not encrypted, the read replicas cannot be encrypted.
        - To encrypt and un-encrypted DB, go through a DB snapshot & restore as encrypted.
    - **In-flight encryption:** Data is encrypted while traveling between your application and the database
    - uses SSL/TLS protocols
    - prevent man-in-the-middle attacks
    - IAM authentication: IAM roles connect to DB (instead of username/pass)

**RDS Proxy**

- allows apps to reuse and share DB connections established with the DB.
- Databases can struggle when there are too many connections. 
 Instead of every app opening its own DB connection:
    - RDS Proxy reuses connections reduces load on the database serverless, autoscaling. RDS proxy is never publicly accessible (must be accessed from VPC)

**Example:** 1000 users hit your app Without proxy → 1000 DB connections ❌ 
With proxy → maybe only 100 active connections ✅

### **ElastiCache**

-helps app run faster by storing frequently used data in memory (RAM) instead of fetching it from a database every time.
- service that gives you a very fast in-memory cache.
- caches are in-memory databases with high performance, low latency.
- helps reduce load/traffic

    ### **ElastiCache Solution Architecture - DB Cache**
      - Applications queries ElastiCache, if not available, get it from RDS and store in ElastiCache.
      - helps relieve load in RDS.
      - Cache must have an invalidation strategy to make sure only the most current data is used in there.

    ### **ElastiCache Solution Architecture - User Session Store**
    - Instead of storing user session data (like login info, cart, preferences) in app server or DB, it stores in ElastiCache (usually Redis).
   **How it works**
        - User logs in
        - Your app creates a session ID
        - Session data is stored in ElastiCache
        - Session ID is sent to the user (via cookie)
        - On next request:
            - App reads session ID
            - Fetches session data from ElastiCache

  Architecture: User → Load Balancer → App Servers → ElastiCache (Redis)

    ### **ElastiCache Redis VS Memcached**
  - Redis = powerful, feature-rich
  - Memcached = simple, lightweight cache
 | Feature           | Redis                            | Memcached                      |
| ----------------- | -------------------------------- | ------------------------------ |
| Data types        | Strings, lists, sets, hashes     | Only key-value (string)        |
| Persistence       | ✅ Yes (can save to disk)         | ❌ No                           |
| High availability | ✅ Replication + failover         | ❌ No native failover           |
| Scaling           | ✅ Cluster mode (sharding)        | ✅ Easy horizontal scaling      |
| Performance       | Very fast                        | Slightly faster for simple use |
| Use case          | Sessions, queues, real-time apps | Simple caching                 |
- failover: automatically switching to a backup system when the main system fails.
- Cluster node sharding: means splitting your data across multiple nodes so you can store more data and handle more traffic.
Use Redis if:
You need session storage
You want data persistence
You need advanced features (pub/sub, counters, queues)
You need high availability

Use Memcached if:
You only need simple caching
No need to save data permanently
You want a very lightweight setup

- If your app is complex → Redis
- If your need is basic caching → Memcached

    ### **ElastiCache - Cache Security**
- ElastiCache is usually placed inside a private network, so security is mainly about who can access it and how.
- runs inside a VPC
- acts like a firewall
- redis supports AUTH token
- data is encrypted while moving (TLS)
- data is stored in memory snasphots is encrypted


    ### **Patterns for ElastiCache**
- Cache-Aside (Lazy Loading)
    How it works:
    - App checks cache
    - If data is found → return it ✅
    - If not → fetch from DB ❌
    - Store in cache for next time
 use when data is read frequently.

- Write-Through: cache is updated along with database
      How it works:
      - App writes data
      - data goes to DB + cache together
  use when you want cache always up-to-date.

 - Write-behind: cache updates DB later (async)
       How it works:
       - App writes to cache
       - Cache updates DB after some time
    use when high write performance is needed

  - Session Store: store user sessions in cache
      - use when multiple app servers and need fast session access

   - Leaderboard/ Counter
    - Redis uses a data structure called a sorted set (ZSET).
    - each element has value-score.
    - keeps elements unique and maintains them sorted by score.
      
      How it works:
    - Add/update a user score
    - Redis inserts or updates the value
    - It automatically reorders ranking in real time
 
    - uses: Gaming leaderboard, rankings
 
- Cache-Aside → most common
Write-Through → consistent but heavier
Write-Behind → fast writes, some risk
Read-Through → simpler app logic
Session Store → user sessions
Leaderboard → real-time ranking

**AWS ROUTE 53**

**DNS**

- Domain Name system: translates the hostname into IP addresses.
- [www.google.com](http://www.google.com/) -> 172.216.13.45.14

**DNS Terminologies** :
**- Domain Registrar:** where you can buy a domain 
**- DNS record:** provide information about a domain

| Record Type | Purpose |
| --- | --- |
| A | Domain → IPv4 address |
| AAAA | Domain → IPv6 address |
| CNAME | Alias to another domain |
| Alias | Maps domain to AWS resource |
- **zone files:** file that stores all DNS records of a domain
- **Name server:** server that responds to DNS queries for a domain
- **Top level domain(TLD):** last segment of a domain 
example: .com, .org, .net, .gov, .edu
- **second level domain (SLD):** the part directly to the left of the TLD. 
example: in example.com -> example is SLD.
- **sub domain:** part of a larger domain. 
example: mail.google.com ->mail is sub domain
- **FQDN (fully qualified domain name):** complete domain name including all levels and ending with a dot.
    - example: [www.google.com](http://www.google.com/)
- **Protocol**: set of rules that defines how data is transmitted over a network

**How DNS Works** 
Check Cache → Browser looks for saved IP, if not then: 
Ask Resolver → If not found Root → TLD → Name Server → Find correct server Get IP → Name server returns IP Load Website → Browser connects using IP

- DNS finds IP address step by step, then loads website.
- **It is a scalable DNS that translates domain names into IP addresses and routes users to the correct servers.**
    - example: If a user types **`www.google.com`**, Route 53 finds the **IP address of the server** where the website is hosted and directs the user there.
    - **Route 53:** routes traffic to correct destination. DNS uses port 53.
- DNS is a collection of rules and records which helps clients understand how to reach a server through URLs.

**Route 53 Record**

- DNS record stored in amazon route 53 that tells how your domain should behave.
- In AWS, the most common records are:
    
    
    | Record Type | Purpose |
    | --- | --- |
    | A | Domain → IPv4 address |
    | AAAA | Domain → IPv6 address |
    | CNAME | Alias to another domain |
    | Alias | Maps domain to AWS resource |
- example: web browser→ dns request to Route 53 (A)→ sends back IP to web browser.
- Route 53 can use:
    - public domain names you own (or buy)
    - private domain names that can be resolved by your instance in you VPCs
- Route53 has advance features such as:
    - Load Balancing
    - Health checks
    - Routing policy

**Route 53 - Hosted Zone**

- container of records that define how to route traffic to a domain and its subdomain.
- A hosted zone = DNS “folder” for one domain Types of Hosted Zones
- **Public Hosted Zone:**
    - Controls how your domain is accessed on the internet
     Example: example.com website
- **Private Hosted Zone:**
    - Used inside a private network (VPC)
    - Not accessible from the internet
     Example: application.company.internal
- You pay $0.50 per month per hosted zone.

**Route 53 TTL (Time To Live):**

- It is the time a DNS record is stored in cache before it is refreshed. example: [www.example.com](http://www.example.com/) → 93.184.216.34 → TTL = 300 seconds 
This means:
    - Save result for 5 minutes
    - After 5 minutes → ask DNS again

**Route 53 CNAME vs Alias :**

- CNAM (Canonical Name):
    - Points one domain to another domain name 
    example: [www.example.com](http://www.example.com/) → example.com
    - Only for NON ROOT DOMAIN
- Alias:
    - Points a domain directly to AWS resources
     example: example.com → AWS Load Balancer / S3 / CloudFront
    - Works for both ROOT DOMAIN & NON ROOT DOMAIN
- **ROOT DOMAIN:** main domain name without any prefix 
example: example.com, google.com
- **NON ROOT DOMAIN:** A child part of the main domain
 example: [www.example.com](http://www.example.com/), mail.example.com

**Alias Record** It works like a CNAME, but more powerful 
Can point to:

- AWS Load Balancer
- S3 website
- CloudFront distribution
- Another domain
- Alias record is always of type A/ AAAA for AWS resource( IPv4/IPv6)
- you can't set the TTL
    
    **Alias Record Targets**
    
    - ELB
    - CloudFront distributions
    - API Gateway
    - S3 websites
    - VPC interface endpoints

**Route 53 - Routing Policy** Types

- Simple → Send traffic to one single resource(server)
- Weighted → Split traffic (% based) -example: 80% -> server A, 20% -> server B
- Latency → send user to the faster server
routes traffic to the AWS region that provides the lowest network latency.
    - example: India user-> India server, US user -> US server
- Failover → Switch to Backup if main fails
- Geolocation → routes traffic based on user’s location 
example: India user -> India server
- Multi-value → Returns multiple IPs
    - client picks one.
- Geo-proximity -> ability to shift more traffic to resources based on the defined bias.
- IP based routing -> routing is based on client's IP address.
- Health check -> monitors endpoints.

**Route 53 - Hybrid DNS**

- route 53 resolver automatically answers DNS queries for:
    - local domain names for EC2 instances
    - records in private hosted zones.
    - records in public name servers
- Hybrid DNS lets: resolving DNS queries between VPC (Route 53 resolver) and your network (other DNS resolvers)
    - On-prem systems resolve AWS private domains (like app.internal)
    - AWS resources resolve on-prem domains (like corp.local)
- *** section 11 important Recap of all concepts****

- **Stateless Web App:** does NOT store client session information on the server between requests.
    - Each request is treated as independent and complete on its own. 
    example: REST APIs, microservices
- **Stateful Web App:**  stores user session data on the server so it can “remember” previous interactions.
 example: shopping cart, banking web

### **Instantiating Applications Quickly**

- EC2 instances:
    - **use a golden AMI :** install applications, OS dependencies,.. beforehand and launch EC2 instance from the Golden AMI.
    - **bootstrap** using user data: dynamic configuration, use user data scripts. (initial setup)
    - **hybrid**: Golden AMI + user data (Elastic Beanstalk)
- **RDS DBs:**
    - restore from a snapshot: the db will have schemas and data ready.
- **EBS volumes:**
    - restore from a snapshot: the disk will already be formatted and have data.

### Beanstalk

- lets you **deploy, manage, and scale web applications automatically** without worrying about infrastructure.

**Elastic Beanstalk** is a service where you:

- Upload your application code
- AWS automatically handles:
    - Servers (EC2)/ Load balancing/ Auto scaling/ Monitoring

👉 You just focus on **writing code**, not managing servers.

| Feature | Beanstalk | EC2 |
| --- | --- | --- |
| Setup | Automatic | Manual |
| Control | Medium | Full |
| Scaling | Auto | Manual setup |
| Use case | Quick deployment | Full customization |

**Beanstalk Components:**

- **Application**: collection of elastic beanstalk components (version, environments, configurations,…)
- **Application version**: specific version of your code.
- **Environment**: actual running instance of your application.
    
    Types:
    
    - **Web Server Environment** → handles HTTP requests
    - **Worker Environment** → processes background jobs (via Amazon SQS)
- can create multiple envs (dev, test, prod,…)

**create application → upload version → launch environment → manage environment**

- **Environment Tier**
Defines the **type of environment**:
    - **Web Tier**
        - Handles web traffic (HTTP/HTTPS)
    - **Worker Tier**
        - Processes async/background tasks
- **Environment Configuration**
Settings that control environment behavior:
    - Instance type (t2.micro, etc.)
    - Scaling rules
    - Environment variables
    - Networking
    
    👉 You can modify config without redeploying code
    
- **Deployment Options**
Controls how updates happen:
    - **All at once** → fastest, but downtime
    - **Rolling** → updates in batches
    - **Rolling with additional batch** → safer
    - **Immutable** → new instances created (most reliable)

### Amazon S3

- scalable object storage device
- used to store and retrieve **any amount of data from anywhere on the web**.

Think of S3 like a **cloud storage drive**:

- You store files (images, videos, backups, logs)
- AWS manages storage, durability, and scaling

👉 Instead of folders, S3 uses **buckets + objects**

**Structure**

Bucket (like a folder)
     └── Object (file)
            ├── Data (actual content)
            ├── Metadata
           └── Key (unique name/path)

**Features**

- Scalable (unlimited storage)
- Versioning support
- Lifecycle management (auto move/delete data)
- Event triggers (Lambda integration)

**Use Cases**

- Store website assets (images, CSS, JS)
- Backup & restore data
- Log storage
- Static website hosting
- software delivery

**Amazon S3- Buckets**

- It is the **top-level container** used to store data (objects/files).
**Bucket** (like a folder)
     └── Object (file)
            ├── Data (actual content)
            ├── Metadata
           └── Key (unique name/path)
- buckets are defined at region level
- Each bucket has:
    - Unique name (globally)
    - Region
    - Access permissions
- Naming:
    - Shared Global Namespace: have a globally unique name (across all regions all accounts)
    - Account Regional Namespace: allows for ‘reuse’ of the same bucket name across regions.

**Amazon S3- Objects**

- it is **actual file/data** stored inside an S3 bucket.
- Each object consists of:
    - **Data** → actual content (image, video, file, etc.)
    - **Key** → unique name (path)
    Key is composed of prefix + object name
    example: s3://my-bucket/**my_file.txt**
                     s3://my-bucket/**my_folder/folder2/my_file.txt**
    - **Metadata** → extra information about the object

**Structure**:

Object
    ├── Key: images/profile.png
    ├── Data: (image file)
   └── Metadata:
        ├── Size: 2MB
        ├── Content-Type: image/png
       └── Last-Modified: date

**Features:**

- **Object Size Limits**
    - Minimum: **0 bytes**
    - Maximum: **5 TB per object**
    
    👉 For large files → use **Multipart Upload**
    
- **Metadata types**
    - **System metadata:** managed by AWS
    example: size, last modified date
    - **User metadata:** custom metadata you define
    example: **x-amz-meta-userid: 123**

**Key Features of S3 Objects**

- Versioning:
    - Multiple versions of same object, helps recover deleted/overwritten files
- Encryption
    - Data security options:
        - SSE-S3
        - SSE-KMS
        - Client-side encryption
- Lifecycle Management
    - Automatically:
        - Move objects to cheaper storage
        - Delete old versions
- Operations on Objects
    - Upload (PUT)
    - Download (GET)
    - Delete
    - Copy
    - Move (copy + delete)

 Example (Your Project)

For your **Ampcharge app**:

- Bucket: `ampcharge-data`
- Objects:
    - `users/101/profile.png`
    - `stations/45/image.jpg`
- S3 Object URL

Each object can be accessed via URL:

```
https://bucket-name.s3.region.amazonaws.com/key
```

👉 Example:

```
https://ampcharge-data.s3.ap-south-1.amazonaws.com/users/101/profile.png
```

**Amazon S3 - Security**

S3 security is about **protecting your data** by controlling:

- **Who can access it**
- **How it is accessed**
- **How it is encrypted**

**Access Control Mechanism**

- User based (IAM Policies):
    - Managed via AWS Identity and Access Management
    - Attached to **users, groups, roles**
    - Controls what actions they can perform
    example: Allow user to upload files to S3
- Resource based:
    - Bucket Policies:
        - Applied directly to a bucket
        - Controls **who can access the bucket**
         Used for: Public access/ Cross-account access
- Encryption:
    - Data at Rest:
        - **SSE-S3** → AWS-managed keys
        - **SSE-KMS** → Key management via AWS Key Management Service
        - **Client-side encryption**
    - Data in Transit
        - Use **HTTPS (SSL/TLS)**
        👉 Prevents data interception

**S3 bucket Policies:
JSON-based access control policy** attached directly to an S3 bucket to define **who can access what and how**.

- Controls access to:
    - Entire bucket
    - Specific objects (using key paths)
- Written in **JSON format**

Structure: 

```
{
  "Version":"2012-10-17",
  "Statement": [
    {
      "Effect":"Allow / Deny",
      "Principal":"* or specific user",
      "Action":"s3:GetObject / s3:PutObject",
      "Resource":"arn:aws:s3:::bucket-name/*"
    }
  ]
}
```

- effect: grant access/ block access
- principal: who gets access (specific IAM user)
- actions: what actions allowed (read/ upload/ delete)
- resource: which bucket/ object

**Example 1: Public Read Access**

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-bucket/*"
    }
  ]
}
```

👉 Anyone can view files (used for static websites)
note: principal is ‘*’ means accessible to everyone

**Example 2: Allow Only Specific User**

```
{
  "Effect":"Allow",
  "Principal": {
    "AWS":"arn:aws:iam::123456789012:user/Pranav"
  },
  "Action":"s3:*",
  "Resource":"arn:aws:s3:::my-bucket/*"
}
```

- principal is set to specific user.

**Example 3: Restrict by IP Address**

```
{
  "Effect":"Deny",
  "Principal":"*",
  "Action":"s3:*",
  "Resource":"arn:aws:s3:::my-bucket/*",
  "Condition": {
    "IpAddress": {
      "aws:SourceIp":"192.168.1.0/24"
    }
  }
}
```

**Static Website Hosting**

S3 can host **static websites** which has no backend/server logic 

- You upload frontend files to an S3 bucket
- S3 serves them over HTTP as a website

**Working**

User → Browser → S3 Bucket → Static Files (HTML/CSS/JS)

- User requests a page
- S3 returns the file directly

**Steps to Host Website on S3**

1. Create Bucket

- Bucket name must match domain
 Example: `my-website.com`

2. Enable Static Website Hosting

- Go to bucket → Properties
- Enable:
    - **Static website hosting**
    - Set:
        - Index document → `index.html`
        - Error document → `error.html`

3. Upload Files

- Upload:
    - `index.html`
    - CSS, JS, images

4. Set Bucket Policy (Public Access)

```
{
  "Version":"2012-10-17",
  "Statement": [
    {
      "Effect":"Allow",
      "Principal":"*",
      "Action":"s3:GetObject",
      "Resource":"arn:aws:s3:::my-website.com/*"
    }
  ]
}
```

Makes files publicly accessible (principal : *)

5. Access Website

You get a URL like:

```
http://my-website.s3-website-region.amazonaws.com
```

**short ans:** Create a bucket, enable static website hosting, upload files, and configure bucket policy for public read access.

**Amazon S3- versioning**

**S3 Versioning** allows you to **keep multiple versions of the same object** in a bucket.

 It protects your data from:

- Accidental deletion
- Overwriting files

When versioning is enabled:

- Every time you upload/update a file → a **new version** is created
- Old versions are **not deleted**

**How It Works?**

Each object gets a **Version ID**:

file.txt
    ├── VersionId: A1 (old)
    ├── VersionId: B2 (old)
   └── VersionId: C3 (latest)

 By default, latest version is returned

**Delete Behavior** 

When you delete an object:

It is **NOT permanently deleted**
S3 adds a **Delete Marker**

file.txt
    ├── v1
    ├── v2
   └── Delete Marker (latest)

File appears deleted, but old versions still exist

**Amazon S3-  Replication (versioning + IAM role)**

- automatically **copies objects from one bucket to another** (same or different region).
- must enable versioning in source and destination buckets.
- copying in asynchronous.
- must give IAM permission to S3.
- Used for: Backup, Disaster recovery, Low-latency accessTypes of Replication

**Types of Replication**

**1. Same-Region Replication (SRR)**

- Copies data **within the same AWS region**

👉 Use case:

- Compliance: following rules set by organisation.
- Log aggregation: collecting logs from multiple places and storing them in one central place.

**2. Cross-Region Replication (CRR)**

- Copies data **to a different region**

👉 Use case:

- Disaster recovery
- Global users (faster access)

**How It Works**

```
Source Bucket → Replication Rule → Destination Bucket
```

- You upload an object to source
- S3 automatically copies it to destination

**note:**

- After you enable replication, only new objects are replicated.
- you can replicate existing objects using S3 batch replication.

For DELETE operations

- can replicate delete markers from source to target
- deletions with a version ID are not replicated.

There is no ‘chaining’ of replication:

- If bucket 1 has replication into bucket 2, which has replication into bucket 3.
- then objects created in bucket 1 are not replicated to bucket 3.

| Feature | Replication | Backup |
| --- | --- | --- |
| Timing | Automatic | Manual/Scheduled |
| Regions | Same/Different | Usually same |
| Use case | High availability | Long-term storage |

**Amazone S3 - Storage Classes**

- define **how your data is stored, accessed, and priced**.

Storage Class

- Frequently Access
    - S3 Standard
    - S3 express one zone
- Infrequently Access
    - S3 Standard IA
    - S3 Express one zone IA
- Automatically Optimise
    - S3 Intelligent Tiering
- Rarely Access
    - Glacier instant retrieval
    - Glacier deep archive
    - Glacier flexible retrieval

Types of Storage Class

| Storage Class | Access | Cost | Retrieval Time | Use case |
| --- | --- | --- | --- | --- |
| Standard | Frequent | High | Milliseconds | website, apps |
| Intelligent-Tiering | Variable | Medium | Milliseconds |  |
| Standard-IA | Infrequent | Lower | Milliseconds | backups, disaster recovery |
| One Zone-IA | Infrequent, stored in single AZ  | Cheaper | Milliseconds | re-creatable data   |
| Glacier | Rare | Very Low | Minutes–Hours | long time archives |
| Deep Archive | Very Rare | Lowest | Hours | old backups |

![image.png](attachment:507f631a-a15c-469e-900f-a6dbf00419e1:image.png)

Lifecycle Example 

```
Day 0 → Standard
Day 30 → Standard-IA
Day 90 → Glacier
Day 365 → Deep Archive
```

Automatically reduces cost over time

Example:

- User images → **Standard**
- Old logs → **Glacier**
- Backups → **Standard-IA**

**S3 Express one zone**

- **high-performance storage class** designed for **ultra-low latency and very high request rates**—much faster than standard S3
- stores data in single AZ
- handles millions of request per second
- upto 10x better performance than S3 standard
- high durability (99.9999999%) and availability (99.5%)

Architecture Difference

**Normal S3**

```
Data → Multiple AZs (high durability)
```

**S3 Express One Zone**
```
Data → Single AZ (high speed)
```


| Feature | S3 Standard | S3 Express One Zone |
| --- | --- | --- |
| Latency | Milliseconds | Lower (faster) |
| Storage | Multi-AZ | Single AZ |
| Durability | Very high | Lower |
| Use case | General storage | High-performance apps |

**Amazon S3 - Lifecycle Rules**

 **automatically manage objects over time**—moving them to cheaper storage or deleting them.

**Goal**: Reduce cost + automate data management

**Types of lifecycle actions**

- **Transition Action**: Move objects to cheaper storage classes:
    - Standard → IA
    - IA → Glacier
    - Glacier → Deep Archive

![image.png](attachment:2ec3c7e3-6bd5-48d1-aebc-230c3b710542:image.png)

- **Expiration Actions**
    - Permanently delete objects after a time
    Example: Delete logs after 1 year
    can be used to delete older version of files (if versioning is enabled)

Rules can be applied based on

- Prefix (folder like):
    - logs/
    - images/
- Tags:
    - type=backup
    - env=prod

**Example Lifecycle Policy (JSON)**

```
{
  "Rules": [
    {
      "ID":"MoveToGlacier",
      "Filter": { "Prefix":"logs/" },
      "Status":"Enabled",
      "Transitions": [
        {
          "Days":30,
          "StorageClass":"GLACIER"
        }
      ],
      "Expiration": {
        "Days":365
      }
    }
  ]
}
```

**Amazon S3 analytics -Storage class analysis**

- helps you decide when to transition objects to right storage class.
- determine the optimal timing for moving obejcts between storage tiers effectively.
- recommendations for standard and standard IA
- does not work for one zone IA or glacier
- report is updated daily


**Amazon S3 -Requestor Pays**

Normally, the bucket owner pays for:

- Data storage
- Data transfer out
- Requests (GET, PUT, etc.)

With Requester Pays enabled:

- The requester pays for data transfer and request costs
- The bucket owner still pays for storage

When it’s useful
- Sharing large public datasets (e.g., research, logs, archives)
- Preventing unexpected bills when many users download data
- Open data platforms where users are expected to bear access costs


**Amazon S3 - Event Notifications**
- let you automatically react when something happens in an S3 bucket—like a file upload, deletion, or restore.
- They trigger downstream services when specific events occur in a bucket.
- Common event types:
    - s3:ObjectCreated:* → file uploaded (PUT, POST, COPY)
    - s3:ObjectRemoved:* → file deleted
    - s3:ObjectRestore:* → object restored from Glacier
    - s3:Replication:* → replication status changes
 
- S3 can send events to:
    - AWS lamda: run serverless code.
    - Amazon SNS: push notifications.
    - Amazon SQD: queue for asynchronous processing
    - Amazon Event bridge: advanced event routing (advanced filterin options with JSON rules )
 
- Example use cases
Automatically resize images after upload (Lambda)
Send alerts when files are deleted (SNS)
Process logs asynchronously (SQS)
Trigger workflows or pipelines (EventBridge)

- How it works (simple flow)
File is uploaded to S3
S3 detects the event
Notification is sent to the configured destination
Destination service processes it

- note: Event Notifications need IAM permissions.

**Amazon S3- Baseline Performance**
- default throughput and request scaling behavior you get from S3 without any special tuning.

- Request rate performance

- Per prefix (folder-like path), S3 supports at least:

    - 3,500 PUT/COPY/POST/DELETE requests per second
    - 5,500 GET/HEAD requests per second

-  And you can have unlimited prefixes, so you can scale horizontally by spreading objects across prefixes.
-  More parallel requests + more prefixes = more performance

  **S3 Performance**
  - Multi-part upload:
      - recommend for files > 100mb, must use for files > 5GB.
      - can help parallelize uploads
    multi part upload: Instead of uploading one big file:
        - Break it into pieces
        - Upload pieces at the same time
        - S3 joins them into one file
- S3 Transfer acceleration:
    - Instead of sending data directly to S3:
        -  Your data goes to the nearest AWS edge location
        - Then travels on AWS’s fast private network to S3
     
- S3 Byte-Range fetches:
    - let you download only a specific part of a file instead of the whole object.
 
**Amazon S3- Batch Operations**
- perform bulk operations on existing S3 objects with a single request
example:
    - modify object metadata & properties.
    - copy objects between S3 buckets.
    - encrypt un-encrypted objects.
    - restore objects from S3 glaciers.
- use S3 inventory to get object list and use Athena to query and filter objects.


**Amazon S3 - Storage Lens**
helps you analyze and monitor how your S3 storage is being used.
- It gives you a dashboard + metrics about your S3 usage
- So you can optimize cost, security, and performance


- Metrics:
    - Summary Metrics:
      - general insights about your S3 storage.
      - use cases: identify the fastest growing buckets and prefixes.
    - Cost optimization metrics:
        - provide insights to manage and optimize your storage costs.
        - uses cases: identify buckets with incomplete multipart uploaded older than 7 days.
     
      - Data protection metrics:
          - provide insights for data protection features.
          - use cases: identify the buckets that aren't following data protection best practices.
       
        - Access management metrics:
            - provide insights for S3 object ownership
         
        - Event metrics:
            - provide insights for S3 event notifications
        - Performance metrics:
            - provide insights for S3 transfer acceleration  
        - Activity metrics:
            - provide insights about your storage is requested 
        - Detailed Status code metrics:
            - provide insights for HTTP status codes. 

### **Amazon S3 - Object Encryption**
- protecting your data (files) by encrypting it when stored in S3.
- object in S3 buckets can be encrypted using 1 of 4 methods

- Server-Side Encryption:
    -  encryption is handled by AWS.
        - SSE - S3:
            - AWS manages keys automatically
            - encryption type is AES-256.
            - object is encrypted server side.
            - must set header "x-amz-server-side-encryption":"AES256"
            - enabled by default for new buckets and new objects.
        - SSE-KMS:
            - more control over keys.
            - managed by AWS KMS (Key management service).
            - can track and manage access.
            - object is encrypted server side.
            - must set header "x-amz-server-side-encryption":"aws:kms"
            - KMS limitation:
                - when you upload, it calls the GenerateDataKey KMS API.
                - when you download, it calls the Decrypt KMS API.
                - count towards the KMS quota per second. (5k,10k,30k req/s based on region).
                - you can request a quota increase using the service quotas console.


        - SSE-C:
            - provide your own encryption key.
            - AWS does not store the key.
            - encryption key is managed by customer outside the AWS.
         
    - Client Side encryption:
        - You encrypt the file before uploading to S3
        - You decrypt the file when retrieving from S3
        - You manage everything (keys + encryption)

    - Encryption in transit (SSL/TLS)
        - encryption in flight is also called SSL/TLS
        - amazone S3 exposes 2 endpints:
            - HTTPS Endpoint: encryption in flight.
            - HTTP Endpoint: non encrypted.
        - HTTPS is mandatory for SSE-C
     
- Force encrytion in Transit aws:SecureTransport:
    - Allow requests only if they use HTTPS
    -  Block any unencrypted (HTTP) access


### S3 CORS

- Cross origin resource sharing
- origin= scheme(protocol)+host(domain)+port
- if a client make a Cross origin request on our S3 bucket, we need to enable the correct CORS headers.

  Quick model:
- origin: who is calling (your frontend)
- methods: what they can do (GET,PUT,DELETE,...)
- headers: waht they can send
- s3 cors: premission rules

### S3 MFA Delete
- MFA (Multi factor authentication): force uses to generate a code on a device before doing improtant operations on S3
- MFA Will be required to:
    - permanently delete an object version
    - suspend versioning on the bucket
- MFA won't be required to:
    - enable versioning
    - list deleted versions.
- to use MFA delete, versioning must be enabled on the bucket.
- only the bucket owner (root account) can enable/disable MFA delete.


### S3 Access logs

- They are records of every request made to your S3 bucket.
- helpful in auditing, debug

- How to enable S3 access logs:
    - go to your bucket in AWS
    - open properties
    - scroll to server access logging
    - enable it
    - choose a target bucket (where logs will be stored)
- Amazon S3 can generate log files showing:
    - who accessed objects
    - request type
  - thes logs are stored as text files in another s3 bucket.
  - normally these logs are hard to read manually.
  - athena lets you:
      - query logs using SQL
      - search specific events
      - generate reports
      - detect suspicious activity
    - without moving data from S3.  
### Amazon S3- Pre signed URLS
- its a temporary, secure link that lets someone access a private S3 object without AWS credentials.
- expiry: you set a time limit (eg. 5min, 1hr, 7days max with SDKs)
    after that link stops working
- generate pre-signed URLs using S3 console, AWS CLI or SDK
- users give a pre-signed URL inherit the permission of the user that generated the URL for GET/PUT


**S3 Glacier Vault Lock**

- It's a feature that lets you lock a policy on a vault so it cannot be changed.
- it ensures data cannot be deleted or modified before a certain time.
- eg: financial regulations, healthcare data retention
- adopt Write Once Read Many model
- **S3 Object Lock:** versioning must be enabled
    - adopt a WORM model
    - once saved, this file is locked- no one can change or delete it.
    - Retention modes:
        - **Governance mode:**(user with permission can delete/modify)
            - most users can't overwrite or delete an object version or alter its lock settings.
            - some users have special permissions to change the retention or delete the object
        - **Compliance mode:** (no one can delete/modify)
            - object versions can't be overwritten or deleted by any user, including the root user.
            - object retention modes can't be changed, and retention periods can't be shortend.
        - **Retention period:**
            - protect the object for a fixed period; it can be extended. until the defined period - no delete, no overwrite.
        - **Legal Hold:**
            - protect the object indefinitely, independent from retention period.
            - no expiry date.
            - must be manually removed.

**S3 Access Points**

- An **Access Point** is like a **custom entry point (URL)** to an S3 bucket with its own permissions.
- Instead of using one bucket policy for everyone, you create **multiple access points**, each with different access rules.

**Example**

You have one S3 bucket: `my-data-bucket`

Create:

- Access Point 1 → for App A (read-only)
- Access Point 2 → for App B (read-write)

👉 Both use the same bucket but **different permissions**

**s3 access point - VPC origin**

- You can **access your S3 bucket only from inside a specific VPC**, not from the public internet.
- **VPC Origin = Restrict access to a Virtual Private Cloud**
- So, the access point will **only accept requests coming from that VPC**.

**How it works**

- You create an S3 Access Point
- Set **Network Origin = VPC**
- Attach it to a specific **Amazon VPC**
- Access happens via a **VPC Endpoint**

👉 No internet access allowed
**S3 Object Lambda**
Amazon S3 Object Lambda lets you modify the data returned by S3 GET requests using a Lambda function, without changing the original object.

- Think of it as a “middleman” that can transform your files on-the-fly.
-  Example:
- You have a file in S3: example.txt containing: Hello world!
    - You create an S3 Object Lambda with a Lambda function that converts text to uppercase.
`    - When someone GETs example.txt through the Object Lambda endpoint, they see: HELLO WORLD!
…but the file in S3 stays unchanged.


### AWS Snowball

- it is a physical data transport device used to transfer large amounts of data into and out of AWS securely and quickly.
- Instead of transferring terabytes or petabytes over the internet, AWS ships a secure device to your location.

**Why Snowball is Used**

- Internet transfer can be slow
- Large data uploads may take weeks or months
- Snowball provides:
    - Faster transfer
    - Secure encryption
    - Offline migration
    - Lower network cost

**How It Works**

1. Order Snowball device from AWS
2. AWS ships the device to you
3. Connect device to your system/network
4. Copy data into the device(snowball device)
5. Ship device back to AWS
6. AWS uploads data to services like:
    - Amazon S3
    - Glacier
    - EBS

**Types of Snow Family**

**1. Snowball Edge**

- Storage + compute capabilities
- Used for: Data migration, Edge computing, Local processing

**2. Snowcone**

- Small portable device
- Good for remote locations
- Lightweight

**3. Snowmobile**

- Massive truck-sized data transfer system
- Transfers exabytes of data

**Example :** A company wants to move **500 TB** of backup data to AWS.

Uploading through internet may take months.

Using Snowball:

- AWS sends device
- Company copies data locally
- Ships it back
- AWS uploads data quickly

**Simple Comparison**

| Service | Size |
| --- | --- |
| Snowcone | Small |
| Snowball Edge | Medium/Large |
| Snowmobile | Extremely Huge |

### Amazon FSx

- It is a fully managed file storage service in AWS that provides high-performance file systems for different workloads.
    
    AWS handles:
    
    - Setup
    - Maintenance
    - Scaling
    - Backups
    - Patching
    
    **Types of Amazon FSx**
    
    **1. FSx for Windows File Server:**
    
    - Native Windows file system
        
        Supports:
        
        - SMB protocol: file sharing
        - Active Directory
        - NTFS permissions: File/folder-level access control
        
        **Example:** A company has employees using Windows systems and wants a shared company folder.
        
        **Solution:**
        Use Amazon FSx for Windows File Server
        Employees connect using SMB
        Access controlled through Active Directory
        
    
    **2. FSx for Lustre**
    
    - Very high-speed file system: **Millions of IOPS and GB/s throughput**
    - Lustre= Linux+cluster
    - It is designed for workloads that need:
        - Extremely fast storage
        - Low latency
        - Massive throughput
    - Designed for:
        - Machine Learning
        - HPC (High Performance Computing)
        - Big data analytics
    
    **Integration with S3**
    
    Amazon S3 integration is a major feature.
    
    You can:
    
    - Import data from S3 into FSx Lustre
    - Process data at high speed
    - Export results back to S3
    
    **Example:** A company trains AI models on petabytes of image data stored in S3.
    
    **Solution:**
    
    - Import data into Amazon FSx for Lustre
    - Train models with high-speed access
    - Store outputs back into S3

**FSx file system deployment Options**

- **Scratch file system:**
    - Temporary storage
    - data is not replicated
    - high performance
    - best for:
        - Data processing jobs
        - Video rendering
        - Machine learning training
    
    **Example:** A company processes log files for 5 hours daily.
    After processing, data is deleted.
    
- **Persistent file system:**
    - Long term storage
    - data is replicated within in same AZ.
    - replace failed files within minutes
    - Best For
        - Production HPC systems (HPC-high performance computing)
        - Continuous ML workloads
    
    **Example:** A research company stores scientific simulation data continuously for months.
    
    → Persistent file system is suitable.
    
    Choose:
    
    - **Scratch** when speed and low cost matter more than durability
    - **Persistent** when reliability and long-term storage are important

**FSx for NetApp ONTAP**

- it is a data storage OS.
- it provides enterprise-grade storage features for:
    - Linux
    - Windows
    - macOS environments
- file system compatible with NFS, SMB, iSCSI protocol.
- Supports NetApp features:
    - Snapshots
    - Cloning
    - Compression
    - De-duplication
- Works with:
    - Linux , windows, mac, VMware cloud on AWS, Amazon EC2, ECS and EKS
- Storage shrinks or grows automatically.

**Amazon FSx for OpenZFS**

- managed OpenZFS file system on AWS.
- file system compatible with NFS(v3,v4,v4.1,v4.2)
- snapshot, compression, low-cost.

### Storage Gateway

- it is a hybrid cloud storage service  that connects on-premises environments with AWS cloud storage.
- bridge between on-premises data and cloud data.
- use cases:
    - disaster recovery
    - backup & restore
    - on-premise cache & low latency file access.

**Why Storage Gateway is Used**

Organizations may:

- Have on-premises applications
- Want cloud backups
- Need hybrid storage
- Require low-latency local access

**Types of Storage Gateway:**

- **S3 File Gateway:**
    - Provides file-based access using:
        - NFS
        - SMB
    - most recently used data is cached in file gateway.
    - bucket access using IAM roles for each file gateway.
    
    Stores files in:
    
    - Amazon S3
    
    Used For
    
    - File sharing, Backups
- **Volume Gateway:**
    - Provides block storage using iSCSI.
    - backed by EBS snapshots which can help restore on-premises volumes.
    - two modes:
        - Cached volumes: Main data in AWS, cached locally
        - Stored volumes: Main data on-premises, backups in AWS
    
    Used For
    
    - Backup solutions
    - Disaster recovery
- **Tape Gateway:**
    - Replaces physical tape backups with virtual tapes stored in AWS.
    - Stores data in: S3, Glacier

**File Gateway:** files in on-premise connected via NFS,SMB to file gateway

**Volume Gateway:** Application servers in on-premise connected via iSCSI to volume gateway

**Tape Gateway:** Backup applications in on-premise connected via iSCSI vTL to tape gateway.

| Feature | Storage Gateway | Snowball |
| --- | --- | --- |
| Purpose | Continuous hybrid storage | Large offline data transfer |
| Connectivity | Online | Offline shipping device |
| Use Case | Daily backups & access | Massive data migration |

### AWS Transfer Family

- used for secure file transfers into and out of AWS storage services.
- supported protocols:
    
    
    | Protocol | Full Form |
    | --- | --- |
    | SFTP | SSH File Transfer Protocol |
    | FTPS | File Transfer Protocol Secure |
    | FTP | File Transfer Protocol |
- pay per provisioned endpoint per hour + data transfers in GB.
- Files transferred through AWS Transfer Family can be stored in:
    - Amazon S3
    - Amazon Elastic File System

**Why Use AWS Transfer Family**

Many organizations already use:

- FTP servers
- SFTP clients
- Legacy file transfer systems

AWS Transfer Family allows them to:

- Continue using existing protocols
- Move storage to AWS
- Avoid managing file transfer servers

**Example**: A company exchanges files daily with partners using SFTP.

**Solution**:

- Use AWS Transfer Family
- Partners continue using SFTP
- Files stored directly in S3

![image.png](attachment:69bb1abb-682b-4689-b196-7c54c00aebc4:image.png)

| Feature | AWS DataSync | AWS Transfer Family | AWS Snowball |
| --- | --- | --- | --- |
| Purpose | Automated data transfer & sync | Secure file transfer using FTP/SFTP | Large offline data migration |
| Transfer Type | Online | Online | Offline |
| Main Use | Sync/migrate storage data | Exchange files with users/partners | Bulk migration of huge datasets |
| Protocols | NFS, SMB, HDFS | FTP, FTPS, SFTP | Physical device copy |
| Internet Required | Yes | Yes | Not required for transfer |
| Best For | Hybrid cloud sync | Secure file exchange | TB/PB-scale migration |
| Data Movement | Automated synchronization | User-based file uploads/downloads | Physical shipment |
| Recurring Transfers | Yes | Yes | No |
| Scale | GBs to TBs | Files and business transfers | TBs to PBs |
| Physical Device | No | No | Yes |
| Common Destination | S3, EFS, FSx | S3, EFS | S3, Glacier |

### AWS Integration & Messaging

- two types:
    - **Synchronous Communications (application to application):**
        - method where one service/application sends a request and waits immediately for the response before continuing.
    - **Asynchronous/ Event based Communications (application to queue to application):**
        - method where a service sends a message/request and does **not wait immediately** for the response.
        - Sender → Message Queue → Receiver

| Service | Purpose |
| --- | --- |
| Amazon SQS | Queue-based messaging |
| Amazon SNS | Pub/Sub notifications |
| Amazon EventBridge | Event routing |
| AWS Lambda | Event processing |
| AWS Step Functions | Workflow automation |

### **Amazon SQS (Simple Queue Service)**

- It enables applications and services to communicate asynchronously by sending messages through queues.
- SQS helps:
    - Decouple applications
    - Store messages temporarily
    
    **How SQS Works**
    
    ```
    Producer → SQS Queue → Consumer
    ```
    
    - Producer: who sends messages.
    - Consumer: who reads and processes messages.
    
    **Steps**
    
    1. Producer sends message to queue
        1. Producing messages: using SDK (SendMessage API)
    2. Message stored safely in SQS
    3. Consumer retrieves and processes message
    4. Message deleted after processing
    
    **Amazon SQS-Standard Queue**
    
    - used to decouple applications
    - unlimited throughput, unlimited no of messages in queue
    - retention of messages in queue:
        - default: 4days
        - maximum: 14 days
    - low latency
    - can have duplicate messages
    - At-least-once delivery: A message is never lost, but it may sometimes be delivered multiple times (duplicates can occur).
    
    **Amazon SQS- Security**
    
    - **Encryption**:
        - In flight encryption using HTTPS API
        - At-rest encryption using KMS keys
        - client-side encryption if the client wants to perform encryption/decryption itself
    - **Access controls :** IAM policies to regulate access to the SQS API
    - **SQS access policies:**
        - useful for cross-account access to SQS queues.

**SQS- Message visibility Timeout**

- after a message is polled by a consumer, it become invisible to other consumers.
- by default, the ‘message visibility timeout’ is 30sec means that message has 30sec to be processed.
- if a message is not processed within the visibility timeout, it will be processed twice.
- a consumer could call the **ChangeMessageVisibility** API to get more time
- if visibility timeout is high, and consumer crashes, re-processing will take time.
- if visibility timeout is too low we may get duplicates.

**SQS- Long polling**

- the consumer waits for a period of time for messages to arrive instead of getting an immediate empty response.
- the wait time can be between 1sec-20sec
- long polling can be enabled at the queue level or at the API level using **WaitTimeSeconds**.

**SQS- FIFO Queues**

- Messages are processed in the exact order they are sent.
- **First-In-First-Out ordering**
- **Exactly-once message processing (** by removing duplicates using Deduplication ID **)**
- FIFO queues use:
    - Message Group IDs
- Messages in the same group:
    - Processed sequentially and in order
- Different groups:
    - Can process in parallel
- no duplicates allowed.

### **Amazon Simple Notification Service (SNS)**

- It is fully managed **publish/subscribe (Pub/Sub)** messaging service
- used to send messages or notifications to multiple subscribers simultaneously. (One message can be delivered to many receivers.)

**How SNS Works**

- Publisher sends message to an SNS topic
- SNS distributes the message
- All subscribers receive the notification

| Component | Description |
| --- | --- |
| Publisher | Sends messages |
| Topic | Communication channel |
| Subscriber | Receives messages |

SNS can send notifications to:

| Subscriber Type | Example |
| --- | --- |
| Email | Email alerts |
| SMS | Mobile notifications |
| HTTP/HTTPS | Web applications |
| Lambda | Serverless processing |
| SQS | Queue processing |
| Mobile Push | App notifications |
- the **producer** does not send separate messages to every receiver.
    - Instead:
    
    ```
    Producer → SNS Topic
    ```
    
    The producer sends the message only once to an SNS topic.
    
- Every subscriber connected to that topic receives a copy of the message.
    - **Example**:
    
    ```
    SNS Topic
     ↓     ↓      ↓
    Email  SQS   Lambda
    ```
    
    If producer sends:
    
    ```
    "Order #101 placed"
    ```
    
    Then:
    
    - Email subscriber gets it
    - SQS queue gets it
    - Lambda function gets it
- up to 12,500,000 subscriptions per topic.
- 100,000 topics limit.

**Amazon SNS- Security**

- **Encryption**:
    - In flight encryption using HTTPS API
    - At-rest encryption using KMS keys
    - client-side encryption if the client wants to perform encryption/decryption itself
- **Access controls :** IAM policies to regulate access to the SNS API
- **SQS access policies:**
    - useful for cross-account access to SNS topics.

**SNS and SQS Fan-Out Pattern**

The **Fan-Out Pattern** in AWS is a messaging architecture where:

- One message is sent to an SNS topic
- SNS distributes copies of the message to multiple SQS queues

This allows multiple services to process the same event independently.

**How It Works**

- Producer sends one message to SNS topic.
- SNS creates copies of the message.
- Each SQS queue receives its own copy.
- Different services process messages independently.

**Why Use Fan-Out Pattern?**

**Without fan-out:** Producer must send separate messages to every service.

**With fan-out:** Producer sends only once.

SNS handles distribution automatically.

### Amazon Kinesis Data Stream

- it is a real-time data streaming service.
- used to collect, process, and analyse streaming data continuously in real time.
- Streaming data means data generated continuously, such as:
    - Application logs
    - Website clicks
    - IoT sensor data
    - Video streams
    - Financial transactions

| Component | Description |
| --- | --- |
| Producer | Sends streaming data |
| Stream | Stores streaming records |
| Consumer | Reads and processes data |
- retention between up to 365 days.
- ability to reprocess data by consumers
- data can’t be deleted from kinesis (until it expires)
- data ordering guarantee for data with the same ‘Partition ID’
- Encryption:
    - at rest- KMS
    - in flight - HTTPS
- **Kinesis Producer Library (KPL):**
    - helps applications efficiently send data to Kinesis Data Streams.
- **Kinesis Consumer Library (KCL):**
    - helps applications consume and process data from Kinesis streams.

**Kinesis Data Streams Capacity Modes**

- **Provisioned Mode:**
    - Manually manage shards
    - Shard capacity:
        - One shard supports approximately:
            
            
            | Operation | Capacity |
            | --- | --- |
            | Write | 1 MB/sec or 1000 records/sec |
            | Read | 2 MB/sec |
    - Shard is the basic unit of storage, capacity, throughput.
    - **How Scaling Works**
        
        If traffic increases: Add more shards manually
        
        If traffic decreases: Reduce shards manually
        
- **On-demand Mode:**
    - AWS automatically scales the stream capacity based on traffic.
    - No shard management required.

### Amazon Data Firehose

- used to capture, transform, and load streaming data into storage and analytics services.
- **What Firehose Does**
    - It:
        - Collects streaming data
        - Optionally transforms/compresses it
        - Delivers it automatically

No shard management required.

- **near real-time** with buffering capability based on size/ time.
- Firehose can deliver data to:

| Destination | Purpose |
| --- | --- |
| Amazon S3 | Storage |
| Amazon Redshift | Data warehousing |
| Amazon OpenSearch Service | Log analytics |
| Splunk | Monitoring/log analysis |
| HTTP endpoints | Custom integrations |

| Data Firehose | Kinesis Data Streams |
| --- | --- |
| Load streaming data into S3/ Redshift/ OpenSearch | Streaming Data collection |
| Fully managed | Producer & Consumer code |
| Near real time | Real-time |
| Automatic Scaling | Provisioned/ On-demand mode |
| No data storage | Data storage upto 365 days |
| doesn’t support replay capability | replay capability |

### Amazon MQ

- it is a message broker service
    - A message broker acts as a middle layer between applications.
- used for reliable communication between applications using traditional messaging protocols.

**Why Amazon MQ is Used**

Many enterprise applications already use:

- ActiveMQ
- RabbitMQ
- JMS
- AMQP
- MQTT

Amazon MQ helps migrate these applications to AWS without changing existing messaging logic.

**Example:** A company has an old Java application using:

- JMS
- ActiveMQ

Instead of redesigning the application:

- Move messaging to Amazon MQ

Application continues working with minimal changes.


### Docker
- it is a software development platform to deploy apps
- apps are packaged in containers that can be run on any OS.
- app run the same, regardless of where they're run:
    - any machine
    - no compatibility issues
    - easier to maintain and deploy
    - works with any language, any OS, any technology.

  **where are docker images stored?**
  - docker images are stored in docker repositories
  - docker hub:
      - public repository
      - find base images for many techonologies or OS
   
**Amazon ECR (Amazon Elastic Container Registry)**
- fully managed container image registry service used to store, manage, and deploy Docker and OCI container images.
- private repository

-  What ECR does
You can:
- Push Docker images
- Pull images into deployments
- Store private or public container repositories
- Scan images for vulnerabilities
- Replicate images across AWS regions/accounts
- Control access using IAM policies

ECR supports:
- Docker images
- OCI images
- OCI artifacts (Helm charts, signatures, et


Typical workflow
- Build a Docker image locally
- Authenticate Docker to ECR
- Push image to an ECR repository
- Deploy image using:
    - Amazon Elastic Kubernetes Service (EKS)
    - Amazon Elastic Container Service (ECS)
    - Kubernetes
    - EC2 instances
    - Lambda container images

- docker vs VM
    - docker is sort of virtualization technology, but not exactly
    -  resources are shared with the host-> many containers on one server.



### Amazon ECS 
- fully managed container orchestration service from AWS
 used to run and scale Docker containers in production.
- It helps you deploy containers without managing your own Kubernetes control plane.

- two ECS launch types:
- EC2 launch type → You manage the servers
Fargate → AWS manages the servers
    - EC2 launch type:
        - launch Docker containers on AWS = launch ECS tasks on ECS Clusters
        - you must provision and maintain the infrastructure
        - each EC2 instance must run the ECS agent to register in the ECS cluster.
        - How it works
Create EC2 instances
Install ECS agent automatically
Add EC2 instances to ECS cluster
Deploy containers to those EC2 machines       
    - Fargate (serverless containers):
        -  Fargate Launch Type:
            - launch docker containers on AWS.
            - you do not provision the infrastructure
            - you just create task definitions
            - AWS just runs ECS tasks for you based on CPU/ RAM u need
            - to scale, just increase the no of task.
           | Feature           | ECS EC2 Launch Type       | Fargate                          |
| ----------------- | ------------------------- | -------------------------------- |
| Server management | You manage EC2 instances  | AWS manages infrastructure       |
| Setup complexity  | More                      | Less                             |
| Maintenance       | You patch/update servers  | AWS handles it                   |
| Scaling           | You scale EC2 machines    | Automatic infrastructure scaling |
| Control           | Full control over servers | Limited server access            |
| Pricing           | Pay for EC2 instances     | Pay per container resources      |
| Best for          | Large/custom workloads    | Simple microservices/apps        |
| GPU support       | Yes                       | Limited                          |
| OS access         | Yes (SSH possible)        | No SSH access                    |


### Amazon ECS- IAM roles for ECS
- EC2 instance profile (EC2 launch type only):
    - used by ECS agent
    - make API calls to ECS service
    - send container logs to cloudWatch logs
    - pull docker image from ECR
    - reference sensitive data in secret manager or SSM parameter store.
 
  - ECS task role:
      - allows each task to have a specific role
      - use different roles for the different ECS services you run
      - task role is defined in task definition


### Amazon ECR
- ECR= Elastic Container Registry
- store and manage docker images on AWS
- private and public repository
- fully integrated with ECS, backed by Amazon S3
- access is controlled through IAM
- example: let docker images are in ECR repsority, using the IAM roles those images are pulled to the ECS cluster.

### Amazon EKS
- Amazon Elastic Kubernetes service
- Runs Kubernetes clusters on AWS infrastructure
- kubernetes is an open-source system for automatic deployment, scaling, and management of containerized application
- its an alternative to ECS
- EKS supports EC2 if you want to deploy worker nodes or Fargate to deploy serverless containers.
- Workeer nodes: machines that actually run your application containers(pods).

  **Amazon EKS - Node types**
  - Managed Node Groups:
      - creates and manages nodes (EC2 instances) for you.
      - nodes are part of an ASG managed by EKS
      - supports on-demand or spot instances
      - aws automatically manages: EC2 provisioning, updates, scaling, lifecycle management.
   
- Self-managed Nodes:
    -  nodes created by you and registered to the EKS cluster and managed by an ASG
    -  you can use prebuilt AMI- Amazon EKS Optimized AMI
    -  supports on-demand or spot instances
    -  you manage: EC2 instances, AMIs, scaling groups
 
- AWS Fargate:
    - no EC2 servers to manage
    - pods runs serverlessly
    - pay per pod resource
 
  ### AWS App runner
  - fully managed service that makes it easy to deploy web applications and APIs at scale.
  - start with your source code or container image
  - automatically builds and deploy the web app
  - automatic scaling, highly available, load balancer, encryption
  - VPC access support
  - connect to database, cache, and message queue services
 
  ### AWS App2Container (A2C)
  - CLI tool for migrating and modernizing JAVA and .NET web apps into docker containers.
  - Lift-and-shift your apps running in on-premises bare metal, virtual machines or in any cloud to AWS
  - accelerate modernization, no code changes, migrate legacy apps
  - generate cloudformation templates
  - register generated docker containers to ECR
  - deploy to ECS, EKS or app runner
  - supports pre-built CI/CD pipelines
 
    
### AWS Lambda integrations
- API Gateway
- Kinesis
- DynamoDB
- S3
- CloudFront
- CloudWatch Events EventBridge
- Cloudwatch Logs
- SNS
- SQS
- Cognito

  ### Lambda Limits - per region
  - Execution:
      - Memory allocation: 128 MB- 10 GB (1 MB increment)
      - Maximum execution time: 900 seconds (15minutes)
      - Environment Variables : 4kb
      - disk capacity in the 'function continaer' (/tmp): 512mb- 10gb
      - concurrency executions: 1000
  - Deployment:
      - lambda function deployment size (compresse.zip): 50mb
      - size of uncompressed deployment (code + dependencies): 250 mb
      - can use the /tmp directory to load other files at the startup
      - size of env variables: 4kb

### Lambda Concurrency
- number of instances your Lambda function running at the same time
- Each concurrent request is runs in its own separate execution environment.
- concurrency limit: upto 1000 concurrent executions
- can set a 'reserved concurrency' at a function level (can set limit)
- each invocation over the concurrency limit will trigger a 'Throttle'
 **Throttling** happens when the number of incoming requests exceeds the available concurrency.
  if a function is throttled, 
  - if synchronous invocation: return ThrottleError-429
  - if asynchronous invocation: retry automatically and then go to DLQ

-Throttling occurs in these scenarios:
    - The function exceeds reserved concurrency.
    - The account exceeds regional concurrency limits.
    - Burst of traffic exceeds available provisioned/unreserved concurrency.

  example:
  | Function | Reserved Concurrency | Incoming Requests | Result                                                                |
| -------- | -------------------- | ----------------- | --------------------------------------------------------------------- |
| MyFunc   | 10                   | 8                 | All 8 requests execute immediately.                                   |
| MyFunc   | 10                   | 15                | 10 execute immediately, 5 throttled (for async triggers, they retry). |
| MyFunc   | None (default)       | 1,200             | If account limit is 1,000, 1,000 execute, 200 throttled.              |


When requests arrive:
- Lambda checks available concurrency.
    - If concurrency is available → function executes.
    - If concurrency is exhausted → Lambda throttles additional requests.
 
- Cold Start & Provisioned Concurrency
    - Cold Start : happens when AWS Lambda has to create a new execution environment before running your function.
    - includes:
        - allocating compute resources
        - starting the runtime
        - loading your function code
        - initializing the dependencies/ libraries
- Why Cold Starts Happen
Lambda scales automatically.

If:

no existing execution environment is available, or
traffic suddenly increases,

AWS creates a new container/environment.

That new environment initialization = cold start.
  - Example

Suppose:

Your Lambda normally handles 5 requests.
Suddenly 100 requests arrive.

AWS may:
reuse 5 warm environments
create 95 new environments

Those 95 may experience cold starts  

- Provisioned Concurrency
    - keeps Lambda environments pre-initialized and ready.
    - This minimizes or eliminates cold starts.

AWS maintains a specified number of warm execution environments continuously.

 
 ### Lambda SnapStart
 -reduces cold start latency by restoring Lambda execution environments from a pre-initialized snapshot instead of initializing them from scratch every time.
 - improve the lambda function performance upto 10X at no extra cost for JAVA, python & .NET
 - when enabled, function is invoked from a pre-initialized state
- when you publish a new version:
    - lambda initializes your function
    - takes a snapshot of memory and disk state of the initialized function
    - snapshot is cached for low-latency access.
          
- How SnapStart Works
Without SnapStart
Request arrives
    → Lambda creates environment
    → Runtime initializes
    → Code initializes
    → Function executes

- Cold start latency is high.

- With SnapStart

-When you publish a Lambda version:

Lambda initializes function once
→ Creates encrypted memory snapshot
→ Stores snapshot

Later during invocation:

Request arrives
→ Lambda restores snapshot
→ Function resumes quickly
→ Function executes

Instead of rebuilding the environment, AWS restores it from the saved state.


### Lambda 
**add this in lambda in VPC**

- by default, lambda function is launched outsdie the VPC, therefore it cannot access resources in VPC (RDS, elasticcache, ELB,....)
- lambda in VPC: define the VPC ID, subnets and the security groups
    - lambda will create an ENI in your subnets


 ### RDS - event notifications
 - RDS event notifications:
     - let you get alerts when something happens inside your database service. 
     - notifications that tells information about the DB instance itself
     - you don't have any information about the data itself
     - near real time events
     - send notifications to SNS or subscribe to events using EventBridge
  
   
### Amazon DynamoDB
- it is a fast, scalable NoSQL database.
- stores data in tables
- scales to massive workloads, distributed database.
- millions of requests per second
- integrated with IAM for security, authorization and administration
- low cost and auto scaling capabilities

- dynamoDB is made of tables
- each table has a primary key (must be decided at craetion time)
- each table can have an infinite no of items (rows)
- each item has attributes (can be added over time- can be null) (columns)
- maximum size of an item is 400kb
- dynamo db is better than RDS & Aurora

- DynamoDB Capacity Modes
    -Provisioned Capacity Mode:
      - manually specify:
          - read capacity units (RCUs)
          - write capacity units (WCUs)
      How it works

    - Example:
    
    - 100 RCUs
    - 50 WCUs
    
    The table can handle:
    
    100 strongly consistent reads/sec (4 KB items)
    50 writes/sec (1 KB items)
    
    If traffic exceeds provisioned capacity:
    
    requests may get throttled
    you receive ProvisionedThroughputExceededException
    - AutoScaling:
        - dynamo can automatically increase/decrease RCUs, WCUs based on traffic utilization.
    
    
    -  On demand capcity mode:
      
        - do not specify RCUS, wcuS
        - DynamoDB automatically:
            - scales up, scales down based on incoming traffic
          - pay for what you use
          - no capacity planning needed

### DynamoDB Accelerator (DAX)
- fully managed, in-memory cache for Amazon DynamoDB.
- improves read performance from : milliseconds -> microseconds
- 5 minutes TTL for cache (default)
-  What is DAX?

DAX sits between: your application & DynamoDB table

- Architecture:

Application
     ↓
    DAX
     ↓
 DynamoDB  
 - DAX caches frequently accessed data in memory.
 - Why Use DAX?

- Without DAX: every read goes to DynamoDB
- With DAX: repeated reads are served from cache

- | Feature             | DAX                   | ElastiCache     |
| ------------------- | --------------------- | --------------- |
| Built for DynamoDB  | Yes                   | No              |
| API compatible      | Yes                   | No              |
| Managed cache logic | Automatic             | Manual          |
| Setup complexity    | Simple                | Higher          |
| Best for            | DynamoDB acceleration | General caching |

### DynamoDB stream Processing
- captures changes made to a DynamoDB table and allows you to process them in near real time.
- Whenever an item in DynamoDB is:
inserted
updated
deleted
- a stream record is generated automatically.
- Applications can consume these events for processing.
- Stream Prcoessing flow:
- DynamoDB Table
      ↓
 DynamoDB Stream
      ↓
 Lambda / Kinesis / App
      ↓
 Process Event
- each stream record contains: event type, timestamp, keys, old image, new image

- DynamoDB global tables:
    - They replicate table data automatically across multiple AWS regions.
    - active active writes
    - application can READ and WRITE to the table in any region
    - must enable DynamoDB streams as pre-requisite
    - user access nearest AWS region
    - if one region fails, other regions continues serving the traffic

  -How Replication Works

DynamoDB uses:

DynamoDB Streams internally

to replicate changes across regions.

When item changes in one region:

change captured
replicated asynchronously
applied to other regions


### DynamoDB -TTL
- automatically delete items after an expiry timestamp
- workflow:
- Application
    ↓
Write item with expiration timestamp
    ↓
DynamoDB TTL process
    ↓
Expired item automatically deleted



### API Gateway
- API Gateway receives client requests and routes them to backend services like:

AWS Lambda
EC2
ECS
DynamoDB
HTTP services
- Architecture:
- Client
   ↓
API Gateway
   ↓
Backend Service
(Lambda / EC2 / ECS / DynamoDB)

- support WebSocket protocol
- handle API versioning
- hadnle different environments (dev,prod,test,..)
- create API keys, handle request throttling
- cache API responses
- swagger/Open API import to quickly define APIs

- Flow:

Request hits API Gateway
Authentication validated
Routed to Lambda
Lambda queries DynamoDB
Response returned to user

- Lamdba Function: easy way to expose REST API backed by AWS lambda
- HTTP: expose HTTP endpoints in the backend
    - why? add rate limiting, caching , user authentication, API keys
- AWS service: expose any AWS API through API Gateway

- API Gateway -End points:
    - Edge- Optimized: for global clients
        - requests are routed through the CloudFront Edge location
        - the API gateway still lives in only one region
    - Regional:
        - for clients within the same region
        - could manually combine with cloudfront
    - Private:
        - can only be accessed from VPC , using an interface VPC endpoint (ENI)
     
### Step Functions
- serverless workflow orchestration service used to coordinate multiple AWS services into a sequence of steps.
- -Step Functions allow you to define workflows as:

states
transitions

using JSON-based Amazon States Language (ASL).
- architecture:
- Start
  ↓
Lambda Function
  ↓
Choice / Condition
  ↓
Another Service
  ↓
Success / Failure

-Why Use It?

Instead of writing complex code for:

retries
waiting
sequencing
error handling

AWS manages it for you.

### Amazon Cognito:
- gives users an identity to interact with our web or mobile applications
- Cognito = Login system for applications.
-used for: user authentication, authorization, user management

It helps users:

sign up
sign in
access applications securely

- What Cognito Does

It manages:

usernames/passwords
social logins
OTP verification
JWT tokens
user sessions

- Example

Mobile app login flow:

User Login
    ↓
Amazon Cognito
    ↓
Verify User
    ↓
Return Token
    ↓
Access App APIs

- User Pool: handles sign up, sign in, authentication
  - acts like a user database.
  - example: email/password login
- Identity Pool:
    -  get identities for 'users' to obtain temporary AWS credentials
    - used when app need access to S3, dynamoDB, other AWS services


## section 20 important



### Amazon Neptune
- fully managed graph database
- a popular graph dataset would be a social network
    - users have friends
    - posts have comments
    - comments have likes from users
    - users share and like posts
- highly available across 3AZ, with upto 15 read replicas
- build and run applications working with highly connected datasets
- can store up to billions of relations and query the graph with milliseconds latency
- highly available with replications across multiple AZs

### Amazon Neptune - Streams
- real time ordered sequence of every chagne to your graph data
- changes are available immediately after writing
- no duplicates, strict order
- streams data is accessible in an HTTP REST API


### Anazon Keyspaces ( for Apache Cassandra)
- open source NoSQL distributed database
- it is a serverless, scalable, highly available, fully managed by AWS
- automatically scale tables up/down based on the application's traffic
- tables are replicated 3 times across multiple AZ
- using the CQL(cassandra query language)
- single digit millisecond latency at any scale, 1000s of requests per second


 ### Amazon Timestream
 - fully managed, fast, scalable, sreverless time series database
 - automatically scales up/down to adjust capacity
 - store and analayze trillions of events per day
 - 1000s times faster and 1/10th the cost of relational databases (cheaper)
 - scheduled queries, multi-measure records
 - encryption in transit and at rest
   
### Amazon Athena

- **serverless query service** in AWS that allows you to analyze data directly in Amazon S3 using standard SQL.
- you do **not** need to:
    - manage servers
    - create databases manually
    - load data into another system

Athena works directly on files stored in S3.

supports CSV, JSON, ORC, Parquet, Avro.

**How Athena Works**

```
Data → Stored in S3
        ↓
Athena reads files
        ↓
Uses SQL to query data
        ↓
Returns results
```

### **Amazon QuickSight**

- AWS tool for dashboards and data visualisation
- It converts raw data into:
    - graphs
    - charts
    - reports
    - interactive dashboards

| Feature | QuickSight | Athena |
| --- | --- | --- |
| Purpose | Visualization | Querying |
| Output | Dashboards | SQL results |
| Uses SQL? | Indirectly | Yes |
| Main Use | BI analytics | Data querying |

**Integrations:**

| Service | Purpose |
| --- | --- |
| Amazon S3 | Analyze files/data lake |
| Amazon Athena | Query S3 data and visualize |
| Amazon Redshift | Data warehouse analytics |
| Amazon RDS | Database reporting |
| AWS Glue | Metadata/catalog integration |
| Amazon OpenSearch Service | Log analytics dashboards |
| Amazon CloudWatch | Monitoring dashboards |
| AWS Lambda | Automation/workflows |
| AWS Identity and Access Management IAM | Access control/security |

Data Source
↓
Athena / Redshift / RDS
↓
QuickSight
↓
Dashboards & Reports

### Redshift

- AWS data warehouse for analysing huge amounts of data
- based on PostgreSQL
- 10x better performance than other ware houses
- Redshift stores data by columns instead of rows.
    - **Traditional row storage:**
    
    ```
    1, Ram, 500
    2, Sam, 700
    ```
    
    - **Columnar storage:**
    
    ```
    IDs: 1,2
    Names: Ram,Sam
    Amounts: 500,700
    ```
    
- It stores and analyses:
    - TBs to PBs of structured data
    - using SQL queries

**Architecture:**

Client SQL Query
↓
Leader Node
↓
Compute Nodes
↓
Parallel Processing

| Component | Purpose |
| --- | --- |
| Leader Node | Receives SQL queries and coordinates execution |
| Compute Nodes | Store data and execute queries, send results to Leader node. |
| Node Slices | Parallel processing units inside nodes |

**How Redshift Works**

1. Data loaded into Redshift
2. Leader node receives query
3. Query distributed to compute nodes
4. Nodes process data in parallel
5. Results returned quickly

**Example**

```
Company Sales Data
        ↓
   Amazon Redshift
        ↓
 Complex Analytics Queries
        ↓
 Dashboards / Reports
```

Example:

- analyse years of sales data
- generate business reports
- perform trend analysis

| Feature | Redshift | RDS |
| --- | --- | --- |
| Purpose | Analytics | Transactions |
| Query Type | Complex analytical queries | OLTP queries |
| Storage | Columnar | Row-based |
| Scale | Petabytes | Smaller workloads |
| Best For | BI & reporting | Web applications |

**Deployment Types**

| Type | Description |
| --- | --- |
| Provisioned Cluster | Traditional node-based cluster |
| Serverless | No cluster management |

### Redshift Spectrum

Amazon Redshift Spectrum allows **Redshift** to query data directly from:

- Amazon S3

without loading data into Redshift.

```jsx
      Query
        ↓
Amazon Redshift Cluster (leader node, compute node)
        ↓
Redshift Specturm
        ↓
			 S3
```

### Amazon Open Search Service

- OpenSearch is an open-source search and analytics engine.
- in dynamoDB, queries only exist by primary key or indexes
- with open search, you can search any field.
- doesn’t natively support SQL
- AWS provides it as a managed service:
    - automatic scaling
    - backups
    - monitoring
    - security
    - cluster management

**OpenSearch Deployment Modes**

| Mode | Description |
| --- | --- |
| Managed Cluster | Traditional cluster deployment |
| Serverless | Auto-managed OpenSearch |

**OpenSearch Serverless**

Amazon OpenSearch Serverless:

- removes cluster management
- automatically scales
- charges based on usage

### Amazon EMR (Elastic MapReduce)

- It is used to process and analyze **huge amounts of data** using big data frameworks.

| Component | Purpose |
| --- | --- |
| Cluster | Group of EC2 instances |
| Master Node | Controls cluster |
| Core Nodes | Store/process data |
| Task Nodes | Extra processing only |

EMR creates a cluster of EC2 instances to process big data in parallel.

Large Dataset
↓
Split Across Multiple Machines
↓
Parallel Processing
↓
Fast Results

**Why EMR is Needed**

Traditional systems struggle with:

- TBs/PBs of data
- distributed computation
- large-scale analytics

EMR solves this using:

- distributed clusters
- parallel processing

### AWS Glue

- Serverless ETL (Extract, Transform, Load) service
- Used to:
    - discover data
    - transform data
    - move data between sources
    - prepare data for analytics
- example: Extract data from Amazon S3 / Amazon RDS, transform the data using AWS Glue, and load the transformed data into Amazon Redshift.

| Component | Purpose |
| --- | --- |
| Glue Crawler | Scans data and creates schema/metadata |
| Data Catalog | Stores table metadata |
| Glue ETL Jobs | Transform/process data |
| Glue Studio | Visual ETL builder |
| Glue DataBrew | No-code data preparation |
| Glue Job bookmarks | prevent re-processing old data |
| Glud dataBrew | clean and normalize data using pre-built transformation |

### AWS Lake

- data lake: central place to have all data for analytic purpose
- discover, cleanse, transform, ingest data into your data lake.
- it automates many complex manual steps(collecting, cleansing, moving,..) and de-duplications (ML transfoms)
- combine structured and unstructured data in the data lake.
- built on top of AWS Glue.

 **Architecture Flow**

```
Data Sources
(S3, RDS, Databases, Logs)
        ↓
AWS Glue Crawlers
        ↓
Data Catalog
        ↓
AWS Lake Formation
(Security + Permissions)
        ↓
Analytics Services
(Athena, Redshift Spectrum, EMR, QuickSight)
```

### **Amazon MSK**

- **Amazon MSK (Managed Streaming for Apache Kafka)** is a **fully managed Apache Kafka service** provided by AWS.
    
    It helps you:
    
    - Build real-time streaming applications
    - Process large amounts of streaming data
    - Avoid managing Kafka infrastructure manually

**Why Amazon MSK?**

Normally, managing Kafka requires:

- Server setup
- Broker management
- Scaling
- Patching
- Monitoring
- Replication handling

Amazon MSK handles all these automatically.

 **Architecture**

```
Producers
(Apps, Logs, IoT)
      ↓
Amazon MSK Cluster
(Kafka Brokers + Topics)
      ↓
Consumers
(Analytics, Applications, ML)
```

| Component | Purpose |
| --- | --- |
| Kafka Brokers | Store and manage messages |
| Topics | Categories for messages |
| Producers | Send messages |
| Consumers | Read messages |
| ZooKeeper / KRaft | Cluster coordination |

![image.png](attachment:725f111f-a03a-4c37-b76f-ae636e1b2a04:image.png)

### Big Data Ingestion Pipeline

- **A Big Data Ingestion Pipeline** is the process of:
    - Collecting large volumes of data
    - Moving the data into storage or analytics systems
    - Processing it for analysis

Data can come from:

- Applications
- IoT devices
- Logs
- Databases
- Streaming platforms

**General Flow**

```
Data Sources
(Apps, IoT, Logs, DBs)
        ↓
Ingestion Layer : Used to collect streaming or batch data.
(Kafka / Kinesis / MSK)
        ↓
Processing Layer : Transforms and cleans the data.
(Glue / Spark / EMR)
        ↓
Storage Layer : Stores raw and processed data.
(S3 / Data Lake / Redshift)
        ↓
Analytics Layer : Used for querying and visualization.
(Athena / QuickSight / ML)
```

**Real-Time Streaming Pipeline Example**

```
Application Logs
        ↓
Amazon MSK / Kinesis
        ↓
AWS Glue Streaming / Lambda
        ↓
Amazon S3
        ↓
Athena / Redshift
        ↓
QuickSight Dashboard
```

- IOT core allows you to harvest data from IoT devices
- kinesis : real time data collection
- Firehose: helps with data delivery to S3 in near real-time
- Lambda: help firehose with data transformation
- Amazon S3: trigger notifications to SQS
- Lambda can subscribe to SQS
- Athena: serverless SQL service and results are stored in S3
