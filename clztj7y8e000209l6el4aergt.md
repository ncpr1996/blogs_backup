---
title: "AWS Elastic Block Store { Part - I }"
datePublished: Wed Aug 14 2024 07:30:30 GMT+0000 (Coordinated Universal Time)
cuid: clztj7y8e000209l6el4aergt
slug: aws-elastic-block-store-part-i
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723387933228/6f495f4f-4d9f-461a-bc3b-a73fabcec2a9.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1723610182181/878a2ebf-4b4e-4487-9e9d-39c3eb76943b.png
tags: cloud, aws, cloud-computing, devops, ebs, aws-certified-solutions-architect-associate, devops-articles, devops-trends, aws-ebs, devopscommunity, aws-ebs-introduction, aws-ebs-beginners, elastic-block-store, ebs-volume-types, aws-ebs-pricing

---

## Introduction

* Amazon Elastic Block Store (EBS) provides scalable, high-performance block storage for use with Amazon EC2 instances.
    
    **Multiple volume types :**
    
    * SSD-backed storage for transactional workloads.
        
    * HDD-backed storage for throughput-intensive workloads.
        
    * Optimizes storage performance and cost for various applications.
        
    
    **Scalability :**
    
    * Customize EBS volumes to meet your capacity and performance needs.
        
    * Adjust volume size and performance with no downtime using Elastic Volumes.
        
    
    **Backup and recovery :**
    
    * Use EBS snapshots to back up data on your volumes.
        
    * Snapshots can restore volumes instantly or migrate data across AWS accounts, regions, or zones.
        
    
    **Data protection :**
    
    * Encrypt EBS volumes and snapshots for data security.
        
    * Encryption ensures security for data-at-rest and data-in-transit between an instance and its volume.
        
    
    **Data availability and durability :**
    
    * io2 Block Express volumes offer 99.999% durability with a 0.001% annual failure rate.
        
    * Other volume types offer 99.8% to 99.9% durability with a 0.1% to 0.2% annual failure rate.
        
    * Data is automatically replicated across multiple servers to prevent data loss from component failures.
        
    
    **Data archiving :**
    
    * EBS Snapshots Archive provides a low-cost option for archiving snapshots for 90 days or more, useful for regulatory, compliance, or future project needs.
        

With Amazon Elastic Block Store, you can create and manage the following block storage resources :

## Amazon EBS volumes

* An Amazon EBS volume is a durable block-level storage device for EC2 instances.
    
* You can attach EBS volumes to instances and use them like a physical hard drive.
    
* EBS volumes are flexible :
    
    * Increase size, adjust IOPS capacity, and change volume type on live volumes for current-generation instances.
        
* Use EBS volumes for :
    
    * Primary storage with frequent updates (e.g., system drive, database storage).
        
    * Throughput-intensive applications needing continuous disk access.
        
* EBS volumes persist even if the EC2 instance is stopped or terminated.
    
* Attach multiple EBS volumes to a single instance; volumes and instances must be in the same Availability Zone.
    
* Multi-Attach feature allows mounting a volume to multiple instances simultaneously.
    
* EBS volume types include :
    
    * General Purpose SSD (gp2, gp3)
        
    * Provisioned IOPS SSD (io1, io2)
        
    * Throughput Optimized HDD (st1)
        
    * Cold HDD (sc1)
        
    * Magnetic (standard)
        
* Each type has different performance and cost characteristics.
    
* Your account has a storage limit. Check Amazon EBS endpoints and quotas for details and how to request increases.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723388293575/55d74819-d93c-48fc-a35a-5ee2a0bfb504.png align="center")

### Advantage of using EBS Volumes

* **Data Availability :**
    
    * EBS volumes are replicated within their Availability Zone.
        
    * Attach to EC2 instances in the same zone.
        
    * Format volumes like physical drives.
        
    * Striping improves performance.
        
    * io1/io2 volumes can attach to up to 16 instances; others to one.
        
    * Free monitoring with CloudWatch and EventBridge.
        
* **Data Persistence :**
    
    * EBS volumes persist beyond instance life.
        
    * Uncheck "Delete on Termination" to keep data after termination.
        
    * Data remains through stop-start cycles.
        
    * Deleted volumes are overwritten or encrypted.
        
* **Data Encryption :**
    
    * Use Amazon EBS encryption with AES-256.
        
    * Manage keys with AWS KMS or customer keys.
        
* **Data Security :**
    
    * EBS volumes are zeroed or randomized before use.
        
    * Follow erasure standards like DoD 5220.22-M if needed.
        
* **Snapshots :**
    
    * Back up EBS volumes to S3 with incremental snapshots.
        
    * Encrypted snapshots create encrypted volumes.
        
    * Share and tag snapshots; use Data Lifecycle Manager or AWS Backup.
        
* **Flexibility :**
    
    * Change volume type, size, and IOPS without downtime.
        

### **EBS Volume Types**

* **SSD-backed volumes :**
    
    * **General Purpose SSD (GP2) :**
        
        * Default volume type for EC2 instances.
            
        * Balanced price and performance.
            
        * 3 IOPS/GB, up to 10,000 IOPS.
            
        * Low latency boot volume.
            
        * Size : 1 GB to 16 TB.
            
        * Price : $0.10/GB/month.
            
    * **Provisioned IOPS SSD (io1) :**
        
        * Best for IOPS-intensive and low-latency applications.
            
        * Up to 32,000 IOPS per volume.
            
        * Size : 4 GB to 16 TB.
            
        * Price : $0.125/GB/month.
            
