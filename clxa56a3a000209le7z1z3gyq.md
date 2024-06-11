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

An Elastic IP is a static IPv4 address designed for dynamic cloud computing in Amazon Web Services (AWS). Unlike regular IP addresses, which can change if you restart your instance, an Elastic IP remains constant, allowing you to maintain a stable IP address for your AWS resources. This feature is particularly useful for applications that require a fixed IP for consistent communication.

## **Key Features of Elastic IP**

* **Static IP Address :** Remains unchanged, even if you stop and start your instance
    
* **Flexibility:** Easily reassign the Elastic IP to another instance within the same AWS region.
    
* **Fault-Tolerance** : If an instance becomes unavailable, you can quickly remap the Elastic IP to a standby instance.
    
* **Reverse DNS** : Supports reverse DNS, making it easier to manage email delivery and other services.
    
* **Cost Management** : You only pay for the Elastic IP when it is not associated with an instance, encouraging efficient use.
    

## How Elastic IP Works

* Elastic IPs work by associating a static IP address with your AWS instance.
    
* When you allocate an Elastic IP, AWS reserves the IP address for your account.
    
* You can then associate this Elastic IP with any of your instances within the same region.
    
* You can then associate this Elastic IP with any of your instances within the same region.
    

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

* **Minimize Idle Addresses** : Only use Elastic IPs when necessary to avoid unnecessary charges.
    
* **Automate Failover** : Use Elastic IPs with automated failover mechanisms to improve application availability.
    
* **Monitor Usage** : Regularly review your Elastic IP usage to ensure efficient allocation.
    
* **Security** : Implement security groups and network ACLs to protect instances associated with Elastic IPs.
    
* **Documentation** : Keep track of your Elastic IP assignments and document any changes for better management.
    
* **Regular Audits** : Conduct regular audits of your Elastic IPs to ensure they are being used efficiently.
    
* **Cost Management** : Release any unused Elastic IPs to avoid unnecessary costs, but we can't release the elastic IP like that. We have to first Disassociate Elastic IP address by navigate to VPC service and then we can release it.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717944896308/f7da9cef-d28c-48b6-a481-c694767f9092.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717945047404/c1071f79-d9c1-41ff-b268-bcc03de2e91d.png align="center")
    
* **Naming Conventions** : Use clear naming conventions for Elastic IPs to simplify management and tracking.
    
* **Tagging** : Use tags to categorize and manage your Elastic IPs effectively.
    

## Use Cases

* **Web Hosting** : Provide a consistent IP address for your web server, ensuring users can always reach your site.
    
* **Disaster Recovery** : Quickly switch an Elastic IP to a backup instance if the primary instance fails.
    
* **Mail Servers** : Ensure email delivery by maintaining a fixed IP address for reverse DNS lookup.
    
* **Load Balancing** : Assign Elastic IPs to multiple instances behind a load balancer for consistent traffic management.
    

## Conclusion

* **Static and Reliable** : Elastic IPs provide a stable IP address that doesn't change, ensuring consistent connectivity for your applications.
    
* **Easy Reassignment** : You can quickly move an Elastic IP to another instance if needed, enhancing flexibility.
    
* **Improved Uptime** : Quickly reassign an Elastic IP to a backup instance if the primary instance fails, minimizing downtime.
    
* **Cost-Effective** : Only pay for Elastic IPs when they are not in use, promoting efficient resource management.
    
* **Security** : Use security features like security groups and network ACLs to protect your instances.
    
* **Efficient Management** : Regularly monitor and audit your Elastic IPs, use clear naming conventions, and tagging for better organization and cost control.
    

## References

* [Elastic IP](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html)