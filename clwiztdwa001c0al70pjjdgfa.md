---
title: "ELASTIC COMPUTE CLOUD ( EC2 ) Part - II"
datePublished: Thu May 23 2024 08:30:29 GMT+0000 (Coordinated Universal Time)
cuid: clwiztdwa001c0al70pjjdgfa
slug: elastic-compute-cloud-ec2-part-ii
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1716287219719/4aa66ccf-1635-4294-a3b6-bec8dfe21a66.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1716298238685/94214b26-dfa6-4d39-b10e-69de0d2aadda.png
tags: cloud, ec2, aws, technology, cloud-computing, monitoring, devops, ssh, scalability, virtualization, aws-certified-solutions-architect-associate, cloud-security, ec2-user-data, ec2-instance, ec2-monitoring

---

## Getting started with EC2

### **Step 1 : Launch an EC2 Instance**

1. **Sign in to the AWS Management Console**:
    
    * Navigate to the [AWS Management Console](https://aws.amazon.com/free/?trk=14a4002d-4936-4343-8211-b5a150ca592b&sc_channel=ps&s_kwcid=AL!4422!3!453325184782!e!!g!!aws&ef_id=CjwKCAjw2OiaBhBSEiwAh2ZSP6GOy7HtywPPXwpgkQbe-PpwtZMoU_l0dDaBKkG59c0nhySUVZdiCBoCHEIQAvD_BwE:G:s&s_kwcid=AL!4422!3!453325184782!e!!g!!aws&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all).
        
    * Sign in with your AWS account credentials.
        
    * First, you have to log in via root user.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716288794351/ec8dd2fa-0e76-4fbd-8f7e-dfb104a8be31.png align="center")
    
2. **Open the EC2 Dashboard** :
    
    * In the Services menu, find and select "EC2" under the "Compute" category or you can search on top box.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716288879382/e83cc5b9-f912-443d-892a-9da09e2ec6e6.png align="center")
        
3. **Launch an Instance** :
    
    * Click on "Launch Instance."
        
    * Give instance name and add tags. Tags are optional but useful for managing your resources.
        
    * Choose an Amazon Machine Image (AMI). For beginners, the Amazon Linux 2 AMI is a good choice or ubuntu as it is "free-tier eligible" .
        
    * Select an instance type. The t2.micro instance is free-tier eligible and suitable for small workloads and also you can see free-tier lable on the right hand side as shown in the snip.
        
    * Configure instance details. For basic usage, you can leave the default settings.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716289310357/72cac4b8-f5aa-4254-855a-d025c696a1e1.png align="center")
        
    * Create a new key pair or use an existing one if you have. The key pair is essential for accessing your instance securely. Download the private key file (.pem) and keep it safe.
        
    * It helps to login into the instances using key-pairs, in which AWS manages the public key, and the user operates the private key. You cannot access instances via RDP or SSH (linux) without Key pair.
        
    * There are 20 EC2 instances soft limit per account, you can submit a request to AWS to increase it.
        
    * Configure security groups. Create a new security group with rules to allow SSH (port 22) access from your IP address. This is crucial for connecting to your instance.
        
    * Add storage. By default, an 8 GB root volume is provided, which should be sufficient for getting started.
        
    * Review your settings and click "Launch instance."
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716290097722/d7f66480-6525-4134-8f06-ffc005207fc3.png align="center")
        

### **Step 2 : Connect to Your EC2 Instance**

1. **Using SSH :**
    
    * Open a terminal (Linux/macOS) or use an SSH client like PuTTY (Windows) and navigate to the path where key pair file is downloaded.
        
    * Ensure the private key file (.pem) has the correct permissions :
        
        `chmod 400 /path/to/your-key-pair.pem`
        
    * Connect to your instance using the public DNS name:
        
        `ssh -i /path/to/your-key-pair.pem ec2-user@your-instance-public-dns`
        
    * For PuTTY, you need to convert the .pem file to a .ppk file using PuTTYgen, then use PuTTY to connect.
        
    * You can find these commands when you click the check box of EC2 instance and hit "connect" on top.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716292957813/161e6410-c0f6-4019-914f-455446e5e244.png align="center")
        

### **Step 3 : Manage Your EC2 Instance**

1. **Install Software** :
    
    * Once logged in, you can install software as needed. For example, to update the package lists and install Docker :
        
        `sudo apt update -y`
        
        `sudo apt install docker.io -y`
        
2. **Monitor and Maintain** :
    
    * Use the EC2 Dashboard to monitor the instance's performance, CPU usage, and network activity.
        
    * Set up alarms and notifications using CloudWatch to keep track of your instance's health.
        

### **Step 4 : Terminate the Instance ( When No Longer Needed )**

* If you no longer need the instance, make sure to terminate it to avoid incurring charges.
    
* In the EC2 Dashboard, select your instance, click on "Instance State," and then "Terminate instance".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716293749315/4c845f67-bc4e-4c1a-94f4-8530bfccd367.png align="center")
    

