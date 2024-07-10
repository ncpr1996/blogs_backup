---
title: "AWS Virtual Private Cloud ( AWS VPC )
{ Part - I }"
seoTitle: "AWS VPC Essentials : Building Secure and Scalable Cloud Networks"
seoDescription: "Learn to build secure and scalable cloud networks with AWS VPC."
datePublished: Wed Jul 10 2024 08:30:54 GMT+0000 (Coordinated Universal Time)
cuid: clyfkysym001n09i85ps2e7ns
slug: aws-virtual-private-cloud-aws-vpc-part-i
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720354356563/d241f49e-3f1d-4ca7-9860-80d0be8ebef2.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1720355280324/00fa967e-39bd-43a4-98e0-5d12a7c870af.png
tags: cloud, aws, cloud-computing, devops, vpc, aws-security, aws-vpc, aws-certified-solutions-architect-associate, devops-articles, devops-trends, vpc-endpoints, vpc-peering, vpcroutes, devopscommunity, vpc-basics

---

## Introduction

* A virtual private cloud (VPC) is a virtual network that mirrors a traditional data center network, utilizing AWS's scalable infrastructure.
    
* A VPC serves as a virtual data center network within AWS for a single client.
    
* It is logically isolated from other virtual networks in the AWS cloud.
    
* You can create up to 5 VPCs per region and 200 subnets per VPC.
    
* A maximum of 5 Elastic IPs can be allocated.
    
* When a VPC is created, DHCP, NACL, and security groups are automatically generated.
    
* A VPC is limited to a single AWS region and cannot span across regions.
    
* The CIDR block range of a VPC cannot be changed once it is created.
    
* To use a different CIDR size, a new VPC must be created.
    
* Subnets within a VPC must not overlap.
    
* You can expand your VPC's CIDR by adding new IP address ranges, except in GovCloud and AWS China regions.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720347879384/8bd88eb6-e0ca-41d1-b5d1-5d827d9ebf48.png align="center")

## Types of AWS VPC

### Default VPC

* Created automatically in each AWS region upon account creation.
    
* Comes with default CIDR block, security group, Network ACL (NACL), and route table configurations.
    
* Includes an internet gateway by default for internet connectivity.
    

### Custom VPC

* Created by the owner of the AWS account.
    
* The AWS user can choose the CIDR block for the Custom VPC.
    
* Comes with its own default security group, Network ACL (NACL), and route tables.
    
* Does not include an internet gateway by default; one must be created separately if needed.
    

## Features of VPC

### CIDR (**Classless Inter-Domain Routing)**

* CIDR is a method for specifying the range of IP addresses used in a VPC.
    
* It's written as an IP address followed by a slash and a number (e.g., 10.0.0.0/16).
    
* Determines the number of IP addresses available within the VPC.
    
* Allows for efficient allocation and management of IP addresses.
    
* A CIDR block of 10.0.0.0/16 provides up to 65,536 IP addresses.
    
* Defines the size of the virtual network and its capability to accommodate AWS resources.
    

**Understanding the IP Address** :

* An IP address is a unique numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication.
    
* It identifies the location of a device in a network using a binary address.
    
* An IPv4 address is represented as four decimal numbers separated by periods (e.g., 192.168.1.1).
    
* Each number represents an octet (8 bits) of the address in binary form. (e.g., 192 = 11000000).
    
* An IP address consists of 32 bits in total (for IPv4).
    
* Each octet (e.g., 10.0.0.0) is represented in binary, with each digit being a bit (0 or 1).
    
* I will share more information regarding networking in the upcoming blog.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720355642121/6e44d13b-c869-4ee5-a8c4-06c304f54be7.png align="center")

**CIDR Notation** :

* The number after the slash in CIDR notation (e.g., /16) indicates how many bits are used for the network portion of the address.
    
* The remaining bits are used for host addresses within that network.
    

**Calculating the Number of IP Addresses** :

* In CIDR notation, /16 means the first 16 bits are used for the network portion.
    
