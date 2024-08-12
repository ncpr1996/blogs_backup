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

* A network access control list (ACL) lets you allow or block specific incoming or outgoing traffic at the subnet level.
    
* You can either use the default network ACL for your VPC or create a custom one with rules similar to your security groups to add extra security.
    
* There is no extra cost for using network ACLs.
    
* The diagram shows a VPC with two subnets, each having its own network ACL.
    
* When traffic enters the VPC (from another VPC, VPN, or the internet), the router directs it to its destination.
    
* Network ACL A controls which traffic can enter or leave subnet 1.
    
* Network ACL B controls which traffic can enter or leave subnet 2.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723357290288/02195e73-521d-4308-99a5-a48fca53819e.png align="center")
    

## Network ACL Essentials

* Your VPC automatically includes a default network ACL that you can modify. By default, it allows all inbound and outbound IPv4 and, if needed, IPv6 traffic.
    
* You can create a custom network ACL and link it to a subnet to control specific inbound and outbound traffic.
    
* Each subnet in your VPC must be linked to a network ACL. If you don't link a subnet to a specific ACL, it automatically uses the default network ACL.
    
* You can link one network ACL to multiple subnets, but a subnet can only have one network ACL at a time. Linking a new ACL to a subnet removes the previous link.
    
* Network ACLs have inbound and outbound rules, each with a number from 1 to 32766. Rules are evaluated in order, starting with the lowest number. Once traffic matches a rule, that rule is applied, and no further rules are checked.
    
* It's suggested to create rules in increments (e.g., 10 or 100) to allow space for new rules if needed.
    
* Network ACL rules are evaluated when traffic enters or leaves a subnet, not while it is routed within the subnet.
    
* Network ACLs are stateless, meaning they don't remember previous traffic. If you allow specific inbound traffic, the response traffic isn't automatically allowed, unlike security groups, which are stateful and remember previous traffic.
    
* Network ACLs can't block DNS requests to or from the Route 53 Resolver. To filter DNS requests, enable Route 53 Resolver DNS Firewall.
    
* Network ACLs can't block traffic to the Instance Metadata Service (IMDS). To manage access to IMDS, refer to the Amazon EC2 User Guide.
    
* Network ACLs don't filter traffic for Amazon DNS, DHCP, EC2 instance metadata, ECS task metadata endpoints, Windows instance license activation, Amazon Time Sync Service, or reserved IP addresses used by the default VPC router.
    
* There are limits on the number of network ACLs per VPC and the number of rules per network ACL. You can check VPC Quotas.
    

## Amazon VPC Quotas

* [VPC Quotas](https://docs.aws.amazon.com/vpc/latest/userguide/amazon-vpc-limits.html)
    

## Network ACL Rules

* You can add or remove rules from the default network ACL or create new ones for your VPC.
    
* Changes to a network ACL are automatically applied to its associated subnets.
    
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

* **Use multiple Availability Zones :** Create subnets in different Availability Zones to make your application more reliable, fault-tolerant, and scalable.
    
* **Use security groups :** Control traffic to EC2 instances within your subnets.
    
* **Use network ACLs :** Manage inbound and outbound traffic at the subnet level.
    
* **Manage access :** Use IAM for managing access to AWS resources in your VPC, including identity federation, users, and roles.
    
* **Monitor traffic :** Use VPC Flow Logs to track IP traffic going to and from your VPC, subnets, or network interfaces.
    
* **Identify network access :** Use Network Access Analyzer to find unintended access to resources in your VPC.
    
* **Protect with AWS Network Firewall :** Filter and monitor traffic to and from your VPC.
    
* **Detect threats with Amazon GuardDuty :** Use it to identify potential threats, including monitoring VPC Flow Logs for your EC2 instances.
    
* **Segment your network :** Use separate VPCs or subnets for different environments (e.g., production, staging, development) to limit the blast radius in case of a breach.
    
* **Use private subnets :** Place sensitive resources in private subnets that do not have direct internet access, reducing exposure to potential threats.
    
* **Restrict outbound traffic :** Use network ACLs and security groups to limit outbound traffic to only what is necessary, reducing the risk of data exfiltration.
    
* **Use AWS Shield and WAF :** Protect your applications from DDoS attacks and other web threats by using AWS Shield and AWS Web Application Firewall (WAF).
    
* **Implement automated backups :** Regularly back up your data and resources using automated solutions like AWS Backup to ensure quick recovery in case of data loss.
    

## Conclusion

* A network ACL controls traffic at the subnet level, allowing or blocking specific traffic.
    
* You can use the default network ACL or create custom ones for added security.
    
* Network ACLs are stateless, meaning they don't remember previous traffic, unlike stateful security groups.
    
* Rules in a network ACL are applied in order, starting from the lowest numbered rule.
    
* Network ACLs can't block certain AWS services like DNS or Instance Metadata Service traffic.
    
* Use best practices like multiple Availability Zones, security groups, and VPC Flow Logs to enhance VPC security.
    

## References

* [**Network Access Control List (NACL)**](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)