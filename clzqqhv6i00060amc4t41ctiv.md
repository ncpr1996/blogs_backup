---
title: "AWS Virtual Private Cloud ( AWS VPC ) { Part - II }"
datePublished: Mon Aug 12 2024 08:30:51 GMT+0000 (Coordinated Universal Time)
cuid: clzqqhv6i00060amc4t41ctiv
slug: aws-virtual-private-cloud-aws-vpc-part-ii
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723358034387/4b0e45f4-53f3-4209-99bd-7a71c80fce43.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1723357475449/9343ad00-cc16-4bc7-985e-ef1891cc9539.png
tags: cloud, aws, cloud-computing, devops, vpc, aws-security, aws-vpc, aws-certified-solutions-architect-associate, devops-articles, devops-trends, nacl, devopscommunity, vpc-basics, aws-nacl, aws-network-acl

---

## Introduction

* At the subnet level, you can permit or prohibit particular inbound or outbound traffic using a network access control list (ACL).
    
* To add even more protection, you can utilize your VPC's default network ACL or make a custom one with rules that match your security groups.
    
* There is no extra cost for using network ACLs.
    
* The diagram shows a VPC with two subnets, each having its own network ACL.
    
* The router routes traffic to its specified destination when it enters the VPC (from the internet, another VPC, or a VPN).
    
* Network ACL A controls which traffic can enter or leave subnet 1.
    
* Network ACL B controls which traffic can enter or leave subnet 2.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723357290288/02195e73-521d-4308-99a5-a48fca53819e.png align="center")
    

## Network ACL Essentials

* You can change the default network ACL that is automatically included in your VPC. It permits all incoming and outgoing IPv4 traffic by default, as well as IPv6 traffic if necessary.
    
* To regulate particular incoming and outgoing traffic, you can build a custom network ACL and connect it to a subnet.
    
* Each subnet in your VPC must be linked to a network ACL. If you don't link a subnet to a specific ACL, it automatically uses the default network ACL.
    
* A subnet can only have one network ACL at a time, but you can link one network ACL to several subnets. When you attach a new ACL to a subnet, the old link is broken.
    
* Each inbound and outbound rule in a network ACL has a number between 1 and 32766. Rules are ranked lowest to highest once they are examined. A rule is executed when traffic matches it; further rules are ignored at that point.
    
* It is advised to establish rules in increments of 10, or 100, for example, to make room for additional rules later on.
    
* When traffic enters or exits a subnet, rather than when it is being routed within it, network ACL rules are considered.
    
* Due to their statelessness, network ACLs are incapable of remembering past traffic. Security groups are stateful and remember past traffic; if you allow specific inbound traffic, the response traffic is not automatically allowed.
    
* The Route 53 Resolver is not capable of blocking DNS requests to or from network ACLs. Route 53 Resolver DNS Firewall must be enabled in order to filter DNS requests.
    
* Traffic to the Instance Metadata Service (IMDS) cannot be blocked by network ACLs. See the Amazon EC2 User Guide for information on controlling access to IMDS.
    
* Amazon DNS, DHCP, EC2 instance information, ECS task metadata endpoints, Windows instance license activation, Amazon Time Sync Service, and reserved IP addresses used by the default VPC router are among the services for which network ACLs do not block traffic.
    
* Both the amount of rules per network ACL and the number of network ACLs per VPC have limitations. Check out VPC Quotas.
    

## Amazon VPC Quotas

* [VPC Quotas](https://docs.aws.amazon.com/vpc/latest/userguide/amazon-vpc-limits.html)
    

## Network ACL Rules

* For your VPC, you can make new rules or modify the ones that are already in the default network ACL.
    
* Subnets connected to a network ACL immediately receive updates when changes are made to it.
    
* Parts of a network ACL rule include:
    
    * **Rule number :** Rules are checked starting with the lowest number. Once a match is found, it's applied, ignoring higher-numbered rules.
        
    * **Type :** Specifies the type of traffic (e.g., SSH) or a custom range.
        
    * **Protocol :** Choose any protocol with a standard number (e.g., ICMP).
        
    * **Port range :** The port or port range for the traffic (e.g., 80 for HTTP).
        
    * **Source :** \[Inbound only\] Specifies where the traffic comes from (CIDR range).
        
    * **Destination :** \[Outbound only\] Specifies where the traffic is going (CIDR range).
        
    * **Allow/Deny :** Decides whether to allow or block the traffic.
        
* If you add a rule via command line or API, the CIDR range is automatically adjusted to its standard form. For example, 100.68.0.18/18 becomes 100.68.0.0/18.
    

## Create Network ACL

**Create a new Network ACL**

* **Sign in to AWS Management Console :** Go to the Amazon VPC service.
    
* **Navigate to the "Network ACLs" section :** Find this option on the left-hand menu under "Virtual Private Cloud."
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723354615423/ddfe6239-ca55-4e1b-8993-5badd444e852.png align="center")
    