* For the subnet 10.0.0.0/16 :
    
    * The first 16 bits (10.0) define the network.
        
    * The remaining 16 bits (0.0) are available for specific addresses within that network.
        

**Formula to Calculate IP Addresses**:

* To find the number of IP addresses:
    
    * Take 2 raised to the power of (32 - prefix length).
        
    * In this case, 2^(32 - 16) = 2^16 = 65,536 IP addresses.
        

**Example** :

* For 10.0.0.0/16 :
    
    * The IP addresses range from 10.0.0.0 to 10.0.255.255.
        
    * This provides a total of 65,536 unique IP addresses.
        

### Subnets

**Public Subnet :**

* Routes its traffic through an internet gateway.
    
* Instances require a public IPv4 address or Elastic IP for internet communication.
    

**Private Subnet :**

* Lacks a route to an internet gateway.
    
* Typically used for instances that do not need direct internet access.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720355894516/dbeecdbe-c3ee-43b1-8132-36b3b345048f.png align="center")

**VPC Creation :**

* Requires specifying an IPv4 CIDR block (e.g., 10.0.0.0/16 to 10.0.0.0/28).
    
* First four and last IP addresses of a subnet are reserved (e.g., for routers, DNS servers, future use).
    

**Internet Access :**

* Instances in public subnets can send outbound traffic to the internet.
    
* Instances in private subnets cannot directly access the internet.
    

**Reserved Addresses :**

* AWS reserves specific IP addresses within a VPC.
    
* Example reservations include addresses for routers, DNS servers, and future use.
    
    * **10.0.0.0** - Network address
        
    * **10.0.0.1**\- reserved by AWS for the VPC router
        
    * **10.0.0.2** - reserved by AWS the IP address of DNS server
        
    * **10.0.0.3** - reserved for future use
        
    * **10.0.0.255** - broadcast address
        
    
    Note : AWS reserves the broadcast address in a VPC, even though AWS does not support broadcast functionality within VPCs.
    

### Implied Router and Routing Table

**Central Routing Function** :

* Manages the routing within the VPC and between different Availability Zones (AZs).
    
* Connects the VPC to the internet gateway for external communication.
    

**Route Table Limits** :

* Supports up to 200 route tables per VPC.
    
* Each route table can contain up to 50 route entries.
    

**Subnet Association** :

* Each subnet can be associated with only one route table at a time.
    
* If no association is specified, subnets are linked to the default VPC route table.
    

**Management and Customization** :

* Allows editing of the main route table.
    
* The main route table cannot be deleted, but it can be manually replaced by a custom route table.
    
* Once a custom route table becomes the main route table, the former main table can be deleted.
    

**Multiple Subnet Association** :

* Permits multiple subnets to be associated with the same route table for simplified network management.
    

### Internet Gateway

**Overview :**

* Acts as a virtual router connecting a VPC to the internet.
    
* Enables communication between instances in the VPC and the internet.
    

**Default VPC Configuration** :

* The default VPC comes pre-configured with an internet gateway for immediate internet access.
    

**Creating a New VPC** :

* When creating a new VPC, you must manually attach an internet gateway to enable internet connectivity.
    

**Route Table Configuration** :

* Ensure that the subnet's route table includes a route pointing to the internet gateway for outbound internet access.
    

**Network Address Translation (NAT)** :

* Performs NAT (Network Address Translation) between private and public IPv4 addresses, allowing instances with private addresses to access the internet.
    

**IP Version Support** :

* Supports both IPv4 and IPv6 addressing for comprehensive connectivity options within the VPC.
    

### NAT Gateway

**Overview :**

* Enables instances in a private subnet to access the internet or other AWS services while preventing inbound connections from the internet.
    

**Cost Considerations** :

* Charges apply for creating and using a NAT gateway, including hourly usage and data processing rates.
    
* Additional data transfer charges from Amazon EC2 may also apply.
    

**Setup Requirements** :

* When creating a NAT gateway, you must specify the public subnet where it will reside.
    
* An Elastic IP address must be associated with the NAT gateway during creation.
    

**Public IP Management** :

* No need to assign public IP addresses directly to instances in the private subnet.
    