### **Monitoring EC2 Status**

* **Automatic Checks** : AWS EC2 instances perform automated status checks every minute by default.
    
* **Purpose** : These checks help detect any hardware or software issues with the running instance.
    
* **Built-in Feature** : Status checks are an integral part of AWS EC2 and cannot be modified, deleted, or disabled.
    
* **Monitoring with CloudWatch** : EC2 sends its metrics to AWS CloudWatch every five minutes by default.
    
* **Detailed Monitoring** : For more frequent monitoring, detailed monitoring can be enabled, which sends metrics every minute. This service is available at an additional cost.
    
* **Cost Considerations** : You are not charged for EC2 instances that are stopped. However, charges still apply for any attached EBS (Elastic Block Store) volumes.
    

### Terminate Instance

* **Instance State Changes** : When you terminate a running instance, its state transitions from Running to Shutting Down, and finally to Terminated.
    
* **No Charges During Shutdown** : You do not incur charges while the instance is in the Shutting Down or Terminated states.
    
* **EBS Root Volume** : By default, the EBS root device volume is automatically deleted when the EC2 instance is terminated.
    
* **Additional Volumes** : Any additional attached volumes (non-root) are not deleted by default and persist after the instance is terminated.
    
* **Modifying Volume Behavior** : You can change the deletion behavior of EBS volumes by adjusting the "Delete on Termination" attribute during instance launch or while the instance is running.
    
* **Termination Protection** : Enable "EC2 Termination Protection" to prevent accidental termination of your instances.
    

### **User Data for Instances :**

* **Custom Launch Scripts** : User Data allows you to provide scripts to be executed during instance boot, tailored to your specific requirements.
    
* **Size Limitation** : User Data is limited to 16kb in size, ensuring efficiency and simplicity.
    
* **Modification Process** : To change User Data, you need to stop the EC2 instance first, ensuring smooth updates without disruptions.
    
* **Encryption Considerations** : User Data is not encrypted on EC2 bare metal instances, providing direct access to hardware resources.
    
* **Non-Virtualized Environment** : In bare metal instances, the operating system runs directly on the hardware, offering high performance and minimal overhead.
    
* **Suitability for Critical Applications** : Bare metal instances like M5.metal, C5.metal, R5b.metal, X1e.metal, and u-12tb1.metal are suitable for running licensing-restricted, tier-1 business-critical applications.
    
* **Example** : For instance, M5.metal, C5.metal, R5b.metal, X1e.metal, and u-12tb1.metal are examples of bare metal instances ideal for hosting demanding workloads.
    
* You can find user data environment in "Advance Details" during launching an instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716297846803/7a4f71eb-3f2d-450d-9369-69a88d12aca1.png align="center")
    

### **EC2 Metadata :**

* **Instance Information** : EC2 metadata provides useful data that can help configure or manage your instance.
    
* **Examples of Metadata** : This includes IPv4 addresses, IPv6 addresses, DNS hostname, AMI ID, instance ID, instance type, local hostname, public keys, and security groups.
    
* **Access Requirements** : You can only view metadata from within the instance itself, requiring you to log in to the instance.
    
* **Security Note** : Metadata is not encrypted; anyone with access to the instance can view this information.
    
* **How to Access** : To view instance metadata, use the following request EC2 instance :
    
    `curl http://169.254.169.254/latest/meta-data/`.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716296770423/5619dc72-3f3b-428d-a3b3-3849bb83cacf.png align="center")
    
    * You can retrieve specific metadata by appending the desired attribute to the URL. For example, to view the instance type :
        
        `curl http://169.254.169.254/latest/meta-data/instance-type`
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716297048503/80e7d75c-d954-412b-a38c-295282dc31da.png align="center")
        

## Conclusion

1. **Easy Instance Launch** : Launching an EC2 instance is straightforward, involving a few simple steps to configure and start your virtual server.
    
2. **Secure Access** : Using key pairs ensures secure access to your instance, preventing unauthorized logins.
    
3. **Flexible Management** : EC2 provides various tools to manage, monitor, and maintain your instances efficiently.
    
4. **Cost Efficiency** : You only pay for what you use, with options to minimize costs by stopping instances and managing storage effectively.
    
5. **Built-in Protection** : Features like automated status checks and termination protection help keep your instances running smoothly and avoid accidental data loss.
    
6. **Custom Launch Scripts** : Utilizing User Data allows for the execution of custom scripts during instance boot, tailored to specific requirements, enhancing instance functionality.
    
7. **Enhanced Security** : EC2 metadata provides valuable instance information but should be accessed securely from within the instance to prevent unauthorized access and maintain data integrity.
    
8. **Bare Metal Instance Benefits** : Bare metal instances offer a non-virtualized environment with direct hardware access, ideal for running high-performance, critical applications with minimal overhead and increased reliability.