---
title: "AWS EC2 Auto Scaling"
datePublished: Sun Dec 22 2024 16:31:49 GMT+0000 (Coordinated Universal Time)
cuid: cm4ztstk5000009jp8by9h3n5
slug: aws-ec2-auto-scaling
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1734884750693/e18aeefe-238c-4c3f-bf96-05f7c161f35c.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1734885068720/4a3ae6d3-57d7-46c5-a8c3-e23b1b2238d6.png
tags: cloud, ec2, aws, cloud-computing, devops, amazon-web-services, aws-certified-solutions-architect-associate, auto-scaling, devops-articles, devops-journey, auto-scaling-aws, devopscommunity, ec2-instance, auto-scaling-group, awsautoscaling

---

## Introduction

* Depending on demand, Amazon EC2 Auto Scaling modifies the quantity of EC2 instances for your application.
    
* "Auto Scaling groups" are created to control groups of EC2 instances.
    
* You can set:
    
    * **Minimum instances**: This is the lowest number the group will ever have.
        
    * **Maximum instances**: This is the maximum number the group will ever have.
        
    * **Desired capacity**: The group will try to keep this amount of instances.
        
* Depending on demand, scaling policies might automatically add or remove instances.
    

Example: An Auto Scaling group with:

* Minimum size: 6 instances
    
* Desired capacity: 8 instances
    
* Maximum size: 14 instances
    
* The instances in this range are modified by scaling policies according to set criteria.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734878356684/6b615018-311f-4106-9ec3-6d8fb9e9e638.png align="center")

## Characteristic of AWS EC2 Auto Scaling

* For simpler scalability and administration, Amazon EC2 Auto scalability groups EC2 instances into Auto Scaling groups.
    
* Launch templates or launch configurations are used by Auto Scaling groups to build up instances.
    

## Key Features

* **Health Monitoring**: Uses EC2 health checks to automatically verify and maintain instance health. To preserve the required capacity, instances that fail or terminate are replaced.
    
* **Custom Health Checks**: For certain application requirements, you can design your own health checks. When these checks are not met, instances are replaced.
    
* **Balanced Capacity**: To improve availability and adaptability, instances are uniformly distributed among several Availability Zones.
    
* **Multiple Instance Types**: Enables the use of various instance types and buying choices (Reserved, On-Demand, and Spot) in a single group to reduce expenses.
    
* **Automated Spot Instance Replacement**: Automatically replaces interrupted Spot Instances. In the event of an interruption, Spot Instances may be replaced by Capacity Rebalancing.
    
* **Load Balancing**: Enables traffic to be distributed evenly among healthy instances by integrating with elastic load balancing. As instances grow, they are automatically registered and deregistered.
    
* **Scalability**: You can manually choose the group size, and it automatically adjusts to handle changing loads.
    
* **Instance Refresh**: Whenever the launch template or AMI is modified, instances are updated via rolling or canary deployment.
    
* **Lifecycle Hooks**: When an instance is launched or terminated, it permits custom actions, which is helpful for event-driven architectures.
    
* **Support for Stateful Workloads**: Uses lifecycle hooks, scale-in protection, or unique termination policies to guarantee that stateful applications continue to run continuously.
    

## Balancing EC2 Instances

* **Auto Scaling Rebalancing**: In the event that EC2 instances are not uniformly distributed between Availability Zones (AZs), Auto Scaling (AS) will automatically rebalance them.
    
* **Rebalancing Action**: Excess instances are removed from other AZs, and new instances are started in AZs with fewer instances.
    

### **Causes of Imbalance**

* AZs can be added or removed from Auto Scaling.
    
* EC2 instances are manually terminated from ASG.
    
* The distribution of instances is impacted by AZs gaining or losing capacity.
    

## Attaching EC2 Instances

### **Conditions for Attachment**

* EC2 needs to be operational.
    
* The EC2 must still be launched using the same AMI.
    
* An instance cannot be included in another ASG.
    
* The instance and the ASG need to be in the same AZ.
    

### Capacity Check

* The request fails if the maximum capacity of the ASG is exceeded by adding an instance.
    

## Detaching EC2 Instances

* **Manual Detachment**: To remove EC2 instances from an ASG, use the CLI or AWS Console.
    
* **Post-Detachment**: Detached instances can be transferred to another ASG or managed separately.
    
* **Desired Capacity Adjustment**: While detaching an instance, you might choose to reduce the ASG's desired capacity.
    
    * If it isn't decremented, ASG will start a new instance.
        
* **Deleting ASG**: When an ASG is deleted, all EC2 instances are terminated and its capabilities are reset to zero.
    
    * Detach the EC2 instances before destroying the ASG in order to preserve them.
        

## Elastic Load Balancer (ELB) Integration:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734884597782/8ff0b2f7-b3b1-40a1-8364-95f83f19d399.webp align="center")

* **Attach ELB to ASG**: As long as it is in the same region and VPC, you can add an ELB to the ASG.
    