**Route Table Configuration** :

* Update the route table associated with your private subnets to direct outbound internet traffic through the NAT gateway.
    
* This setup allows instances in private subnets to communicate with the internet.
    

**Deleting and Disassociation** :

* Deleting a NAT gateway disassociates its Elastic IP address but retains the address in your AWS account without releasing it.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720356333478/b383731b-53e2-4047-b1b7-8ca99223b54c.png align="center")

### **Security Groups**

* [You can check out this blog to understand Security Groups.](https://devopstour.hashnode.dev/aws-network-security-part-1)
    

### Network Access Control List (NACL)

**Overview :**

* Operates as a security layer for your VPC, functioning similar to a firewall to regulate traffic in and out of one or more subnets.
    

**Default Configuration** :

* Your VPC includes a default NACL that is modifiable.
    
* Initially permits all inbound and outbound IPv4 traffic, and IPv6 if applicable.
    

**Custom NACL Creation** :

* Create custom NACLs and associate them with specific subnets.
    
* Custom NACLs initially deny all inbound and outbound traffic until rules are added.
    

**Subnet Association** :

* Every subnet in your VPC must be associated with a NACL.
    
* Subnets without explicit NACL associations are automatically linked to the default NACL.
    

**Association Flexibility** :

* A NACL can be associated with multiple subnets, but each subnet can have only one NACL at a time.
    
* Associating a new NACL with a subnet removes any previous association.
    

**Rule Configuration** :

* NACLs contain sequentially numbered rules that are evaluated starting from the lowest numbered rule.
    
* Rule numbers can range up to 32,766, with recommended intervals of 100 to facilitate future rule insertion.
    

**Operational Scope** :

* Functions at the subnet level, controlling traffic entering and leaving the subnet.
    

**Stateless Operation** :

* NACLs are stateless, requiring explicit allowance for outbound traffic corresponding to allowed inbound traffic.
    

**Rule Types** :

* Supports both permit and deny rules, enabling fine-grained control over network traffic.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720356909573/57589656-0265-45d6-a228-134fd297cc8c.png align="center")

### VPC Peering

**Overview** :

* Establishes a network link between two VPCs, allowing private IPv4 or IPv6 traffic routing between them.
    

**Seamless Communication** :

* Enables instances in either VPC to communicate seamlessly as if they were part of the same network.
    

**Flexibility in Setup** :

* Create VPC peering connections between your own VPCs or with VPCs in different AWS accounts.
    
* Peering connections can span across different AWS regions.
    

**Functionality** :

* Enables direct, secure communication between VPCs without needing to route traffic over the internet.
    

### VPC Endpoint

**Overview** :

* Allows private connections between your VPC and supported AWS services.
    
* Instances within your VPC can communicate with these services without needing public IP addresses.
    

**Eliminates Public IP Requirement** :

* Removes the need for instances in your VPC to have public IP addresses to access resources in the connected AWS services.
    

**Virtual Device Functionality** :

* VPC endpoints are virtual devices that enables secure and direct communication between your VPC and AWS services.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720356782219/eddf56a7-9b85-4333-b22d-dbfe554a22fb.webp align="center")

## Difference between security group and NACL

| **SecurityGroup** | **NACL** |
| --- | --- |
| Operates at instance level | Operates at subnet level |
| Supports allow rules only | Supports allow as well as deny rules |
| Stateful, return traffic automatically allowed | Stateless, return traffic must be explicitly allowed by rules |
| Applies to an instance only | Applies to all instances in the subnet |
| Evaluates rules based on all rules combined. | Evaluates rules in numerical order. |

## Conclusion

* AWS VPC provides scalable and secure virtual network environments.
    
* It supports flexible networking configurations like CIDR blocks, subnets, and security groups.
    
* VPC enables seamless connectivity between instances, whether for public internet access or private communication.
    
* Features like NAT gateways, VPC peering, and endpoints enhance network flexibility and security.
    
* Mastering these fundamentals ensures efficient AWS infrastructure management and secure data handling.
    

## References

* [AWS VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)