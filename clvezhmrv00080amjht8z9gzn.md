---
title: "Introduction to Amazon Web Services"
datePublished: Thu Apr 25 2024 08:30:34 GMT+0000 (Coordinated Universal Time)
cuid: clvezhmrv00080amjht8z9gzn
slug: introduction-to-amazon-web-services
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1713975472780/864c97b9-3a3e-49c2-bc78-5e735d3d9a57.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1713975888241/a022af9e-8212-4eb6-a3ea-f09ce8403d02.png
tags: cloud, aws, technology, paas, saas, cloud-computing, scalability, infrastructure, amazon-web-services, iaas, virtualization, innovation, aws-certified-solutions-architect-associate, cost-optimisation, cloud-security

---

## Introduction

* AWS started in 2006, offering IT services as web services, which we now call cloud computing.
    
* With cloud computing, we don't have to worry about buying servers or other IT stuff in advance.
    
* Instead, we can quickly get hundreds or thousands of servers when we need them.
    
* We only pay for what we use, with no upfront costs or long-term contracts, making AWS cheaper.
    
* Today, AWS is a reliable, scalable, and affordable cloud platform used by many businesses in 190 countries.
    
* It's popular because it keeps up with the latest trends in digital technology.
    
* AWS offers many services like computing and storage.
    
* It has different services like :
    
    * **Infrastructure as a service (IaaS) :** It gives you basic computing resources.
        
    * **Platform as a service (PaaS) :** It offers a platform for building and managing software.
        
    * **Software as a service (SaaS) :** It provides ready-to-use software packages.
        

**Advantages of AWS**

* **Easy Growth** : You can easily adjust your resources as your needs change, so your system always runs smoothly.
    
* **Saves Money** : You only pay for what you use, which means you can avoid big upfront costs and save money in the long run.
    
* **Reliable Service** : AWS is built to stay up and running, so your apps are always available when you need them.
    
* **Keeps Things Safe** : AWS has strong security measures to keep your data and apps safe from hackers and other threats.
    
* **Always Improving** : AWS keeps adding new features, so you can keep your tech up-to-date and try out new ideas without hassle.
    

## History & Evolution of AWS

* **2003** : Chris Pinkham and Benjamin Black proposed selling Amazon's internal infrastructure as a service. They wrote a six-page document and decided to move forward with the idea after reviewing it.
    
* **2004** : Amazon officially launched SQS (Simple Queue Service) in Cape Town, South Africa, where a team introduced the service.
    
* **2006** : AWS launched by Amazon as a platform offering web services, starting with simple storage services (S3) and computing services (EC2).
    
* **2007 :** Over 180,000 developers had signed up for AWS, indicating its rapid adoption and popularity within the developer community.
    
* **2010 :** Amazon.com's retail web services were migrated to AWS, demonstrating the platform's reliability and scalability.
    
* **2011 :** AWS experienced major technical issues, including volume problems with Elastic Block Store (EBS) and service disruptions affecting popular websites like Pinterest and Reddit.
    
* **2012 :** AWS hosted its first customer event, the re:Invent conference, where new products and services were unveiled. However, the platform also faced technical challenges impacting several prominent sites.
    
* **2013 :** AWS introduced certifications for software engineers specializing in cloud computing, further enhancing its credibility and expertise in the industry.
    
* **2014 :** AWS committed to achieving 100% renewable energy usage for its global operations, demonstrating its commitment to sustainability.
    
* **2015 :** AWS surpassed $6 billion in annual revenue, experiencing rapid growth at a rate of 90% per year.
    
* **2016 :** AWS doubled its revenue, reaching $13 billion annually, reflecting its continued expansion and dominance in the cloud computing market.
    
* **2017 :** AWS re:Invent showcased a range of Artificial Intelligence Services, leading to a doubling of revenue to $27 billion annually as businesses embraced AI capabilities.
    
* **2018 :** AWS launched Machine Learning Specialty Certifications, focusing on automating artificial intelligence and machine learning processes, further solidifying its position as a leader in innovative technologies.
    
* **2020** : AWS maintained its market dominance, focusing on global expansion, strategic partnerships, and technological innovation to meet evolving customer demands.
    
* **2021** : AWS further solidified its position as a leading cloud provider, Highlighting customer adoption, environmental efforts, and investment in research and development.
    
* **2022** : AWS remained at the leading of the cloud computing landscape, driving innovation, growth, and sustainability initiatives while continuing to serve millions of customers worldwide.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713973143391/27b60b9e-d9de-4ff8-968b-40b544817db3.png align="center")

