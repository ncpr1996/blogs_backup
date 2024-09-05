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

* A virtual private cloud, or VPC, is an AWS-powered virtual network that mimics the architecture of a traditional data center network.
    
* For a single client, a VPC functions as a virtual data center network within AWS.
    
* It makes sense for it to be separated from other virtual networks on the AWS cloud.
    
* Up to five VPCs and 200 subnets each can be created per region.
    
* Elastic IPs can be assigned in maximum of five.
    
* Security groups, NACL, and DHCP are automatically produced when a VPC is setup.
    
* A VPC can only exist in one AWS region; it cannot extend to several regions.
    
* Once a VPC is formed, its CIDR block range cannot be changed.
    
* One must create a new VPC in order to use a different CIDR size.
    
* A VPC's subnets can't cross over.
    
* AWS China and GovCloud regions excluded, you can add new IP address ranges to your VPC to increase its CIDR.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720347879384/8bd88eb6-e0ca-41d1-b5d1-5d827d9ebf48.png align="center")

## Types of AWS VPC

### Default VPC

* Created automatically when an account is created in each AWS region.
    
* Default configurations for the Network ACL (NACL), security group, route table, and CIDR block are included.
    
* For internet access, it comes with an internet gateway by default.
    

### Custom VPC

* Created by the Amazon account owner.
    
* The Custom VPC's CIDR block is selectable by the AWS user.
    
* Network ACL (NACL), route tables, and its own default security group are included.
    
* Does not come with an internet gateway by default; if one is required, one must be made manually.
    

## Features of VPC

### CIDR (**Classless Inter-Domain Routing)**

* The range of IP addresses used in a VPC can be specified using the CIDR approach.
    
* It is stated as an IP address (for example, 10.0.0.0/16) followed by a slash and a number.
    
* Figures out how many IP addresses are available in the VPC.
    
* Makes IP address distribution and management more effective.
    
* A 10.0.0.0/16 CIDR block can contain up to 65,536 IP addresses.
    
* Specifies how big the virtual network can be and how much AWS capacity it has.
    

**Understanding the IP Address** :

* An IP address is an unique numerical identifier that is given to every device linked to a computer network that communicates via the Internet Protocol.
    
* It uses a binary address to locate a device within a network.
    
* Four decimal places, separated by a period, are used to indicate an IPv4 address (e.g., 192.168.1.1).
    
* An octet (eight bits) of the address is represented by each integer in binary form. For example, 192 = 11000000.
    
* For IPv4, an IP address has a total of 32 bits.
    
* Binary representation is used for each octet (for example, 10.0.0.0), where each digit is a bit (0 or 1).
    
* I'm going to write about networking in further detail in a future blog post.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720355642121/6e44d13b-c869-4ee5-a8c4-06c304f54be7.png align="center")

**CIDR Notation** :

* In CIDR notation, the number after the slash (e.g., /16) represents the number of bits utilized for the network portion of the address.
    
* Host addresses on that network are stored in the remaining bits.
    

**Calculating the Number of IP Addresses** :

* The notation /16 in CIDR indicates that the network part uses the first 16 bits.
    
* For the subnet 10.0.0.0/16 :
    
    * In the first 16 bits (10.0), the network is defined.
        
    * That network's remaining 16 bits (0.0) are accessible for use with particular addresses.
        

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

* Uses an internet gateway to route its traffic.
    
* For internet communication, instances need an Elastic IP or public IPv4 address.
    

**Private Subnet :**

* Does not have a path to an internet gateway.
    
* Usually utilized in situations where direct internet access is not required.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720355894516/dbeecdbe-c3ee-43b1-8132-36b3b345048f.png align="center")

**VPC Creation :**

* Demands the specification of an IPv4 CIDR block, such as 10.0.0.0/16 to 10.0.0.0/28.
    
* A subnet's first four and last IP addresses are set aside for future use, routers, and DNS servers, among other things.
    

**Internet Access :**

* Instances in public subnets can send outbound traffic to the internet.
    
* Instances in private subnets cannot directly access the internet.
    

**Reserved Addresses :**

* Within a VPC, AWS reserves particular IP addresses.
    
* Example reservations include addresses for routers, DNS servers, and future use.
    
    * **10.0.0.0** - Network address
        
    * **10.0.0.1**\- reserved by AWS for the VPC router
        
    * **10.0.0.2** - reserved by AWS the IP address of DNS server
        
    * **10.0.0.3** - reserved for future use
        
    * **10.0.0.255** - broadcast address
        
    
    Note : AWS reserves the broadcast address in a VPC, even though AWS does not support broadcast functionality within VPCs.
    

### Implied Router and Routing Table

**Central Routing Function** :

* Manages the routing between and within the various Availability Zones (AZs) of the VPC.
    
* Enables external communication by connecting the internet gateway to the virtual private cloud.
    

**Route Table Limits** :

* Supports up to 200 route tables per VPC.
    
* Each route table can contain up to 50 route entries.
    

**Subnet Association** :

* There can only be one route table linked to each subnet at once.
    
* The default VPC route table is linked to subnets in the absence of an association specification.
    

**Management and Customization** :

* Allows editing of the main route table.
    
