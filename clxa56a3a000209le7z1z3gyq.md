---
title: "AWS Network & Security { Part - II }"
datePublished: Tue Jun 11 2024 08:30:15 GMT+0000 (Coordinated Universal Time)
cuid: clxa56a3a000209le7z1z3gyq
slug: aws-network-security-part-ii
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1717337860364/ea7d82a2-0c97-4b23-887a-6c6939292c3c.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1717945650286/501efa42-ebf4-4e12-a91c-2c3e11d34d9c.png
tags: cloud, aws, cloud-computing, devops, best-practices, scalability, sre, aws-security, aws-certified-solutions-architect-associate, devops-articles, devopscommunity, ec2-instance, aws-elastic-ip

---

## What is an Elastic IP?

A static IPv4 address created specifically for dynamic cloud computing in Amazon Web Services (AWS) is called an elastic IP. An Elastic IP stays constant, in comparison to ordinary IP addresses, which can change if you restart your instance. This means you can keep your AWS resources IP address constant. Applications that depend on a fixed IP address for reliable communication will find this functionality especially helpful.

## **Key Features of Elastic IP**

* **Static IP Address :** Stays the same even when you restart and stop your instance.
    
* **Flexibility:** Transfer the Elastic IP to a different instance in the same AWS region with ease.
    
* **Fault-Tolerance** : You can rapidly remap the Elastic IP to a standby instance in the event that an instance becomes unavailable.
    
* **Reverse DNS** : Enables reverse DNS support, which simplifies the management of email delivery and other services.
    
* **Cost Management** : Elastic IP is only billed when it is not linked to an instance, which promotes economical use.
    

## How Elastic IP Works

* A static IP address is linked to your AWS instance in order for elasticity IPs to function.
    
* Your account's IP address is reserved by AWS when you provide an Elastic IP.
    
* After that, you can link any of your instances that are located in the same area to this Elastic IP.
    

## Creating an Elastic IP

1. **Log in to AWS Management Console** : Open the EC2 Dashboard.
    
2. **Navigate to Elastic IPs :** In the left-hand menu, click on "Elastic IPs" under "Network & Security".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717943524864/379677b2-685e-4aa8-bf57-9fe0913a6597.png align="center")
    
3. **Allocate New Address** : Click on the "Allocate Elastic IP address" button.
    
4. **Allocate** : Click the "Allocate" button, and your Elastic IP will be created.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717943705120/9b661e9f-e71a-4dd3-97aa-193e7d6e38fa.png align="center")
    

To associate this Elastic IP with an instance :

1. **Select Elastic IP** : Click on the newly created Elastic IP.
    
2. **Associate Address** : Click the "Actions" button and select "Associate Elastic IP address".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717943874663/0a9d4c5c-7c5d-437b-a872-62f9490e5ba5.png align="center")
    
3. **Choose Instance** : Select the instance you want to associate the IP with.
    
4. **Associate** : Click the "Associate" button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717944012065/01ed8b1a-4495-4bbb-aa15-7dfeaaf33a87.png align="center")
    
5. You can check the info related to instance like instance ID, private IP address which is associated with the instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717944221998/d7dd80ea-2cf9-4ee3-8de8-2c4e6370ab05.png align="center")
    
6. Select the instance and we can also check which Elastic IP is associated with this instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717944361185/55dfef53-80a9-4949-8cb2-643ef34fe56e.png align="center")
    

## Best Practices for using Elastic IP

* **Minimize Idle Addresses** : To prevent extra fees, only utilize elastic IPs when absolutely essential.
    
* **Automate Failover** : To increase application availability, use automated failover techniques with elastic IPs.
    
* **Monitor Usage** : To guarantee effective allocation, evaluate your Elastic IP usage on a regular basis.
    
* **Security** : Protect instances connected to Elastic IPs by implementing security groups and network ACLs.
    
* **Documentation** : For better administration, keep track of your Elastic IP assignments and record any modifications.
    
* **Regular Audits** : Make sure your Elastic IPs are being used effectively by doing routine audits of them.
    
* **Cost Management** : We can't release the elastic IP in that way, however we can release any unneeded Elastic IPs to save needless expenses. Before we can release it, we must first disassociate the elastic IP address by going to the VPC service.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717944896308/f7da9cef-d28c-48b6-a481-c694767f9092.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717945047404/c1071f79-d9c1-41ff-b268-bcc03de2e91d.png align="center")
    
* **Naming Conventions** : To make tracking and management of Elastic IPs easier, use unique naming standards.
    
* **Tagging** : To efficiently organize and manage your Elastic IPs, use tags.
    

## Use Cases

* **Web Hosting** : To guarantee that people can always access your website, provide your web server a stable IP address.
    
* **Disaster Recovery** : In the event that the primary instance fails, quickly move an Elastic IP to a backup instance.
    
* **Mail Servers** : By keeping a fixed IP address for reverse DNS lookup, you can guarantee email delivery.
    
* **Load Balancing** : Several instances behind a load balancer can have Elastic IPs assigned to them for dependable traffic control.
    

## Conclusion

* **Static and Reliable** : Elastic IPs give your apps a constant, reliable IP address, guaranteeing uninterrupted connectivity.
    
* **Easy Reassignment** : Enhancing flexibility, an Elastic IP can be quickly moved to a different instance if necessary.
    
* **Improved Uptime** : In the event that the primary instance fails, quickly reassign an Elastic IP to a backup instance to reduce downtime.
    
* **Cost-Effective** : Elastic IPs are only billed for when they are not in use, encouraging effective resource management.
    
* **Security** : To protect your instances, make use of security features like network ACLs and security groups.
    
* **Efficient Management** : To improve organization and cost control, tag your Elastic IPs, follow specific naming guidelines, and audit them on a regular basis.
    

## References

* [Elastic IP](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html)