## AWS Global Infrastructure

* AWS is a cloud computing platform that you can use anywhere in the world.
    
* It has a global infrastructure, which means it operates in different regions around the world.
    
* Each region has multiple availability zones, which are like separate data centers in that region.
    
* As of 2024, AWS spans across more than 80 availability zones located within 25 geographic regions globally. These zones serve as strategic points for businesses to deploy their applications and services, ensuring Immediate to end-users for optimized performance and reliability.
    

AWS infrastructure comprises several key components designed to ensure reliability and speed :

* Region
    
* Availability Zones
    
* Edge Locations
    
* Regional Edge Caches
    

### Region

**What is a Region ?**

* A Region in AWS is a geographical area where AWS has data centers.
    
* Each Region is completely independent of others and isolated.
    

**Why are Regions important ?**

* Regions allow you to choose the physical location of your resources, like servers and databases.
    
* They enable you to deploy resources close to your users for better performance and compliance with local regulations.
    

**Key Points :**

* Each Region has multiple Availability Zones (AZs) for redundancy and fault tolerance.
    
* AWS services may have different availability or features depending on the Region.
    
* Regions are named descriptively, like us-east-1 (Virginia) or eu-west-1 (Ireland) or ap-south-1 (Mumbai).
    

**Usage :**

* You can select the Region closest to your users to reduce latency and improve performance.
    
* Businesses with global operations can use multiple Regions to ensure high availability and disaster recovery.
    

**Scenario :**

Let's say you have an online store that sells clothes to customers worldwide. You want your website to be fast for everyone, no matter where they are.

* You decide to host your website on AWS, and you have two options for where to put it: US (Virginia) or Europe (Ireland).
    
* If you choose US (Virginia), your website's data will be stored in AWS's data centers on the east coast of the United States.
    
* If you choose Europe (Ireland), your website's data will be stored in AWS's data centers in Ireland.
    

**Here's why Regions matter :**

* **Speed** : If most of your customers are in Europe, putting your website in Europe (Ireland) will make it load faster for them because the data doesn't have to travel as far.
    
* **Reliability** : If there's a problem in one Region, like a power outage or bad weather, your website can keep running from the other Region.
    
* **Compliance** : Some countries have rules about where data can be stored. By choosing the right Region, you can make sure your website follows those rules.
    

So, by picking the right AWS Region, you can make sure your online store is fast, reliable, and follows the rules wherever your customers are.

### Availability Zones

**What are Availability Zones (AZs) ?**

* Availability Zones (AZs) are isolated locations within a region where AWS has its data centers.
    
* Each AZ operates independently of each other but is connected through low-latency links.
    

**Why are they important ?**

* AZs provide redundancy and fault tolerance. If one AZ fails, others continue to operate, ensuring high availability.
    
* They allow you to deploy your applications across multiple locations for better reliability.
    

**Key Points :**

* Each AZ has its own power, cooling, and networking to maintain operations even during failures.
    
* They are designed to withstand natural disasters and other disruptions.
    
* By distributing resources across AZs, you can minimize the impact of localized failures on your applications.
    

**Usage :**

* You can deploy your infrastructure, such as EC2 instances, databases, and storage, in multiple AZs to create highly available and fault-tolerant architectures.
    
* AWS services, such as Amazon RDS, Amazon S3, and Amazon EC2, are designed to work seamlessly across AZs for increased reliability.
    

**Scenario :**

Let's say you have a website running on AWS that people use from all over the world. To make sure it's always available, you set it up in two different places called "Availability Zones." These zones are like separate rooms in the same building.

**Here's how Availability Zones come into play :**

* **Redundancy** : By deploying your application in multiple AZs, you ensure redundancy. If there's a hardware failure, power outage, or other issue affecting one AZ, the application can continue running smoothly from the servers in the other AZ.
    
* **Fault Tolerance** : Let's say there's a sudden spike in traffic that overwhelms the servers in one AZ, causing them to slow down or become unresponsive. The load balancer can automatically redirect traffic to the servers in the other AZ, ensuring uninterrupted service for your users.
    
* **Disaster Recovery** : In the event of a natural disaster or other catastrophic event affecting one AZ, the application can failover to the servers in the unaffected AZ, minimizing downtime and data loss.
    
* **Low Latency** : Since AZs are physically separate but geographically close, they have low-latency connections between them. This means that users accessing your application from different regions will experience minimal delays.
    

By using multiple Availability Zones, the website stays up and works fast, no matter what happens.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713973587908/d54ec1f7-a3f2-4ee6-933e-b85cc32f522b.png align="center")

