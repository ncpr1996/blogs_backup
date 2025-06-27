---
title: "AWS User Group Chennai Meetup - Session 2: Handle 100x Your Web Traffic Edge Services"
datePublished: Thu Jun 26 2025 13:03:04 GMT+0000 (Coordinated Universal Time)
cuid: cmcde8tak000u02l4b7vx04ou
slug: aws-user-group-chennai-meetup-session-2-handle-100x-your-web-traffic-edge-services
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1750915494598/d32d8723-c4f7-4347-b35d-6e402c2337c8.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1750942869592/84e0993f-faaa-4695-b586-8d60ad3468ff.png
tags: cdn, aws, cloudfront, cloud-computing, amazon-web-services, aws-security, content-delivery-network, edge-computing, webtraffic, aws-user-group-chennai

---

*Continuing from our* [*first session blog*](https://hashnode.com/post/cmcaitr9a000302jx48ejgozx)[*,*](https://www.perplexity.ai/search/your-first-session-url) *here's a detailed breakdown of the second technical session from our AWS User Group Chennai meetup held on May 17, 2025, at Presidio, Chennai.*

The day's second session addressed a crucial subject that all contemporary online applications must deal with: **Handle 100x Your Web Traffic Edge Services**. The presenter, an AWS-certified expert with several credentials, such as Solutions Architect Professional and DevOps Engineer Professional, gave an insightful talk on utilizing AWS edge services to scale web applications to manage 100x traffic.

## **Understanding the Challenge**

The demands placed on modern web applications in terms of cost-effectiveness, security, and performance are unparalleled. Three main use cases where edge computing becomes crucial were highlighted at the start of the session:

* **Mobile Applications**: Applications must offer content fast, no matter where they are, because there are billions of mobile consumers globally.
    
* **Location-Based Services**: Services that demand real-time data transfer with low latency include GPS applications and maps.
    
* **E-commerce Platforms**: Online retailers need to maintain quick page loads while managing spikes in traffic during sales events.
    

## **The Journey Towards Edge Computing**

A clear transition from conventional centralized design to edge-distributed systems was described in the presentation. The "**Towards Edge**" strategy shows how Auto Scaling Groups (ASG) and edge services can effectively spread traffic among several sites.

### **Key Benefits of Edge Computing**

Three key benefits of using edge computing were highlighted during the session:

* **Performance**: Latency was drastically decreased by delivering content from closer user locations.
    
* **Security**: Improved defense via DDoS mitigation and distributed security techniques
    
* **Cost Optimization**: Better use of resources and lower bandwidth costs
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750943562270/325fba35-5a63-4b8f-a952-d3bac59797df.jpeg align="center")

## **Core AWS Edge Services Architecture**

### **Route 53 - DNS Foundation**

The DNS foundation is Route 53, which intelligently directs user requests to the best edge location depending on variables such as:

* Geographic proximity
    
* Health checks
    
* Latency-based routing
    
* Weighted routing policies
    

### **CloudFront - Content Delivery Network**

CloudFront acts as the primary CDN service, providing:

* Global edge locations for content caching
    
* Dynamic content acceleration
    
* Real-time metrics and monitoring
    
* Integration with other AWS services
    

### **Auto Scaling Groups - Dynamic Scaling**

ASG guarantees that your program can manage different traffic loads by:

* Automatically adjusting capacity based on demand
    
* Maintaining application availability
    
* Optimizing costs through efficient resource management
    

## **How Content Delivery Works at the Edge**

Using a real-world example, the seminar gave a thorough overview of the content delivery process:

### **Step-by-Step Content Delivery Process:**

1. **User Request**: A user requests content from your website
    
2. **Edge Location Check**: The request is routed to the nearest CloudFront edge location
    
3. **Cache Verification**: CloudFront checks if the requested content is cached at the edge location
    
4. **Origin Fetch**: If content is not cached, CloudFront fetches it from the origin server (S3 bucket or HTTP server)
    
5. **Content Delivery**: The user receives the content while it is also cached at the edge site for use in further requests.
    

Response times are greatly shortened by this procedure, which guarantees that subsequent requests for the same material are fulfilled straight from the edge location.

## **Security at the Edge**

A key component of the presentation was security, which covered several levels of defense:

### **DDoS Protection with AWS Shield**

* **AWS Shield Standard**:
    
    * Enabled by default for all AWS customers
        
    * Provides protection against common DDoS attacks
        
    * No additional cost
        
* **AWS Shield Advanced**:
    
    * Premium paid service
        
    * Advanced DDoS protection and mitigation
        
    * 24/7 access to DDoS Response Team (DRT)
        
    * Cost protection against DDoS-related charges
        

### **Web Application Firewall (WAF)**

WAF was emphasized in the session as a crucial element of application-layer security:

* Protection against common web exploits
    
* Custom rule creation for specific threats
    
* Integration with CloudFront for edge-level filtering
    
* Real-time monitoring and alerting
    

### **Global Security Coverage**

Using a global map representation, the presentation highlighted AWS's global security infrastructure, showing how security measures are dispersed across continents to offer complete defense against a range of threats and attack vectors.

## **Logic at the Edge - Advanced Implementation**

The final technical concept covered was **Logic @ Edge**, which represents the next evolution in edge computing:

### **CloudFront Functions and Lambda@Edge**

The architecture illustrates the deployment of AWS Lambda services at edge locations, allowing:

* **Viewer Request Processing**: Modify requests before they reach CloudFront cache
    
* **Origin Request Processing**: Customize requests before they reach the origin server
    
* **Origin Response Processing**: Modify responses from origin before caching
    
* **Viewer Response Processing**: Customize responses before delivery to users
    

## **Complete Request-Response Flow**

A thorough flow diagram was presented at the end of the session:

1. **Viewer Request** → CloudFront Edge Location
    
2. **Cache Miss** → **Origin Request** → Origin Server
    
3. **Origin Response** → CloudFront Cache
    
4. **Viewer Response** → End User
    

Applications may manage high traffic volumes with this design and still have the best possible performance and security.

## **Key Takeaways**

For developers and architects wishing to scale their apps, the seminar offered insightful information:

* **Start with the basics**: Implement Route 53, CloudFront, and Auto Scaling Groups as your foundation
    
* **Layer security appropriately**: Use Shield for DDoS protection and WAF for application-layer security
    
* **Leverage edge computing**: Deploy logic at edge locations for maximum performance
    
* **Monitor and optimize**: Continuously analyze performance metrics to optimize your edge strategy
    

## **Conclusion**

This in-depth discussion on edge computing and traffic scalability gave participants the know-how to build scalable, reliable web apps with AWS services. Edge computing is a crucial tactic for modern web applications because to its ability to optimize speed, improve security, and control costs.

## Read Elsewhere

* [Dev Community](https://dev.to/aws-builders/aws-user-group-chennai-meetup-session-2-handle-100x-your-web-traffic-edge-services-4em)
    

## References

**Community:** [AWS User Group Chennai](https://www.linkedin.com/company/awsugchennai/posts/?feedView=all)

**Event:** AWS User Group Chennai Meetup

**Topic:** Handle 100x Your Web Traffic Edge Services

**Speaker:** [**Keerthivasan Kannan**](https://www.linkedin.com/in/keerthivasan-kannan/)

**Date:** May 17, 2025

**Location:** [Presidio, Chennai](https://www.linkedin.com/company/presidio-/)