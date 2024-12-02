---
title: "AWS Load Balancing { Part - I }"
datePublished: Mon Dec 02 2024 04:04:17 GMT+0000 (Coordinated Universal Time)
cuid: cm46iag9r000p09l83ksoh70l
slug: aws-load-balancing-part-i
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1733109162625/1d9dae19-e2bf-46ef-acf7-b572349cd62b.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1733112197279/397c6cf9-8237-4725-bebb-c10a0f75c0ea.png
tags: cloud, ec2, aws, cloud-computing, devops, aws-certified-solutions-architect-associate, devops-articles, network-load-balancer, devops-journey, devopscommunity, aws-elastic-load-balancer, applicationloadbalancer, aws-elb

---

## What is Elastic Load Balancing?

* Incoming traffic is uniformly distributed among several targets, such as EC2 instances, containers, or IP addresses, thanks to elastic load balancing.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733111536339/aee8ec61-5519-47f8-8cb4-ac18ab1b9c66.png align="center")
    
* For increased redundancy and dependability, it operates across one or more Availability Zones.
    
* Keeps a close eye on the condition of every registered target to make sure traffic is only sent to healthy ones.
    
* Automatically modifies the load balancer's capacity to accommodate variations in traffic demand.
    
* Guarantees high availability and seamless scaling for applications with varying traffic.
    

## Benefits

* To distribute the workload, a load balancer divides traffic among several servers.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733111578102/09c26b56-fbb3-4012-a062-26eb81019cbd.jpeg align="center")
    
* It enhances your apps availability and dependability.
    
* Servers can be added or removed as needed without affecting the traffic flow of your application.
    
* Health checks make ensuring that the load balancer only sends requests to servers that are in good health.
    
* Your servers can concentrate on other duties by using load balancers to handle encryption and decryption.
    

## How ELB works?

* Across several Availability Zones, a load balancer controls incoming client traffic and directs it to registered targets, such as EC2 instances.
    
* It only sends traffic to destinations that are healthy after keeping an eye on their condition.
    
* The load balancer will cease transmitting traffic to a target until it recovers if it becomes unhealthy.
    
* Listeners, which provide the protocol and port for incoming and outgoing traffic, are used to configure a load balancer.
    
* Connections between the load balancer and the targets and between clients and the load balancer are managed by listeners.
    
* Four different kinds of load balancers are available with AWS Elastic Load Balancing:
    
    * **Application Load Balancers (ALB):** For HTTP/HTTPS traffic and advanced routing.
        
    * **Network Load Balancers (NLB):** For high performance with TCP/UDP traffic.
        
    * **Gateway Load Balancers (GWLB):** For controlling external equipment, such as firewalls.
        
    * **Classic Load Balancers (CLB):** A legacy option for basic load balancing (previous generation).
        
* Target groups are used by ALBs, NLBs, and GWLBs to control and direct traffic to particular targets.
    
* CLBs are regarded as a previous generation since they register instances directly with the load balancer rather than through target groups.
    

### What is an Application Load Balancer?

* In the OSI architecture, an Application Load Balancer (ALB) functions at the application layer, or Layer 7.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733111891936/20e9a1cc-736f-4956-ba7d-9b17c13ff575.png align="center")
    
* Upon receiving a request, the load balancer determines which listener rule to apply by prioritizing the rules.
    
* The load balancer directs traffic to the relevant target group based on the chosen rule.
    
* Depending on the requests content (such as URL paths), you can set up listener rules to direct traffic to various target groups.
    
* Even if a target is a member of more than one group, routing is managed independently for each target group.
    
* Although round robin is the default routing mechanism, you can select the least number of pending requests.
    
* The load balancer allows targets to be added or withdrawn without impacting the request flow.
    
* When traffic to your application rises or falls, Elastic Load Balancing automatically adjusts the load balancer.
    
* It is possible to set up health checks to guarantee that only healthy targets receive traffic.
    

### What is a Network Load Balancer?

* Operating at Layer 3 of the OSI model, a Network Load Balancer (NLB) has the capacity to process millions of requests per second.
    
* The NLB tries to create a TCP connection on the designated port after receiving a connection request, choosing a target from the target group according to the default rule.
    
* A load balancer node is created inside an availability zone when it is enabled. By default, unless cross-zone load balancing is enabled, traffic is exclusively dispersed within the same Availability Zone.
    
* By distributing traffic throughout all enabled Availability Zones, cross-zone load balancing enhances load distribution.
    
* Enable several Availability Zones and make sure each target group has targets in each zone to improve fault tolerance.
    
* The IP address for that subnet is deleted from DNS if a target group loses a healthy target in an Availability Zone, although traffic can still be routed by the load balancer in other zones.
    
* The load balancer chooses a target for TCP traffic using a flow hash method that takes into account different connection information (protocol, IPs, ports, and sequence numbers).
    
* The flow hash technique for UDP traffic is based on the protocol, IPs, and ports, guaranteeing that every flow is consistently sent to the same destination.
    
* Each configured Availability Zone has a network interface created by Elastic Load Balancing, which is utilized to provide each node a static IP address.
    
