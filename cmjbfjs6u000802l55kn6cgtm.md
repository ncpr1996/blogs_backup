---
title: "Scaling Databases with TiDB: AWS Community Day Bangalore 2025"
seoTitle: "Scaling Databases with TiDB: AWS Community Day Bangalore 2025"
seoDescription: "Why Traditional Databases Struggle and How TiDB Addresses Real-World Scaling Problems"
datePublished: Thu Dec 18 2025 12:41:59 GMT+0000 (Coordinated Universal Time)
cuid: cmjbfjs6u000802l55kn6cgtm
slug: scaling-databases-with-tidb-aws-community-day-bangalore-2025
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766055812194/4508b177-9479-416f-bb4c-5a1f8c6a1827.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766061619845/27df96fe-15b4-443d-99f4-246c700633ee.jpeg
tags: nosql, aws, databases, sql, amazon-web-services, aws-community, tidb

---

One session at AWS Community Day Bangalore 2025 in May fundamentally altered my perspective on database scalability. Senior Solution Architect Ankit Kapoor of TiDB gave a very enlightening session titled "From Startup to Scale-up: Your Database's Growth Journey."

This is for you if you've ever had trouble with database scaling.

## The Problem We All Face

To be honest, conventional relational databases function flawlessly until they break down. Ankit outlined the difficulties faced by the majority of expanding businesses:

### **Manual Configuration Nightmares**

* Shard mapping needs to be configured manually.
    
* Cross-shard searches add needless complexity to application code.
    
* Under heavy load, concurrency constraints result in row-level locking.
    
* Several housekeeping tasks take up important time.
    

### **Vertical Scaling Hits a Wall**

* A bottleneck is created by mutex contention.
    
* Growth is restricted by shared resource bottlenecks.
    
* Commodity hardware is plagued with OOM problems and low CPU utilization.
    

### **Performance Issues That Hurt**

* Writes continue to be bottlenecked, but read operations scale
    
* It is only possible to achieve eventual consistency.
    
* Analytical queries don't work well with row-based storage.
    
* Semantic search moves slowly.
    

Does that sound familiar? The majority of us have been there, which is why.

## What is Distributed SQL?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1766058769711/497c63f8-0811-4a2d-93de-5a53a50a3a12.jpeg align="center")

This is the fascinating part. Distributed SQL is an advanced database architecture that blends the greatest features of both worlds; it's not just another catchphrase. It offers both the horizontal scale of NoSQL databases and the transactional guarantees of relational databases, as Ankit clarified.

Take a moment to consider that. Scalability is maintained while achieving ACID compliance.

## Enter TiDB: The Open Source Solution

I was drawn to TiDB because of its outstanding credentials:

* **Founded in 2015** and 100% open source
    
* **38,000+ GitHub Stars** showing strong developer interest
    
* **800+ Contributors** building and improving it
    
* **10,000+ Adopters** worldwide
    
* **8,000+ Slack Users** in an active community
    

Big names like Pinterest, CAPCOM, Conga, Bolt, and Ninja trust TiDB with their production workloads. Over 4,000+ enterprise adopters across 25 countries use it daily.

## How TiDB Works: Architecture Made Simple

Ankit divided the architecture of TiDB into four primary parts:

### **Compute Layer**

* Handles SQL processing and query optimization
    
* MySQL compatible (huge win for migration!)
    

### **Row Store**

* Distributed key - value storage
    
* Perfect for OLTP workloads with strong consistency
    

### **Columnar Store**

* Enables real-time analytics on transactional data
    
* Uses a columnar storage engine for analytical queries
    

### **Placement Driver (PD)**

* Manages metadata
    
* Balances data distribution across nodes automatically
    

The beauty? Storage and computation are entirely distinct. This implies that you can scale them on your own according to your requirements.

## TiDB vs Traditional Databases: The Real Difference

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1766058605419/ba8cdf9e-ba68-44ba-b85b-db7a670edb7c.jpeg align="center")

Conventional databases employ a single-master configuration in which read replicas use transaction log replication to handle read traffic while one instance manages writes. It's limiting, but it works.

