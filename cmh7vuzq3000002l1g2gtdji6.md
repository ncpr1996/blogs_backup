---
title: "Building Secure Foundations | AWS Community Day Bangalore 2025"
seoTitle: "Building Secure Foundations | AWS Community Day Bangalore 2025"
seoDescription: "A practical guide to AWS Organizations, Control Tower, and Landing Zone architecture"
datePublished: Sun Oct 26 2025 15:48:07 GMT+0000 (Coordinated Universal Time)
cuid: cmh7vuzq3000002l1g2gtdji6
slug: building-secure-foundations-aws-community-day-bangalore-2025
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1761485123972/b580ac98-a6c0-4add-a66f-21001f7652e6.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1761492695375/0cff2d81-8e05-4a0d-9910-6b2e6b74ad5b.jpeg
tags: aws, amazon-web-services, aws-community, cloud-security, aws-service-control-policies, aws-organizations, aws-control-tower, aws-iam-identity-center, multi-account-management

---

The **AWS Community Day in Bangalore**, which took place on May 23, 2025, brought together developers, architects, and cloud enthusiasts to discuss one of the most important aspects of contemporary cloud architecture: operating AWS at scale. One session in particular stood out among the many that day: a thorough in-depth analysis of creating a solid multi-account AWS Landing Zone template that can grow from a few accounts to more than 1,000.

This talk was a treasure mine of information for anyone curious about how big businesses handle hundreds of AWS accounts without going insane. Allow me to outline the main conclusions that fundamentally altered my perspective on cloud governance.

## Understanding the Problem

The session began with a situation that many cloud practitioners may relate to. Consider the following scenario: your company's AWS accounts are safe for now, but what would happen if IAM credentials were stolen? How do you keep customer-facing accounts and internal duties apart? Above all, how do you make sure that every one of your AWS accounts has a strong security baseline?

These are not only hypothetical issues. Organizations require organized approaches to governance, security, and compliance in the multi-cloud, multi-account world of today. Everything fell into place when the webinar presented a fascinating scenario that compared AWS Organizations to a corporate franchise.

## The Corporate Franchise Analogy

Think of AWS Organizations as your franchise headquarters. Just like a franchise business, here's how it breaks down:

* **AWS Organizations** = Franchise Headquarters
    
* **Organizational Units (OUs)** = Regional Divisions
    
* **AWS Accounts** = Individual Coffee Shops
    
* **Policies (SCP/RCP)** = Franchise Rule Book
    
* **Centralized Billing** = Financial Management
    

It is much simpler to see why you would organize your cloud environment in this manner when you use this mental model. Although each "coffee shop" (account) has significant independence, they all follow to the corporate policies established by the corporate office.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1761490767242/43682c61-321c-4384-b98d-cfb0b38d1007.jpeg align="center")

## Why This Architecture Matters

A solid progression framework explaining why firms move toward this approach was presented during the event. There are genuine business advantages at every level, so it's not just about adding complexity for the sake of complication:

**Level 1**: Best practices for multi-account AWS architecture (Landing Zone) - establishing the foundation  
**Level 2**: Centralizing login, security, governance, and compliance at scale - reducing operational overhead  
**Level 3**: Building Landing Zone from scratch - customization for specific needs  
**Level 4**: Going from 100 to 200 level - maturity and optimization  
**Level 5**: Saving 2 hours and solving business problems - actual ROI

The focus on approaching this architecture as more than just a technical exercise rather, as something that addresses actual business problems and saves time was what most impressed me.

## The 100 Level: Getting Started

The essential steps for organizations starting their multi-account journey were covered in detail in the session. At level 100, your attention is on:

* Creating the organization and assigning a management account
    
* Inviting member accounts to the organization
    
* Creating Organizational Units based on workload types and account categories
    
* Implementing Service Control Policies (SCPs) like "Disable Leave Organization" to prevent accidental account removal
    

Creating distinct OUs for internal accounts and customer-facing workloads, as well as testing sandbox environments, was one useful suggestion made. This division creates boundaries for natural security and greatly simplifies government.

## Adding Policies the Right Way

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1761490818084/ef5645f6-7c62-4610-9861-c91ee23c3546.jpeg align="center")

A real demonstration of linking SCPs to Organizational Units was part of the session. In the example, an internal OU was linked to a "Disable Leave Organization" policy, which forbids any accounts within that OU from accidentally departing the company.

The JSON policy structure was straightforward, using the Effect "Deny" on the action "organizations:LeaveOrganization" with a wildcard resource. This simple policy can prevent major headaches down the road.

## AWS Control Tower: Your Facilities Management Office

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1761491444112/2ebb1ed6-3425-4b7b-8764-268a47d4c3a8.jpeg align="center")

This is when the exciting part begins. The "Facilities Management Office" of your cloud infrastructure is AWS Control Tower. Applying the franchise comparison:

* **AWS Control Tower** = Facilities Management Office
    
* **AWS Accounts** = Branch Offices
    
* **Landing Zone** = Corporate Office Blueprint
    
* **Controls** = Corporate Policies
    
* **Account Factory** = Office Setup Team
    
* **Dashboard** = CCTV Camera Room
    

In basic terms, the entire account provisioning and governance process is automated and standardized by Control Tower. Control Tower offers a factory method that eliminates the need to individually set up each account with the proper specifications.

## The Role of Control Tower in Landing Zones

AWS Control Tower serves multiple critical functions:

* Implements the Landing Zone framework as a service
    
* Provides shared accounts for log archiving and audit purposes
    
* Centrally applies controls at the OU level
    
* Offers different types of controls: preventive, detective, and proactive
    
* Violations of controls trigger central alerts
    
