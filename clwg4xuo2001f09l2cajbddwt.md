---
title: "ELASTIC COMPUTE CLOUD ( EC2 ) Part - I"
datePublished: Tue May 21 2024 08:30:37 GMT+0000 (Coordinated Universal Time)
cuid: clwg4xuo2001f09l2cajbddwt
slug: elastic-compute-cloud-ec2-part-i
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1716138660921/697f6374-0628-46ec-acce-64d35a982c7c.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1716210882657/1609a654-109e-4b27-b3a5-522c0b477ef8.png
tags: cloud, ec2, aws, technology, cloud-computing, devops, scalability, amazon-web-services, sre, virtualization, aws-certified-solutions-architect-associate, cloud-security, ec2-instance-types, ec2-instance, ec2-purchasing-options

---

## Introduction

* Amazon EC2 (Elastic Compute Cloud) offers scalable computing resources within the AWS cloud.
    
* You can launch as many or as few virtual servers as necessary using Amazon EC2.
    
* Security, networking, and storage management are customizable.
    
* Amazon EC2 allows dynamic scaling of instances, both up and down.
    
* Two storage options are available: Elastic Block Store (EBS) and instance store.
    
* Preconfigured templates, known as Amazon Machine Images (AMIs), are provided.
    
* By default, new EC2 accounts are limited to a maximum of 20 instances per region, including two high I/O instances.
    
* EC2 Instances come in four sizes: Nano, Small, Medium, Large.
    

## Types of EC2 instances

### General Purpose

* General-purpose instances offer a balanced mix of computing power, memory, and networking resources, suitable for various tasks.
    
* General-purpose instances come in two different series.
    
    1. **M series :** M4, M5, M5a, M5n, M5zn, M6a, M6g, M6i, M6in, Mac, M7a, M7g, M7i, M7i-flex
        
    2. **T series :** T2 (free tier eligible), T3, T3a, T4g
        
        * Here, each series denotes various aspects like
            
            * **M4 :** Older generation, balanced compute, memory, and networking.
                
            * **M5 :** Latest generation, optimized for general-purpose workloads.
                
            * **M5a :** M5 instances powered by AMD processors.
                
            * **M5n :** M5 instances with enhanced networking capabilities.
                
            * **M6a :** M6 instances powered by 3rd generation AMD processors.
                
            * **M6g :** M6 instances powered by AWS Graviton2 processors, with additional memory optimizations.
                
            * **M6i :** M6 instance powered by 3rd Generation Intel Xeon Scalable processors.
                
            * **M6in :** M6 instances powered by 3rd Generation Intel Xeon Scalable processors and also for network-intensive workloads.
                
            * **Mac :** Mac instances designed for macOS workloads.
                
            * **M7a :** M7a instance powered by 4th Generation AMD EPYC processors and also delivered upto to 50% high performance compared to M6a instance.
                
            * **M7g :** M7g instance powered by Arm-based AWS Graviton3 processors.
                
            * **M7i :** M7i instance powered by 4th Generation Intel Xeon Scalable processors and deliver 15% better price performance than M6i instances.
                
            * **M7i-flex :** M7i instance powered by 4th Generation Intel Xeon Scalable processors with flexible configurations.
                
        * As for the same T series , each series denotes various aspects like, generations , architecture, network.
            
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716139021345/6e82f4a5-d75a-47b3-a9ac-cd069bb9fa6f.png align="center")
        
    3. Some instance types support 'arm based architecture' and some are '64bit (x86) architecture'. I'm not included some instance type like 'A series'. It's only support arm based architecture. So, choose carefully based on our requirements.
        

### Compute Optimized

* Compute-optimized instances are perfect for applications that rely heavily on processing power, benefiting from high-performance processors.
    
* Compute-optimized instances comes with only one series i.e, **C series**
    
    1. **C Series :** C4, C5, C5a, C5n, C6a, C6i, C6in, C6g, C6gn, C7a, C7g, C7gn, C7i, C7i-flex
        
* As you have read above instance types series i.e., M Series, You know what does 'a', 'n', 'i', 'in', 'g', 'gn' and flex denotes.
    