* **HDD-backed volumes :**
    
    * **Throughput Optimized HDD (st1) :**
        
        * Ideal for large, frequently accessed datasets.
            
        * Performance measured in MB/s.
            
        * Not used for boot volumes.
            
        * Up to 500 IOPS per volume.
            
        * Size : 500 GB to 16 TB.
            
        * Price : $0.045/GB/month.
            
    * **Cold HDD (sc1) :**
        
        * Lowest cost per GB, used for infrequent access.
            
        * Suitable for file servers.
            
        * Not used for boot volumes.
            
        * Up to 250 IOPS per volume.
            
        * Size : 500 GB to 16 TB.
            
        * Price : $0.025/GB/month.
            
* **Magnetic Standard :**
    
    * Lowest cost per GB for bootable volumes.
        
    * Best for infrequent data access and low-cost storage.
        
    * Price : $0.05/GB/month.
        
    * Size : 1 GB to 1 TB.
        
    * Max IOPS per volume : 40-200.
        

## **Instance Store Backed EC2**

* Virtual hard drive on the host allocated to the EC2 instance.
    
* Limited to 10GB per device.
    
* Ephemeral (non-persistent) storage.
    
* EC2 instance can only be rebooted or terminated; terminating deletes data.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723388481649/2af2cfcb-aa51-41c8-be97-58ed52bd0754.png align="center")

## Best Practices for AWS EBS Volumes

**Choose the Right Volume Type :**

* Select SSD or HDD based on performance needs (e.g., IOPS vs. throughput).
    

**Size Appropriately :**

* Choose the volume size that fits your needs to avoid over-provisioning or under-provisioning.
    

**Use Snapshots Regularly :**

* Create snapshots to back up data and facilitate recovery.
    

**Monitor Performance :**

* Use Amazon CloudWatch to track volume performance and health.
    

**Encrypt Data :**

* Enable encryption to protect data at rest and in transit.
    

**Optimize IOPS :**

* Use Provisioned IOPS SSD for high-performance needs.
    

**Avoid Single Points of Failure :**

* Replicate data across volumes or use snapshots for redundancy.
    

**Manage Volume Lifecycle :**

* Uncheck "Delete on Termination" to keep volumes after EC2 instance termination.
    

**Use Tags :**

* Tag volumes for better management and organization.
    

**Regularly Review Costs :**

* Monitor and optimize storage costs based on usage and volume types.
    

## Use Cases

**Boot Volumes :**

* Store and run the operating system for EC2 instances.
    

**Database Storage :**

* Host databases that require frequent read/write operations, such as MySQL or MongoDB.
    

**Big Data Processing :**

* Store and process large datasets for analytics, using tools like Hadoop or Spark.
    

**Application Hosting :**

* Store application files and data for web servers or enterprise applications.
    

**Backup and Restore :**

* Create snapshots of EBS volumes for data backup, disaster recovery, or migration.
    

**Log Storage :**

* Store logs and other sequential data that need to be retained and accessed over time.
    

**Development and Testing :**

* Use as temporary storage for development environments, testing, and QA processes.
    

**High-Performance Workloads :**

* Use Provisioned IOPS volumes for performance-sensitive applications like high-traffic websites or online transaction processing (OLTP) systems.
    

**Content Management Systems :**

* Store and serve content for CMS platforms like WordPress, Drupal, or Joomla.
    

**Data Archiving :**

* Use lower-cost EBS volumes like Cold HDD (sc1) for archiving infrequently accessed data.
    

## Pros and Cons

### Pros

* **Persistent Storage :** Data remains even if the EC2 instance is stopped.
    
* **Scalable :** Easily resize and adjust performance without downtime.
    
* **Flexible Types :** Choose from SSD, HDD, or Magnetic based on needs.
    
* **Data Backup :** Create snapshots for easy backup and recovery.
    
* **High Availability :** Automatic data replication within the same AZ.
    
* **Encryption :** Built-in data encryption for security.
    
* **Performance Options :** Provisioned IOPS for high-performance needs.
    
* **Monitoring :** Track performance with Amazon CloudWatch.
    
* **Lifecycle Management :** Control whether volumes are deleted or retained.
    

### Cons

* **Tied to AZ :** Volumes are specific to one Availability Zone.
    
* **Potential Cost :** Costs can add up, especially with high-performance volumes.
    
* **I/O Limits :** Performance is capped based on volume type and size.
    
* **Manual Management :** Requires careful management for optimization and cost control.
    

## EBS Endpoints and Quotas

* [Endpoints & Quotas](https://docs.aws.amazon.com/general/latest/gr/ebs-service.html#limits_ebs)
    

## Pricing

* [EBS Pricing](https://aws.amazon.com/ebs/pricing/)
    

## Conclusion

* **Versatile Storage :** EBS provides flexible storage options tailored to different workloads, with both SSD and HDD-backed volumes.
    
* **Scalable & Flexible :** Easily adjust volume size and performance without downtime, ensuring your storage meets your needs.
    
* **Data Security & Protection :** EBS volumes offer strong data encryption and automatic replication for high durability and availability.
    
* **Backup & Recovery :** Snapshots allow for quick backups and easy data recovery or migration across AWS environments.
    
* **Cost-Effective Choices :** EBS offers a range of volume types to optimize storage performance and costs based on specific use cases.
    
* **Best Practices :** Choose the right volume type, monitor performance, use snapshots regularly, and manage your storage lifecycle to ensure efficient and secure storage solutions.
    

## References

* [**AWS EBS Volumes**](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volumes.html)