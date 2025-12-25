---
title: "Securing PII in Data Lakes: AWS Lake Formation Access Control"
seoTitle: "Securing PII in Data Lakes: AWS Lake Formation Access Control"
seoDescription: "A practical guide to role-based permissions, column-level security, and centralized governance for sensitive data | AWS Community Day Bengaluru 2025"
datePublished: Tue Dec 23 2025 13:45:12 GMT+0000 (Coordinated Universal Time)
cuid: cmjin0cf2000102ldgug0gq6k
slug: securing-pii-in-data-lakes-aws-lake-formation-access-control
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766485371637/6ac1e102-5eb9-49b3-aa06-75608f0d00f1.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766497450796/9bbb189c-f445-4da6-960d-92af42683534.jpeg
tags: aws, databases, amazon-web-services, aws-security, data-lake, aws-community, aws-community-builder, lake-formation, aws-lake-formation

---

I recently went to the AWS Community Day in Bengaluru in 2025 on May 23rd, and I have to say, it was full of amazing sessions. One presentation that stood out to me was "**PII Data Management with Lake Formation**" by **Ankit Sheth**. As someone who's always been interested in how companies manage sensitive data on a large scale, this session was just what I was looking for. The talk focused on the access layer of AWS Lake Formation and how it helps provide secure, role-based access to data lakes.

Let's be honest, handling permissions for sensitive data can turn into a big mess, especially when you're managing different types of data all in one place. This session showed me how Lake Formation deals with that issue directly.

## What is a Data Lake? (And Why Should You Care?)

Before we get into the technical details, let's start with the basics.

A data lake is like a big digital storage space where you can keep all your data, both organized and messy, no matter how much there is. You can store things like customer information, app logs, pictures, videos, and data from sensors. It doesn't matter how the data looks or how big it is.

The thing is, traditional databases need you to set up the structure before you start storing data. Data lakes work differently. You save the raw data first, and then decide on the structure when you actually use or look at the data (this is known as "schema-on-read"). This approach makes data lakes very flexible and also more cost-efficient.

## Key Characteristics of Data Lakes

According to the session, data lakes have some really strong features:

* **Single source of truth** - All your information is stored in one place, so it's easier to find and work with.
    
* **Support for multiple formats** - Data lakes can handle all types of data, whether it's organized CSV files, somewhat organized JSON files, or even plain, unorganized files.
    
* **Fast ingestion and consumption** - Data can be added quickly and used by different tools for analysis.
    
* **Low-cost storage** - Most data lakes on AWS use Amazon S3 for storage, which makes the cost much lower than using traditional databases.
    
* **Decoupled storage and compute** - You don’t pay for the computer power when you’re just keeping data safe. You only use the tools for analyzing data when you actually need them.
    
* **Built-in protection and security** - With tools like Lake Formation, you can set up detailed rules for who can access what and keep track of who is using the data.
    

Sound familiar? If you’ve ever had trouble with data tucked away in different places, you’ll understand why this approach makes sense.

## Why the Access Layer Matters

This is where it gets interesting.​

The session focused on the **Access Layer**, specifically how AWS Lake Formation handles role-based access control (RBAC). When you're working with sensitive information like social security numbers, credit card details, or health records, you can't just let everyone have access to everything. You need detailed control over who can see what.

### The Challenge with Traditional Approaches

Imagine you're creating an e-commerce platform. You might have:

* A marketing team that needs access to customer demographics
    
* A finance team that needs transaction records
    
* A data science team working on recommendation models
    
* An analytics team producing reports
    

Each team requires different levels of access to various datasets. Some can see all the data, others should only see data that's been anonymized, and some should not have access to PII at all.

Trying to manage this by manual? It would be a complete mess.

## How Lake Formation Solves This: Role-Based Access

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1766495534933/194d2d51-21d7-49b6-8e7c-8d8fa192cb9c.jpeg align="center")

AWS Lake Formation offers a single place to set up permissions that work across your whole data lake. The slide from the session showed how this system works clearly.

### The Permission Flow

1. **Administrator sets up permissions** - A data lake administrator can set permissions for databases, tables, columns, rows, or even individual cells. They also register these areas in Lake Formation.
    
2. **User queries data** - When a user, like someone using Amazon Athena or another analysis tool, wants to access data, they send a query with temporary login details.
    
3. **Lake Formation checks metadata** - The AWS Glue Data Catalog, which keeps track of your tables and their structure, is checked.
    
4. **Permissions are verified** - Lake Formation then checks if the user's role has the right to access the data they're asking for.
    
5. **Credentials are vended** - If they do, Lake Formation gives them temporary access to the data stored in the S3 bucket.
    
6. **Data is retrieved** - Only after that does the user get access to the data.
    

### Two Layers of Protection