### Memory Optimized

* Memory-optimized instances are designed to deliver swift performance for tasks that involve handling large datasets stored in memory.
    
* Memory optimized instances come in four different series.
    
    1. **R Series :** R4, R5, R5a, R5n, R5b, R6a, R6g, R6i, R6in, R7a, R7g, R7i, R7iz, R8g
        
    2. **X Series :** X1, X1e, X2iedn, X2iezn, X2idn, X2gd
        
    3. **High Memory Series :** like u-3tb1.56xlarge, u-6tb1.56xlarge, u-6tb1.112xlarge, u-9tb1.112xlarge etc.
        
    4. **Z Series :** z1d
        
        * Here, few series denotes various aspects like
            
            * **R5b** instances 3x EBS performance compared to R5 instances of the same size.
                
            * **R7iz** instances are equipped with 4th Generation Intel Xeon Scalable processors, making them perfect for tasks that demand a lot of CPU power and memory.
                
            * **X1e** instances are specifically designed for big databases, in-memory databases, and other memory-heavy business applications like enterprise level.
                
            * **z1d** instances offer high compute capacity and memory, with high-frequency variants delivering up to 4.0 GHz, the fastest in the cloud.
                

### Storage Optimized

* Storage-optimized instances serves to workloads needing high, sequential Read and Write access to massive datasets on local storage.
    
* These instances are optimized to provide tens of thousands of low-latency, random I/O operations per second (IOPS) to applications.
    
* Storage optimized instances come in three different series.
    
    1. **H Series :** H1
        
    2. **D Series :** D2, D3, D3en
        
    3. **I Series :** I3, I3en, I4g, I4i, Im4gn, Is4gen
        

### Accelerated Computing

* Accelerated computing instances use hardware accelerators or co-processors.
    
* They handle tasks like floating-point calculations, graphics processing, and data pattern matching more efficiently than CPUs alone.
    
* Accelerated Computing instances come in Seven different series.
    
    1. **P Series :** P2, P3, P4, P5
        
    2. **G Series :** G3, G4ad, G4dn, G5, G5g, G6
        
    3. **Trn Series :** Trn1
        
    4. **Inf Series :** Inf1, Inf2
        
    5. **DL Series :** DL1, DL2q
        
    6. **F Series :** F1 ( Field programmable gate arrays (FPGAs)
        
    7. **VT Series :** VT1 ( Video Transcoding )
        
        * Here, few series denotes various aspects like
            
            * **Trn1** instance with AWS Trainium chips are designed for high-performance deep learning training, offering up to 50% cost savings.
                
                * AWS Trainium is the machine learning (ML) chip that AWS purpose built for deep learning (DL) training of 100B+ parameter models.
                    
            * **Inf2** instance powered by AWS Inferentia2 offering 3x compute, 4x memory, 4x throughput, and 10x lower latency than Inf1.
                
                * AWS inferentia deliver high performance at the lowest cost in Amazon EC2 for your deep learning (DL) and generative AI inference applications.
                    
            * **DL2q** instance powered by Qualcomm AI 100, cost-efficiently deploy and validate deep learning ( DL ) workloads.
                

### HPC Optimized

* HPC instances are designed for optimal price performance on AWS.
    
* Ideal for large, complex simulations and deep learning workloads.
    
* Built to run high-performance computing (HPC) workloads at scale.
    
* Equipped with high-performance processors for demanding applications.
    
* Below are the series that HPC Optimized instance have
    
    1. **Hpc6a**
        
    2. **Hpc6id**
        
    3. **Hpc7a**
        
    4. **Hpc7g**
        
* Here, Hpc means High Performance Computing ( HPC )
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716139102272/774515ab-3ce7-4268-ad29-e076183c6edc.png align="center")

## EC2 Purchasing options

AWS EC2 instances offer six purchasing options.

### On-Demand Instances

* AWS On-Demand instances are virtual servers in AWS, purchasable at a fixed hourly rate.
    
* Recommended for short-term or irregular workloads that can't be interrupted.
    
* Suitable for testing and developing applications on EC2.
    
