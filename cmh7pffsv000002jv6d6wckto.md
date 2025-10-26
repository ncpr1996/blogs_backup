---
title: "Chaos Testing AWS EKS with AWS FIS | AWS Community Day Bangalore 2025"
seoTitle: "Chaos Testing AWS EKS with AWS FIS | AWS Community Day Bangalore 2025"
seoDescription: "Insights from the session: Chaos testing AWS EKS with FIS for resilient microservices"
datePublished: Sun Oct 26 2025 12:48:03 GMT+0000 (Coordinated Universal Time)
cuid: cmh7pffsv000002jv6d6wckto
slug: chaos-testing-aws-eks-with-aws-fis-aws-community-day-bangalore-2025
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1761476270305/001afa03-f065-4d1c-b038-ab42546594da.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1761479030453/20c21111-81ef-4186-97ae-70b9d89e5e2e.jpeg
tags: microservices, aws, kubernetes, cloud-computing, devops, amazon-web-services, api-gateway, eks, aws-eks, aws-community, chaos-engineering, eks-cluster, aws-fis

---

One of the most interesting tech events I've attended this year was AWS Community Day Bangalore, which took place at the Conrad Hotel on **May 23, 2025**. Cloud enthusiasts, developers, architects, and AWS specialists from all around Bangalore gathered to share information, brainstorm, and go deeply into actual AWS deployments, and the vibe in the room was amazing.

"Failure is Inevitable — Be Ready: Chaos Testing AWS EKS with AWS FIS" was one talk that particularly caught my attention. I want to share what I learnt from this session with all of you because it completely changed the way I think about creating robust microservices.

## Why Chaos Engineering Matters

The inspiring opening statement of the session was, "Failure is Inevitable." Things will break in the era of microservices and complicated distributed systems of today. Using a slide that depicted the reality of microservices. A complex network of interconnected services that seemed more like chaos than order the presenters expertly demonstrated this.

In traditional systems, features are created and then everything is left to chance. A new attitude is required when using AWS EKS (Elastic Kubernetes Service) to execute microservices. You must demonstrate your system's durability through controlled experiments; you cannot simply presume it. ​

## Understanding Chaos Engineering

What is Chaos Engineering, then? According to the presenters, it is the process of conducting "controlled" experiments on a system in order to increase confidence in its resilience. Consider it this way: you purposefully introduce errors during business hours, when your team is prepared to watch and react, rather than waiting for your production system to break at three in the morning.

The core principles of Chaos Engineering include :

* **Simulate Real World Scenarios**: Replicate actual failure conditions
    
* **Observe Impact**: Monitor how your system responds
    
* **Build Recovery Mechanisms**: Design automatic healing processes
    
* **Validate System Assumptions**: Challenge your architectural beliefs
    
* **Target Both Infrastructure & Application**: Don't just test one layer
    

"**The Need for a New Mindset**" was one of the slides that truly spoke to me. The presenters highlighted five important changes in perspective:

1. **Don't assume resilience, prove it** — Don't trust what you haven't tested
    
2. **Design for failures, not just functionality** — Build with failure scenarios in mind
    
3. **Shift from confidence to curiosity** — Question your assumptions constantly
    
4. **Break things before they break you** — Proactive is better than reactive
    
5. **Test both services and infrastructure** — Holistic testing is essential
    

## Creating Resilient Microservices

The presenters displayed an excellent diagram that outlined the process of developing resilient services. It is not enough to simply launch a new service and then forget about it. Rather, it must be built with resilience in mind from the beginning, with appropriate fallbacks and links to pre-existing services that can gracefully deal with failures. ​

When using AWS EKS to orchestrate numerous containerized microservices, this architecture thinking is essential. Using the **AWS REST API Gateway**, the presentation demonstrated a microservices architecture based on EKS. Included in the configuration were:

* AWS API Gateway as the entry point
    
* Network Load Balancer (NLB) and Application Load Balancer (ALB) for traffic distribution
    
* EKS clusters spread across multiple availability zones
    
* Multiple EKS nodes running different microservices (Service A, B, C)
    
* Databases connected to each service
    

You need this multi-layered, redundant design, but how can you be sure it can withstand stress? In this situation, **AWS Fault Injection Service (FIS)** is useful.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1761478794884/1b25b86a-c95d-4a9a-ba3d-ddc10c631e2c.jpeg align="center")

## Enter AWS Fault Injection Service (FIS)

You may conduct controlled chaos experiments on your AWS infrastructure with AWS FIS, a fully managed solution. The presenters divided the main ideas of FIS into four parts:

1. **Actions**: The faults you inject (e.g., stop EC2 instances, failover databases)
    
2. **Targets**: The resources you affect (e.g., EC2 instances, ECS tasks)
    
3. **Stop Conditions**: Safety mechanisms to halt the experiment if things go wrong
    
4. **Experiment Template**: The blueprint of what to do, your chaos playbook
    

What impressed me most was the extensive list of **AWS services FIS supports** :

* Amazon CloudWatch
    
* Amazon DynamoDB
    
* Amazon EBS
    
* Amazon EC2
    
* Amazon ECS
    