* The ELB will automatically register all EC2 instances in the ASG, whether they are new or existing.
    

## EC2 Health Checks

* **Health Check Classification**: Based on EC2 and ELB status checks, EC2 instances are categorized as either healthy or unhealthy.
    
* **Health Check Setup**: Auto Scaling employs EC2 status checks by default.
    
    * It can be set up to use ELB and EC2 health checks.
        
* **Grace Period**: The grace time before doing health checks is set to 300 seconds by default.
    
    * As soon as the instance is in service, its health is checked by setting the grace period to zero.
        
    * During the grace period, any unhealthy state is ignored.
        
* **Unhealthy Instance Handling**: ASG deploys replacements and ends unhealthy instances after the grace period.
    
* **Elastic IP & EBS**: Attach to new instances and manually detach from terminated ones.
    

## Auto Scaling Policies

* **SNS Notifications**: ASG sends email notifications in the following cases:
    
    * An instance is launched.
        
    * An instance is terminated.
        
    * An instance fails to launch.
        
    * An instance fails to terminate.
        

## Combining ASG

* Only the AWS CLI (not the AWS console) can be used for merging.
    
* One multi-AZ ASG can be created by combining many single-AZ ASGs.
    
* **Scale Out**: Start additional EC2 instances.
    
* **Scale In**: Terminate EC2 instances (advised to generate a scale-in event for every scale-out event).
    
* EC2 metrics are sent to **CloudWatch** for monitoring ASG instances.
    
    * **Basic Monitoring**: Every 300 seconds (free).
        
    * **Detailed Monitoring**: Every 60 seconds (chargeable, enabled by default when using AWS CLI).
        

## Standby State

* Within an ASG, EC2 instances can be manually placed in standby mode.
    
* Auto Scaling is still used to manage instances in standby, however
    
    * Like in-service instances, they are billed.
        
    * The EC2 instances that are accessible for workloads are not affected by them.
        
    * Standby instances are not subjected to health checks.
        

## Types of Scaling Policies

* **Manual Scaling**: The quantity of EC2 instances can be manually changed.
    
* **Dynamic Scaling**: According to conditions and alarms in real time.
    
    * **Target Tracking**: Scales the group according to a metric's intended value (such as modifying your home thermostat).
        
    * **Simple Scaling**: Changes the size of the group all at once in response to an alarm (with a 300-second cool-down period).
        
    * **Step Scaling**: Scales based on set steps, with scaling adjustments depending on the size of the alarm breach. It supports a warm-up timer but not cool-down times.
        

## Predictive, Scheduled, and Cycle Scaling

* **Predictive Scaling**: Forecasts daily and weekly load patterns and plans instance adjustments using machine learning.
    
* **Schedule Scaling**: You can schedule scale-out actions for particular times and capacities in order to account for predicted fluctuations in load. The dates and timings of scheduled actions must be unique.
    
* **Cycle Scaling**: It forecasts future scaling requirements using historical data, much like scheduled scaling.
    

## Key Notes

* Alarms and policies are used by scaling policies to decide when to scale.
    
* Scaling changes cannot exceed the ASG's minimum or maximum capacity.
    
* To ensure optimal application performance, **scale-in and scale-out** procedures need to be carefully planned.
    

## Common Use Cases for EC2 Auto Scaling

### **Web Applications**

* Scale web server EC2 instances automatically in response to traffic levels to make sure the application can manage spikes without human assistance.
    

### **Data Processing**

* In order to process huge datasets during specific hours, scale instances according to data processing requirements.
    

### **E-Commerce**

* During periods of heavy demand, such as Cyber Monday or Black Friday, scale instances to make sure the application can handle more users.
    

### **Gaming**

* Scale multiplayer game backend servers automatically in response to player activity to guarantee smooth gaming even during busy periods.
    

## Best Practices for EC2 Auto Scaling

* ELB and Auto Scaling can be used together to evenly divide traffic among your instances.
    

* To quickly identify and replace unhealthy instances, set the proper health check parameters.
    

* As you see the traffic patterns, start with a small minimum number of instances and gradually expand them.
    

* Make sure your scaling policies function as intended under various traffic scenarios by testing them frequently.
    

* Utilize predictive scaling to foresee scaling actions based on historical data for workloads with predictable traffic patterns.
    

## Conclusion

* EC2 Auto Scaling ensures excellent availability and cost-effectiveness by automatically adjusting the number of instances based on traffic.
    
* In order to preserve your application's intended capacity, the service keeps an eye on and replaces unhealthy instances.
    
* To accommodate various use cases and traffic patterns, it provides three different scaling policies: dynamic, manual, and predictive.
    
* For improved management and monitoring, Auto Scaling interfaces with other AWS services like CloudWatch and Elastic Load Balancing (ELB).
    
* EC2 Auto Scaling helps in resource management, performance optimization, and cost reduction by effectively scaling instances.
    

## References

* [AWS EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)