* **Click "Create network ACL" :** Start the process by selecting this button.
    
* **Select your VPC :** Choose the VPC where you want to create the NACL. First, you have to create a VPC based on your requirement.
    
* **Give your NACL a name :** This is optional but helpful for identification.
    
* **Click "Create network ACL" :** Your new NACL will be created.
    

**Add Rules to the NACL**

* **Select your newly created NACL :** Click on the NACL to configure it.
    
* **Go to the "Inbound Rules" tab :** Click "Edit inbound rules."
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723355126092/90cf6571-e30e-43cf-86a3-c8329e973717.png align="center")
    
* **Click "Add Rule" :** Enter the following details for each rule:
    
    * **Rule number :** Start with 100, and increase in increments (e.g., 110, 120).
        
    * **Type :** Choose the type of traffic (e.g., HTTP, SSH, or All Traffic).
        
    * **Protocol :** Select the appropriate protocol (e.g., TCP, UDP, or All).
        
    * **Port range :** Specify the port or range (e.g., 80 for HTTP).
        
    * **Source :** Enter the source IP range (e.g., 0.0.0.0/0 for all).
        
    * **Allow/Deny :** Decide whether to allow or deny the traffic.
        
* **Click "Save" :** Save the inbound rules.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723356084539/fea092f6-430d-4e7a-bcfd-0e04d144f3e3.png align="center")
    

**Add Outbound Rules**

* **Go to the "Outbound Rules" tab :** Click "Edit outbound rules."
    
* **Click "Add Rule" :** Follow the same steps as for inbound rules, but specify the destination IP range.
    
* **Click "Save" :** Save the outbound rules.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723356132071/5f1f3b10-6080-4d32-a8f8-4392061c86b3.png align="center")
    

**Associate the NACL with a Subnet**

* **Go to the "Subnet associations" tab :** Click "Edit subnet associations."
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723356233300/5573c9b9-9723-4af9-b003-ed8978cc5c82.png align="center")
    
* **Select the subnets :** Choose the subnets you want to associate with the NACL. First, you have to create your own subnets based on your requirements.
    
* **Click "Save" :** The NACL is now linked to your selected subnets.
    

**Review and Test**

* **Review your NACL :** Make sure the rules are correct.
    
* **Test the NACL :** Verify that the traffic is being allowed or denied as expected.
    

## Best Practices

* **Use multiple Availability Zones :** To improve the fault tolerance, scalability, and reliability of your application, create subnets in several Availability Zones.
    
* **Use security groups :** Manage the flow of data to your EC2 instances within your subnets.
    
* **Use network ACLs :** Manage inbound and outbound traffic at the subnet level.
    
* **Manage access :** To manage identity union, users, and roles access to AWS resources in your VPC, utilize Identity and Access Management (IAM).
    
* **Monitor traffic :** To monitor IP traffic entering and leaving your VPC, subnets, or network interfaces, use VPC Flow Logs.
    
* **Identify network access :** To discover unauthorized access to resources in your VPC, use Network Access Analyzer.
    
* **Protect with AWS Network Firewall :** Filter and monitor traffic to and from your VPC.
    
* **Detect threats with Amazon GuardDuty :** Utilize it to spot potential risks, such as keeping an eye on your EC2 instances' VPC Flow Logs.
    
* **Segment your network :** If you want to restrict the explosion radius in the event of a breach, use separate VPCs or subnets for each environment (production, staging, development,).
    
* **Use private subnets :** To reduce your exposure to potential threats, keep key resources within private subnets with no direct internet access.
    
* **Restrict outbound traffic :** To lower the risk of data theft, limit outbound traffic to only that which is required using network ACLs and security groups.
    
* **Use AWS Shield and WAF :** Use AWS Web Application Firewall (WAF) and AWS Shield to defend your apps from DDoS attacks and other online risks.
    
* **Implement automated backups :** To ensure speedy recovery in the event of data loss, regularly backup your data and resources using automated solutions like AWS Backup.
    

## Conclusion

* Subnet-level traffic is managed by a network ACL, which permits or prohibits particular types of traffic.
    
* For more protection, you may either utilize the built-in network ACLs or design your own.
    
* Stateful security groups remember past traffic, while network ACLs do not. This is because they are stateless.
    
* A network ACL's rules are implemented sequentially, beginning with the rule with the lowest number.
    
* Certain AWS services, including as DNS and Instance Metadata Service traffic, cannot be blocked by network ACLs.
    
* To improve VPC security, make use of best practices including multiple Availability Zones, security groups, and VPC Flow Logs.
    

## References

* [**Network Access Control List (NACL)**](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)