* **Amazon EKS** (the focus of this talk)
    
* Amazon ElastiCache
    
* Amazon RDS
    
* Amazon S3
    
* Amazon Systems Manager
    
* Amazon VPC
    

With this degree of support for all AWS services, you can fully replicate real-world failures.

## The Live Demo

The **live demo walkthrough**, where they used AWS FIS to illustrate **EKS Pod Termination**, was the session's high point. The FIS console displayed an experiment template intended to remove pods from an EKS cluster, as I could see on the screen. The setup for the experiment included:

* **Experiment Template ID**: Clearly defined for tracking
    
* **S3 bucket log destination**: For storing experiment logs
    
* **Actions**: Specifically targeting EKS pod deletion
    
* **Stop conditions**: Safety nets to prevent runaway failures
    
* **IAM Role**: Proper permissions for FIS to execute the experiment
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1761478641076/e6c2ba9a-a2fa-4f1c-b297-3d5b41c59bba.jpeg align="center")

It was enlightening to watch them start the experiment and observe the system's reaction in real time.

## How AWS FIS Helped Them

Following the demonstration, the presenters discussed the observable advantages of using chaotic engineering with AWS FIS: ​

* **Proactive Risk Mitigation**: Identifying weaknesses before they become incidents
    
* **Improved Service Availability**: Higher uptime due to tested resilience
    
* **Data-Driven Reliability Improvements**: Using experiment data to make informed architectural decisions
    
* **Faster Incident Recovery**: Teams already know how to respond because they've practiced
    

These benefits go beyond theory; they are quantifiable results that have an immediate effect on customer satisfaction and business continuity. ​

## Advanced Capabilities

The session also covered some **advanced FIS capabilities** :​

* **Multi-Account Experiment Support**: Run chaos experiments across multiple AWS accounts
    
* **Custom Fault Injection**: Create your own custom failure scenarios
    
* **Scheduled Experiments**: Automate chaos testing at regular intervals
    
* **Advanced Monitoring using Event Bridge**: Get real-time insights into experiment execution
    
* **Safety Levers**: Additional guardrails to ensure experiments don't cause unintended damage
    

These features make AWS FIS enterprise-ready and scalable for large organizations managing complex cloud infrastructures.​

## Lessons Learned

The presenters concluded by sharing priceless insights from their experience with chaotic engineering: ​

* **Start Small, Scale Gradually**: Don't try to chaos-test everything at once
    
* **Hypotheses Are Critical**: Always form a hypothesis before running an experiment
    
* **Observability Is Non-Negotiable**: You can't understand what you can't see
    
* **Controlled Chaos Builds Confidence**: Regular testing removes fear
    
* **Operational Guardrails is must**: Always have kill switches and rollback plans
    

Because they are based on actual experience, these lessons struck resonated deeply with me.

## Call to Action

The presenters wrapped off with a useful foundation for a call to action: ​

### Before You Begin

* Review system architecture
    
* Define steady state
    
* Form hypotheses
    

### Planning the Experiment

* Start in test environments
    
* Consult team insights
    
* Review outage history
    
* Target high-impact systems
    

### During the Experiment

* Use stop conditions
    
* Track metrics
    
* Iterate safely
    

Even if you're just starting out, chaotic engineering is approachable thanks to our methodical methodology.

## Conclusion

This talk on chaotic engineering really stood out during the amazing learning experience that was **AWS Community Day Bangalore 2025**. I learned from the seminar that while failure in distributed systems is unavoidable, readiness makes all the difference. We can test our systems proactively and gain genuine trust in our architectures with the help of AWS FIS. I strongly suggest experimenting with chaotic engineering using AWS FIS if you're using microservices on EKS.

## **References**

**Event:** AWS Community Day Bangalore 2025

**Topic:** Chaos Testing AWS EKS with AWS FIS

**Date:** May 23, 2025

**Location:** [Conrad Benguluru](https://www.hilton.com/en/hotels/blrkrci-conrad-bengaluru/hotel-location/?WT.mc_id=zPADA0IN1CH2PSH3paid_ggl4DOMBPP_Apr5SiteGGL_ObjROAS_TacBPP_TarKeyword_SMIN_FrmtRSAs_CrNText_DvceAll_LPOHW6BLRKRCI7EN8acctid=9094736915-campid=16903767109-adgrpid=135963230375&&&&&gad_source=1&gad_campaignid=16903767109&gbraid=0AAAAADnjLGN_JqIwAdvqkR6YxlY-a8paB&gclid=CjwKCAjwjffHBhBuEiwAKMb8pLhlL6XFN37JymneexipiKWmv-jIGYxbiJtul9ZkklxfW_jN7zel4RoCCYAQAvD_BwE&gclsrc=aw.ds)

## **Also Published On**

* [AWS Builder Center](https://builder.aws.com/content/34bVsi6UVtmheFfSikhbY5HahvM/chaos-testing-aws-eks-with-aws-fis-or-aws-community-day-bangalore-2025)
    
* [Dev Community](https://dev.to/aws-builders/chaos-testing-aws-eks-with-aws-fis-aws-community-day-bangalore-2025-17k3)