### Edge Locations

**What are Edge Locations ?**

* Edge Locations are places where AWS's content delivery network (CDN), called Amazon CloudFront, stores copies of your data.
    

**Why are they important ?**

* Edge Locations are strategically located around the world to bring content closer to users, reducing latency and improving speed.
    

**Key Points :**

* Edge Locations are not data centers; they are smaller facilities located in major cities and regions.
    
* They store copies of frequently accessed content, like images, videos, and web pages, to deliver them quickly to users.
    

**Usage :**

* When a user requests content from your website or application, CloudFront delivers it from the nearest Edge Location, reducing the time it takes to load.
    

**Benefits :**

* **Faster content delivery :** Users experience quicker load times and better performance.
    
* **Scalability :** Edge Locations automatically scale to handle fluctuations in traffic and demand.
    
* **Global reach :** With Edge Locations worldwide, your content can reach users in remote areas without sacrificing speed.
    

**Scenario :**

Imagine you have a website with lots of pictures and videos, like an online gallery. People from all over the world visit your site to view these images and videos.

* Instead of storing all your pictures and videos in one place, AWS spreads them out to many places called "Edge Locations." These are like mini storage rooms located in different cities around the world.
    
* Let's say someone in Tokyo wants to see a picture from your website. Instead of fetching that picture from a faraway server, it's already stored in an Edge Location nearby. So, the picture loads quickly, almost instantly.
    
* Now, someone in New York wants to watch a video from your site. Again, the video is stored in an Edge Location close to them, so it starts playing right away without any waiting.
    
* These Edge Locations make your website load faster for everyone, no matter where they are. It's like having copies of your pictures and videos stored in storage rooms all over the world, ready to be delivered to anyone who wants to see them, instantly.
    

### Regional Edge Cache

**What is a Regional Edge Cache ?**

* A Regional Edge Cache is a type of caching node located at the edge of AWS's network, close to users.
    
* It stores frequently accessed content at a broader regional level within the AWS network.
    
* This differs from Edge Locations, which primarily focus on caching content at a smaller, city-level scale.
    

**Why are they important ?**

* Both Regional Edge Caches and Edge Locations are strategically placed to store frequently accessed content closer to users, reducing latency and improving performance.
    
* While Edge Locations primarily focus on caching content at a smaller, city-level scale, Regional Edge Caches extend this caching capability to a broader regional level within the AWS network.
    

**Usage :**

* Users accessing content through Amazon CloudFront are served from Edge Locations, where content is cached based on user demand and popularity.
    
* Regional Edge Caches complement Edge Locations by caching content at a larger scale within the same region, further optimizing content delivery and reducing latency for users across multiple Edge Locations.
    

**Scenario :**

Imagine you have a popular video streaming website hosted on AWS. Users from all over the world visit your website to watch videos.

When a user in New York requests to watch a popular video :

* The request is first directed to the Regional Edge Cache located in the US East (Virginia) region.
    
* The Regional Edge Cache checks if the video is already stored nearby.
    
    * If the video is cached in the Regional Edge Cache, it's delivered quickly to the user in New York, reducing buffering time and providing a smooth viewing experience.
        
    * If the video is not cached in the Regional Edge Cache, the request is forwarded to the nearest Edge Location in New York City.
        

Now, a user in London requests the same video :

* Instead of fetching the video from the origin server in the US, the request is directed to the Regional Edge Cache in the EU (Ireland) region.
    
* The Regional Edge Cache checks if the video is already stored nearby.
    
    * If the video is cached in the Regional Edge Cache in the EU region, it's delivered quickly to the user in London, minimizing latency and ensuring a seamless viewing experience.
        
    * If the video is not cached in the Regional Edge Cache, the request is forwarded to the nearest Edge Location in London.
        

In both cases, if the video is not cached in the Regional Edge Cache, the request is then directed to the nearest Edge Location for caching and subsequent delivery to the user, further optimizing content delivery and reducing latency.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713973703242/e6fa51b9-c2ec-4b1b-9cb3-f3be831fb11b.png align="center")

## Conclusion

* **AWS's Evolution :** AWS has grown into a big cloud company. It cares about customers, making new things, and taking care of the environment.
    
* **Flexibility and Affordability :** With AWS, businesses can change how much they use easily and not pay a lot upfront. This helps them save money and try new things.
    
* **Reliability and Security :** AWS is good at keeping things running and making sure data is safe. They have strong computers and rules to protect data.
    
* **Global Reach and Performance :** AWS helps businesses give their stuff to people everywhere. It makes sure things work well and follow the rules in different places.