* You have the option to assign an Elastic IP address to every subnet when building a load balancer that faces the network.
    
* You provide the target type (such as EC2 instances, IP addresses, or an Application Load Balancer) when creating the target group, which affects target registration and client IP protection.
    
* Elastic Load Balancing adapts seamlessly to variations in application traffic, and you can add or delete targets from your load balancer without disrupting traffic flow.
    
* By keeping an eye on targets health, health checks make sure that only healthy ones receive traffic.
    

### What is a Gateway Load Balancer?

* Gateway load balancers assist in the deployment, scaling, and administration of virtual appliances such as intrusion detection systems and firewalls.
    
* It distributes traffic to virtual appliances and serves as a single point of entry and exit for all traffic, expanding in response to demand.
    
* Handles all IP packets across ports and forwards traffic in accordance with listener rules while operating at Layer 3 (network layer) of the OSI model.
    
* Guarantees **flow stickiness** to particular appliances by employing the 2-, 3-, or 5-tuple approach.
    
* Exchanges data between registered virtual appliances and the Gateway Load Balancer via the **GENEVE protocol** on port 6081.
    
* Secure traffic exchange between VPCs is made possible by **Gateway Load Balancer endpoints**, which guarantee private communication between servers and appliances across VPC boundaries.
    
* The virtual appliances are registered with a target group when the load balancer is deployed in the same VPC.
    
* Route tables are used to control traffic to and from the Gateway Load Balancer endpoint.
    
* Through the Gateway Load Balancer, traffic moves from the service consumer VPC to the service provider VPC and back again.
    
* In order to configure the Gateway Load Balancer endpoint as the next hop in the route table, the endpoint and application servers need to be on different subnets.
    

## **Availability Zones and load balancer nodes**

* When a load balancers availability zone is enabled, a load balancer node is created in that zone.
    
* Traffic will not reach targets that are registered in an Availability Zone unless the zone is also activated.
    
* Make sure there is at least one registered target in each activated Availability Zone for optimal efficacy.
    
* To increase reliability, it is advised that all load balancers have several Availability Zones enabled.
    
* At least two Availability Zones must be enabled for Application Load Balancers.
    
* In the event that one Availability Zone is inaccessible or does not have healthy targets, this configuration guarantees that traffic can still be routed.
    
* When an Availability Zone is disabled, the load balancer stops sending traffic to the targets, but the targets are not deregistered.
    

## Best Practices for ELB

* To increase availability and fault tolerance, enable several Availability Zones.
    
* To guarantee that traffic is only sent to healthy instances, set up health checks for each target.
    
* To dynamically modify the number of targets in response to traffic demand, integrate your load balancer with Auto Scaling.
    
* Your application servers will be less burdened if SSL/TLS decryption is offloaded to the load balancer.
    
* Limit which resources can communicate with your load balancer by implementing strong security group restrictions.
    
* Turn on access logs to keep an eye on traffic trends and record complete details about incoming requests.
    
* Set up alerts for any problems and keep an eye on your load balancer's health and performance with AWS CloudWatch.
    
* Applications that need users to be redirected to the same server for the duration of their session should use session stickiness, also known as session affinity.
    
* To better organize and manage traffic, route it to various target groups using hostnames or URL routes.
    
* Network load balancers can distribute traffic evenly among all targets in several zones by turning on cross-zone load balancing.
    
* To minimize resource utilization and prevent holding pointless connections open, set the proper idle timeouts.
    
* Make sure your target groups accurately represent the state of your infrastructure by reviewing and updating them on a regular basis.
    
* Use AWS Web Application Firewall (WAF) together with your load balancer to defend against frequent online threats and vulnerabilities.
    

## Use Cases

* **Web Applications** : To improve performance and uptime, use ELB to split up web traffic among several web servers for load distribution and high availability.
    
* **E-Commerce Platforms** : By allocating load among several instances and automatically modifying resources in response to demand, ELB assists in scaling web traffic during periods of high shopping demand.
    
* **Microservices Architectures** : ELB can improve the management of complicated applications in a microservices context by directing traffic to the relevant microservice based on hostnames or URL routes.
    
* **Hybrid Cloud Deployments** : ELB ensures smooth integration by distributing traffic between on-premises servers and cloud services in hybrid cloud situations.
    
* **Secure Online Services** : Payment information and other sensitive client data are securely handled by outsourcing SSL/TLS encryption and decryption to ELB without affecting server performance.
    

## **Conclusion**

* By effectively distributing traffic among several resources, Elastic Load Balancing (ELB) improves application performance and availability.
    
* It ensures that your infrastructure adjusts without human intervention by scaling automatically to match variations in traffic.
    
* ELB improves the dependability and fault tolerance of your applications by performing health checks and directing traffic only to healthy targets.
    
* Various load balancer kinds, such as ALB, NLB, and GWLB, allow you to optimize traffic routing according to the particular requirements of your application.
    
* Your applications will continue to be robust, safe, and economical if you follow best practices like turning on multiple Availability Zones and integrating with Auto Scaling.
    

## References

* [AWS Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html)