* The main route table cannot be deleted, but it can be manually replaced by a custom route table.
    
* Once a custom route table becomes the main route table, the former main table can be deleted.
    

**Multiple Subnet Association** :

* Enables the sharing of a route table among several subnets, which simplifies network administration.
    

### Internet Gateway

**Overview :**

* Serves as an internet-based virtual router, linking a VPC to the internet.
    
* Permits connectivity between the internet and instances within the VPC.
    

**Default VPC Configuration** :

* An internet gateway is pre-configured in the default VPC to provide instant access to the internet.
    

**Creating a New VPC** :

* To allow internet connectivity, you have to directly attach an internet gateway while creating a new VPC.
    

**Route Table Configuration** :

* To enable outbound internet access, make sure the subnet's route table has a route pointing to the internet gateway.
    

**Network Address Translation (NAT)** :

* Makes it possible for instances with private addresses to access the internet by performing NAT (Network Address Translation) between private and public IPv4.
    

**IP Version Support** :

* Supports both IPv4 and IPv6 addressing for comprehensive connectivity options within the VPC.
    

### NAT Gateway

**Overview :**

* Enables instances in a private subnet to access the internet or other AWS services while preventing inbound connections from the internet.
    

**Cost Considerations** :

* A NAT gateway's creation and use are subject to fees, which also include hourly usage and data processing rates.
    
* There can also be additional Amazon EC2 data transfer fees.
    

**Setup Requirements** :

* The public subnet that a NAT gateway will sit on must be specified when it is created.
    
* At the time of creation, the NAT gateway needs to be connected to an Elastic IP address.
    

**Public IP Management** :

* No need to assign public IP addresses directly to instances in the private subnet.
    

**Route Table Configuration** :

* Change the route table linked to your private subnets so that outbound connections are routed via the NAT gateway.
    
* Instances on private subnets can now connect to the internet thanks to this configuration.
    

**Deleting and Disassociation** :

* A NAT gateway's Elastic IP address is disconnected upon deletion, yet it stays in your AWS account without being released.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720356333478/b383731b-53e2-4047-b1b7-8ca99223b54c.png align="center")

### **Security Groups**

* [You can check out this blog to understand Security Groups.](https://devopstour.hashnode.dev/aws-network-security-part-1)
    

### Network Access Control List (NACL)

**Overview :**

* Functions as a security layer for your virtual private network (VPC), controlling traffic entering and leaving one or more subnets in a way similar to a firewall.**Default Configuration** :
    

* A customizable default NACL is included with your VPC.
    
* Allows all inbound and outbound IPv4 traffic at first, as well as IPv6 if necessary.
    

**Custom NACL Creation** :

* Make unique NACLs and link them to particular subnets.
    
* Until rules are applied, custom NACLs initially block all inbound and outbound traffic.
    

**Subnet Association** :

* Each subnet in your VPC needs to have a NACL assigned to it.
    
* Subnets are automatically associated with the default NACL if they are not specifically linked to one.
    

**Association Flexibility** :

* There can be more than one NACL connected to a single subnet, but only one NACL per subnet at a time.
    
* Associating a new NACL with a subnet removes any previous association.
    

**Rule Configuration** :

* NACLs contain sequentially numbered rules that are evaluated starting from the lowest numbered rule.
    
* Rule numbers can range up to 32,766, with recommended intervals of 100 to facilitate future rule insertion.
    

**Operational Scope** :

* Functions at the subnet level, controlling traffic entering and leaving the subnet.
    

**Stateless Operation** :

* NACLs are stateless, requiring explicit allowance for outbound traffic corresponding to allowed inbound traffic.
    

**Rule Types** :

* Permits and deny rules, allowing for more precise control over network traffic.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720356909573/57589656-0265-45d6-a228-134fd297cc8c.png align="center")

### VPC Peering

**Overview** :

* Creates a network link between two VPCs so that data can be routed privately across IPv4 or IPv6.
    

**Smooth Communication** :

* Permits smooth interaction between instances in either VPC as though they were a single network.
    

**Flexibility in Setup** :

* Establish VPC peering connections with other AWS accounts' VPCs or with your own VPCs.
    
* Peering connections can span across different AWS regions.
    

**Functionality** :

* Allows VPCs to communicate directly and securely without requiring traffic to be routed over the internet.
    

### VPC Endpoint

**Overview** :

* Permits private connections to be made between your supported AWS services and VPC.
    
* These services are reachable by instances within your VPC without requiring public IP addresses.
    

**Eliminates Public IP Requirement** :

* Eliminates the requirement for public IP addresses on instances within your VPC in order to access resources in the associated AWS services.
    

**Virtual Device Functionality** :

* Virtual devices known as VPC endpoints allow direct and secure connection between your VPC and AWS services.
    

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

* Virtual network environments that are secure and scalable are offered by AWS VPC.
    
* It is compatible with subnets, security groups, and CIDR blocks, among other flexible networking configurations.
    
* Smooth communication between instances is made possible by VPC, whether for private or public internet access.
    
* Endpoints, VPC peering, and NAT gateways are examples of features that improve network security and flexibility.
    
* AWS infrastructure management that is both secure and efficient is ensured by mastering these essentials.
    

## References

* [AWS VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)