* Centralizes compliance using AWS Config
    
* Provides centralized logging for all member accounts
    
* Uses Account Factory to standardize provisioning with baseline configurations
    
* Offers a central dashboard to monitor compliance drift
    

This method has the advantage that new accounts instantly inherit all security baselines, logging configurations, and legal requirements once they are properly set up. Each new account will no longer require a manual checklist.

## Prerequisites for the 100 Level

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1761491012583/c3cb26c5-60f5-4599-9189-cb0259cfe295.jpeg align="center")

Before jumping into Control Tower, there are important prerequisites to handle:

* Delete existing CloudTrail for the account
    
* Delete existing AWS Config recorders
    
* Either allow Control Tower to create shared accounts or bring your existing ones
    
* Note that VPCs for existing accounts are NOT affected
    
* New accounts provisioned through Control Tower WILL have a default VPC
    

This is a crucial VPC detail: your networking remains intact when you move current accounts into Control Tower. However, the default VPC will be used for newly created accounts.

## Enrolling Accounts into Control Tower

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1761490930198/0e65cf69-e727-4476-a9aa-0885404c8570.jpeg align="center")

The practical procedures for enrolling Organizational Units under Control Tower supervision were demonstrated during the event. The procedure includes:

1. Enrolling the OU at the Root level
    
2. Creating hierarchical structures like "ck-internal-accounts" for internal workloads
    
3. Creating sandbox OUs for testing environments
    
4. Registering and enrolling individual accounts into the structure
    

With clear status indicators indicating which OUs are successfully enrolled, the visual example demonstrated how simple it is to handle this through the AWS console.

## IAM Identity Center: Unified Login at Scale

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1761490951351/5a74e360-f607-47ca-b0df-4d65564e3c04.jpeg align="center")

AWS IAM Identity Center (previously AWS SSO) was one of the most useful features that was covered. Users can access various AWS accounts using a single set of credentials thanks to this service, which simplifies login throughout your whole organization.

Even Microsoft Entra ID (previously Azure AD) integration as an identity provider was showcased during the session. This means that businesses can offer smooth access to AWS resources while utilizing their current organizational identification systems.

When working with dozens or hundreds of accounts, access management is made much easier by the ability to assign users and groups to AWS accounts straight from the Identity Center.

## Landing Zone: The 200 Level

The 200 level concentrates on customisation and advanced features after you've learned the fundamentals:

* Adding wikis and discussions using GitHub for documentation
    
* Using GenAI to find relevant discussions and wiki content
    
* Centralizing AWS user notifications and health notifications
    
* Adding Compute Optimizer and Cost Optimization Hub for financial management
    
* Centralizing root user operations for security
    
* Adding a central security hub and implementing GuardDuty
    
* Updating central EKS dashboards for container workloads
    
* Customizing Control Tower using CloudFormation Customizations (CfCT)
    
* Using AWS Nova for manual operations and troubleshooting
    

Your Landing Zone is transformed from a simple governance structure into an all-inclusive cloud management platform by these advanced capabilities.

## Key Takeaways

The seminar concluded with some helpful guidance that struck a deep connection:

**Document, Document, Document** - Consider your landing page to be a product. Documentation is necessary for knowledge transfer and team scalability; it is not optional.

**Treat it as a PRODUCT** - Your Landing Zone is an internal product that powers your entire company, not simply the infrastructure.

**Start Small** - Avoid attempting to construct everything at once. Start with simple OUs and a few policies, then progressively increase the level of complexity.

**Use Test Accounts** - Before implementing your rules, controls, and configurations widely, always make sure they are working in test environments (test accounts, test OUs, test permissions, and test controls).

**REPEAT** - The governance of the cloud is iterative. As your company expands and needs change, your Landing Zone will be continuously improved.

The focus on eliminating anxiety was particularly effective. As demonstrated by the crossed-out text "Somebody's watching me, it's my ANXIETY!!!" on one of the last slides, the purpose of all these frameworks and tools is to increase infrastructure confidence rather than to increase stress.

## Conclusion

AWS Community Day Bangalore 2025 demonstrated how, with the correct management structure, businesses can grow from a small number of AWS accounts to thousands with confidence. Cloud administration is transformed from overwhelming chaos into organized simplicity with the help of AWS Organizations and Control Tower, which power the multi-account Landing Zone architecture. Teams may concentrate on innovation rather than putting out fires by centralizing security, automating compliance, and integrating identity management. The main lesson learned is to begin small, record everything, conduct extensive testing, and iterate often as your company expands. Putting these guidelines into practice makes it shockingly easy to manage enterprise-scale AWS infrastructure.

## **References**

**Event:** AWS Community Day Bangalore 2025

**Topic:** Building Secure Foundations

**Date:** May 23, 2025

**Location:** [Conrad Benguluru](https://www.hilton.com/en/hotels/blrkrci-conrad-bengaluru/hotel-location/?WT.mc_id=zPADA0IN1CH2PSH3paid_ggl4DOMBPP_Apr5SiteGGL_ObjROAS_TacBPP_TarKeyword_SMIN_FrmtRSAs_CrNText_DvceAll_LPOHW6BLRKRCI7EN8acctid=9094736915-campid=16903767109-adgrpid=135963230375&&&&&gad_source=1&gad_campaignid=16903767109&gbraid=0AAAAADnjLGN_JqIwAdvqkR6YxlY-a8paB&gclid=CjwKCAjwjffHBhBuEiwAKMb8pLhlL6XFN37JymneexipiKWmv-jIGYxbiJtul9ZkklxfW_jN7zel4RoCCYAQAvD_BwE&gclsrc=aw.ds)

## **Also Published On**

* AWS Builder Center
    
* Dev Community