Lake Formation provides two layers of permissions enforcement:​

* **Metadata layer** - Controlled through the AWS Glue Data Catalog
    
* **Storage layer** - Controlled through credential vending to access S3
    

This two-layer method makes sure that even if someone gets past one layer, they still can't get to the real data without the right permission.

## Database-Level vs Table-Level Permissions

One of the slides talked about the difference between permission scopes:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1766495614087/3e34e5af-5172-4188-851a-6e666dc30089.jpeg align="center")

### Database-Level Permissions

These are wide-ranging permissions that cover the whole database. You might give someone:

* **Select** - Read data from all tables
    
* **Insert** - Add new records
    
* **Delete** - Remove records
    
* **Alter** - Modify table structures
    
* **Super** - Full administrative rights, including the ability to grant permissions to others​
    

### Table-Level Column-Based Access

Lake Formation really stands out here.

You can set up access to specific columns within certain tables. For example:

* Your marketing team can see `customer_name` and `email`, but not `credit_card_number`
    
* Your compliance team can see everything
    
* Your external contractors can only see anonymized, aggregated data
    

This detailed control is very important when handling personal information. Instead of making many copies of the same data with different columns hidden (which is both tricky and costly), you create access rules once, and Lake Formation makes sure they are followed automatically.

You might be thinking, "Can’t I just use S3 bucket policies for this?"

To be honest, you could., but it would be very hard to manage. Every time you add a new user, role, or dataset, you’d have to change policies in several places by hand. Lake Formation brings everything together in one place.

## Real-World Scenarios Where This Helps

Let me give you some practical examples:

### Scenario 1: Healthcare Data

A hospital keeps patient information in a data lake. Doctors need full access to medical history, but billing staff should only see insurance and payment details. Researchers looking at health trends can only use anonymized data and must not see any personal identifying information at all.

With Lake Formation, you set these rules just once. The system makes sure everyone follows them automatically, no matter how they access the data, whether through Athena, Redshift Spectrum, or other connected tools.

### Scenario 2: E-Commerce Platform

An online store wants to study buying habits. Marketing teams can look at customer demographics and types of purchases, but they shouldn’t see exact prices (that’s for the finance team). Data scientists building machine learning models need patterns in transactions but not customer names.

Lake Formation allows you to set up policies based on different roles, which match exactly with your business needs.​

### Scenario 3: Regulatory Compliance

If you're based in the EU, GDPR requires tight control over personal data.  
Lake Formation has tools that track who looked at what data and when, making it easier to check compliance during audits.

## Conclusion

Managing personal information doesn't need to be hard. AWS Lake Formation's access layer lets you control who can see what, keeps everything organized, and gives you confidence, all while keeping the benefits of a data lake.

If you're handling sensitive data or are frustrated with managing permissions by hand, Lake Formation could be a good option to check out. Also, if you ever get the opportunity to go to AWS Community Day, don't miss it. Talks like Ankit's help break down complicated ideas into something easier to understand and put into practice.

## **About the Author**

*As an* ***AWS Community Builder***\*, I enjoy sharing the things I've learned through my own experiences and events, and I like to help others on their path. If you found this helpful or have any questions, don't hesitate to get in touch!\* 🚀

🔗 *Connect with me on* [*LinkedIn*](https://www.linkedin.com/in/chandra-prakash-reddy/)

## **References**

**Event:** AWS Community Day Bangalore 2025

**Topic:** Securing PII in Data Lakes: AWS Lake Formation Access Control

**Date:** May 23, 2025

**Location:** [**Conrad Benguluru**](https://www.hilton.com/en/hotels/blrkrci-conrad-bengaluru/hotel-location/?WT.mc_id=zPADA0IN1CH2PSH3paid_ggl4DOMBPP_Apr5SiteGGL_ObjROAS_TacBPP_TarKeyword_SMIN_FrmtRSAs_CrNText_DvceAll_LPOHW6BLRKRCI7EN8acctid=9094736915-campid=16903767109-adgrpid=135963230375&&&&&gad_source=1&gad_campaignid=16903767109&gbraid=0AAAAADnjLGN_JqIwAdvqkR6YxlY-a8paB&gclid=CjwKCAjwjffHBhBuEiwAKMb8pLhlL6XFN37JymneexipiKWmv-jIGYxbiJtul9ZkklxfW_jN7zel4RoCCYAQAvD_BwE&gclsrc=aw.ds)

## **Also Published On**

[**AWS Builder Center**](https://builder.aws.com/content/37FRSfJBVN28NpXDcfhgijdg2GG/securing-pii-in-data-lakes-aws-lake-formation-access-control)

[**Dev Community**](https://dev.to/aws-builders/securing-pii-in-data-lakes-aws-lake-formation-access-control-18ef)