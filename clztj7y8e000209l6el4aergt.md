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

* High-performance, scalable block storage is offered by Amazon Elastic Block Store (EBS) for usage with Amazon EC2 instances.
    
    **Multiple volume types :**
    
    * SSD-backed storage for transactional workloads.
        
    * HDD-backed storage for throughput-intensive workloads.
        
    * Optimizes storage performance and cost for various applications.
        
    
    **Scalability :**
    
    * EBS volumes can be adjusted to your specifications for performance and capacity.
        
    * Elastic Volumes allow you to change the performance and volume size without any downtime.
        
    
    **Backup and recovery :**
    
    * To back up the data on your volumes, use EBS snapshots.
        
    * Snapshots can move data between AWS accounts, regions, or zones, or they can instantaneously restore volumes.
        
    
    **Data protection :**
    
    * For data protection, encrypt EBS volumes and snapshots.
        
    * Data-at-rest and data-in-transit between an instance and its volume are secure thanks to encryption.
        
    
    **Data availability and durability :**
    
    * io2 Block Express volumes have an annual failure rate of 0.001% and a durability of 99.999%.
        
    * Other volume types have an annual failure rate of 0.1% to 0.2% but give durability of 99.8% to 99.9%.
        
    * In the event that a component fails, data loss is avoided thanks to automatic data replication over multiple servers.
        
    
    **Data archiving :**
    
    * EBS Snapshots Archive provides a low-cost option for archiving snapshots for 90 days or more, useful for regulatory, compliance, or future project needs.
        

With Amazon Elastic Block Store, you can create and manage the following block storage resources :

## Amazon EBS volumes

* For EC2 instances, a robust block-level storage device is an Amazon EBS volume.
    
* EBS volumes can be connected to instances and utilized just like a traditional hard drive.
    
* EBS volumes are flexible :
    
    * Increase size, adjust IOPS capacity, and change volume type on live volumes for current-generation instances.
        
* Use EBS volumes for :
    
    * Primary storage with frequent updates (e.g., system drive, database storage).
        
    * Applications with high throughput that require constant disk access.
        
* Even if the EC2 instance is stopped or terminated, the EBS volumes continue to exist.
    
* A single instance can have numerous EBS volumes attached to it; the instances and volumes need to be in the same Availability Zone.
    
* Mounting a volume to numerous instances at once is possible using the Multi-Attach functionality.
    
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
    
    * Replicated EBS volumes exist within of each Availability Zone.
        
    * Connect to instances of EC2 within the same zone.
        
    * Volumes should be formatted like actual drives.
        
    * You can attach io1/io2 volumes to up to 16 instances and others to just one.
        
    * Free monitoring with CloudWatch and EventBridge.
        
* **Data Persistence :**
    
    * EBS volumes last longer than an instance.
        
    * Uncheck "Delete on Termination" to keep data after termination.
        
    * Data remains through stop-start cycles.
        
    * Volumes that are deleted are encrypted or rewritten.
        
* **Data Encryption :**
    
    * Use Amazon EBS encryption with AES-256.
        
    * Manage keys with AWS KMS or customer keys.
        
* **Data Security :**
    
    * Prior to usage, EBS volumes are randomized or zeroed.
        
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

* Take snapshots to help with recovery and data backup.
    

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

* **Persistent Storage :** Even if the EC2 instance is terminated, data remains.
    
* **Scalable :** Simple resizing and performance adjustments without downtime.
    
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
    
* **I/O Limits :** Performance is limited according to the size and type of volume.
    
* **Manual Management :** Requires careful management for optimization and cost control.
    

## EBS Endpoints and Quotas

* [Endpoints & Quotas](https://docs.aws.amazon.com/general/latest/gr/ebs-service.html#limits_ebs)
    

## Pricing

* [EBS Pricing](https://aws.amazon.com/ebs/pricing/)
    

## Conclusion

* **Versatile Storage :** EBS has both SSD and HDD-backed volumes, offering a variety of configurable storage solutions to suit a variety of applications.
    
* **Scalable & Flexible :** Ensure your storage meets your demands by simply adjusting volume, size, and performance without experiencing any downtime.
    
* **Data Security & Protection :** Strong data encryption and automated replication are provided by EBS volumes for excellent availability and durability.
    
* **Backup & Recovery :** Quick backups and simple data recovery or migration between AWS environments are made possible via snapshots.
    
* **Cost-Effective Choices :** Depending on the use case, EBS provides a variety of volume types to maximize storage performance and costs.
    
* **Best Practices :** To guarantee effective and safe storage solutions, pick the appropriate volume type, keep an eye on performance, take frequent snapshots, and manage your storage lifecycle.
    

## References

* [**AWS EBS Volumes**](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volumes.html)