This model is flipped by TiDB. While ensuring ACID transactions with excellent read consistency, several TiDB instances manage both reads and writes concurrently. The computation layer is stateless and scalable on its own, while the storage layer (TiKV) is horizontally scalable and supports many replicas.

## What This Means for DBAs

Ankit emphasized how TiDB reduces operational headaches:

* **Horizontal Scaling**: Automatic sharding and seamless scaling without the need for human intervention
    
* **99.99% Availability**: Your data is kept accessible by auto-failover and self-healing.
    
* **Mixed Workloads**: AI, analytical, and transactional workloads are all handled by a single database.
    
* **Strong Consistency**: Strong data integrity and worldwide compliance in ACID transactions
    
* **Security**: Enterprise-grade encryption both in-flight and at-rest
    
* **MySQL Compatibility**: Easy migration path for existing MySQL users
    
* **Multi-Cloud**: Deploy across your preferred cloud platforms
    
* **100% Open Source**: Transparent, community-driven development
    

## The Operational Simplicity Win

I was very impressed by TiDB's integrated Grafana and Prometheus dashboards. Instant monitoring, performance measurements, and system health data straight out of the box, no further setup or configuration nightmare.

For teams without dedicated DevOps resources, this is a game-changer.

## Three Deployment Options on AWS

TiDB offers flexibility based on your needs:

### **TiDB Cloud Serverless**

* Fully managed with effortless scalability
    
* Pay-as-you-go pricing
    
* 99.99% availability (currently 99.9%)
    
* Perfect for variable workloads, web applications, and microservices
    

### **TiDB Cloud Dedicated**

* Fully managed with high performance
    
* 99.99% availability
    
* Subscription pricing starting at $2/hour with volume discounts
    
* Ideal for mission-critical applications with heavy read/write operations
    

### **TiDB Self-Managed**

* Self-managed for maximum control
    
* Custom pricing
    
* Premium support available
    
* Best for large enterprises with complex infrastructure needs
    

## Conclusion

My understanding of database architecture has changed as a result of this session. For many years, traditional databases worked well for us, but contemporary applications require more. TiDB solves actual scalability issues without requiring you to give up on SQL or ACID guarantees.

It is a strong competitor due to its open-source nature and production-proven dependability at large corporations. TiDB should be included in your evaluation list if your present database is experiencing scaling issues or if you are designing a new system that must accommodate expansion.

AWS Community Day Bangalore still offers insightful, useful content from actual professionals addressing actual issues. Sessions like Ankit's serve as a reminder of the importance of community gatherings since they provide us with solutions that we might not otherwise come across.

## **References**

**Event:** AWS Community Day Bangalore 2025

**Topic:** Scaling Databases with TiDB

**Date:** May 23, 2025

**Location:** [**Conrad Benguluru**](https://www.hilton.com/en/hotels/blrkrci-conrad-bengaluru/hotel-location/?WT.mc_id=zPADA0IN1CH2PSH3paid_ggl4DOMBPP_Apr5SiteGGL_ObjROAS_TacBPP_TarKeyword_SMIN_FrmtRSAs_CrNText_DvceAll_LPOHW6BLRKRCI7EN8acctid=9094736915-campid=16903767109-adgrpid=135963230375&&&&&gad_source=1&gad_campaignid=16903767109&gbraid=0AAAAADnjLGN_JqIwAdvqkR6YxlY-a8paB&gclid=CjwKCAjwjffHBhBuEiwAKMb8pLhlL6XFN37JymneexipiKWmv-jIGYxbiJtul9ZkklxfW_jN7zel4RoCCYAQAvD_BwE&gclsrc=aw.ds)

## **Also Published On**

[**AWS Builder Center**](https://builder.aws.com/content/34bpGSW7cvq1czKxj1aY5UlykrT/building-secure-foundations-or-aws-community-day-bangalore-2025)

[**Dev Community**](https://dev.to/aws-builders/building-secure-foundations-aws-community-day-bangalore-2025-24b1)