* You only pay for the EC2 instances you use with On-Demand instances.
    
* Using On-Demand instances eliminates the need for hardware planning and maintenance, converting fixed costs to variable costs.
    
* Pricing is per instance hour consumed, billed per second for Linux instances and per full hour for other instance types.
    

### Saving Plans

* Savings Plans offer flexible pricing for savings on AWS usage, with potential savings up to 72% on compute workloads.
    
* Compute Savings Plans provide reduced prices on Amazon EC2, AWS Fargate, and AWS Lambda usage, irrespective of instance type, size, OS, tenancy, or AWS Region.
    
* SageMaker Savings Plans offer lower prices for Amazon SageMaker instance usage, regardless of instance type, size, component, or AWS Region.
    
* Savings Plans provide savings beyond On-Demand rates, requiring a commitment to a specified amount of compute power usage for one or three years.
    

### Reserved Instances

* Amazon EC2 Reserved Instances (RIs) offer discounts of up to 75% compared to On-Demand pricing.
    
* RIs also provide a capacity reservation when utilized in a specific availability zone.
    
* Reserved Instances allow you to reserve a DB instance for one or three years, resulting in significant savings compared to On-Demand pricing for the instance.
    

### Spot Instances

* Amazon EC2 Spot Instances offer unused capacity in the AWS cloud at up to 90% off On-Demand prices.
    
* Suitable for various test and development workloads.
    
* Options to hibernate, stop, or terminate Spot Instances with a two-minute notice when capacity is reclaimed by EC2.
    
* Spot Instances can provide savings of up to 90% compared to On-Demand prices but may be interrupted by AWS.
    
* Request Spot Instances up to your spot limit for each region.
    
* Check Spot request status via status code and message on the EC2 console.
    
* Hibernate preserves RAM data while stopping clears RAM.
    
* Hibernate allows instances to pause and resume seamlessly around interruptions.
    

### Dedicated Hosts

* An Amazon EC2 dedicated host is a physical server exclusively dedicated to your use.
    
* Dedicated hosts help meet compliance requirements and reduce costs by utilizing existing server-bound software licenses.
    
* Pay for a dedicated physical host to run your instances and bring your existing software licenses to reduce costs.
    
* Gain visibility and control over instance placement on physical servers, ensuring consistent deployment over time.
    
* Dedicated hosts enable the use of existing server-bound software licenses and meet compliance requirements.
    
* Instances on a dedicated host are the same as those on traditional EC2 instances using the XEN Hypervisor.
    
* Each dedicated host supports a single instance size and type, such as C3.XLARGE.
    
* Only BYOL, Amazon Linux, and AWS Marketplace AMIs can be launched on dedicated hosts.
    

### Dedicated Instance

* Dedicated instances run in a Virtual Private Cloud (VPC) on hardware dedicated to a single customer.
    
* They are physically isolated at the host hardware level from instances belonging to other AWS accounts.
    
* While dedicated instances are isolated, they may share hardware with other instances from the same account that are not dedicated.
    
* Pay for dedicated instances On-Demand, save up to 70% with Reserved Instances, or save up to 90% with Spot Instances.
    

### Capacity Reservations

* Capacity Reservations enable you to reserve compute capacity for Amazon EC2 instances in a specific Availability Zone.
    
* Two types of Capacity Reservations serves to different use cases.
    

## Conclusion

* **Instance Flexibility** : Launch and manage virtual servers with customizable security, networking, and storage options.
    
* **Instance Selection** : Choose the appropriate instance type and size based on your specific requirements.
    
* **Dynamic Scaling** : Easily scale instances up or down based on your needs.
    
* **Storage Options** : Choose between Elastic Block Store (EBS) and instance store for your storage requirements.
    
* **Purchasing Options** : Benefit from multiple purchasing models including On-Demand, Savings Plans, Reserved Instances, Spot Instances, Dedicated Hosts, and Dedicated Instances, each offering unique cost-saving opportunities.
    

## References

* [Types of EC2 Instances](https://aws.amazon.com/ec2/instance-types/)
    
* [EC2 Purchasing Options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html)