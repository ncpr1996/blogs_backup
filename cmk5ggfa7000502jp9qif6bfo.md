---
title: "How AWS Lambda and Fargate Change the Way We Build Apps"
seoTitle: "How AWS Lambda and Fargate Change the Way We Build Apps"
seoDescription: "Key insights from AWS Student Community Day Tirupati, November 1st, 2025"
datePublished: Thu Jan 08 2026 13:00:27 GMT+0000 (Coordinated Universal Time)
cuid: cmk5ggfa7000502jp9qif6bfo
slug: how-aws-lambda-and-fargate-change-the-way-we-build-apps
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1767869837155/0e85c2cc-6a7c-48bb-af05-49fea52688db.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1767877100837/1c13d9fe-b76a-415b-9dad-9bd5a35799f1.jpeg
tags: aws, amazon-web-services, containers, serverless, aws-lambda, aws-fargate, aws-community, aws-community-builder, aws-user-group-tirupati

---

Attending the AWS Student Community Day in Tirupati at Mohan Babu University was a special experience for me, not just as someone who participated, but also as an **AWS Community Builder** and someone who enjoys sharing cloud knowledge with beginners and other interested people. The session titled “From Code to Containers: Understanding Serverless Beyond Lambda” by **Avinash Dalvi** stood out to me right away because it offered something many of us are looking for: clear guidance on when to use Lambda and when to consider other options, especially containers.

## Setting the stage: Why “serverless beyond Lambda”?

The session began by discussing the main topic: moving from writing code to using containers, but still keeping the serverless mindset. The key point was that serverless is more than just using functions like Lambda. It’s about thinking in a way that lets you focus on your code, while AWS handles the rest of the work behind the scenes.

The speaker introduced himself as a leader of an **AWS User Group Bengaluru** and an **AWS Community Builder**, which made everyone in the room feel confident that the talk would be based on real experiences, not just theory. He focused on helping us understand where Lambda works well, where it might not be the best choice, and how services like AWS Fargate can step in when Lambda can’t handle the job.

## The serverless mindset shift

### From “I need a server” to “I need to run code when X happens”

One of my favorite parts of the talk was the idea about changing how we think. Usually, people think, “I need a server to run my code.” That way of thinking leads to:

* Spending money on server capacity even when traffic is low most of the time
    
* Taking care of the infrastructure, like updating software, fixing security issues, and keeping the system safe
    
* Paying for servers that aren’t being used
    
* Manually adjusting the server size when traffic goes up or down
    

In short, you end up spending too much time watching over servers instead of working on your app.

The serverless approach changes this by focusing on: “I need to run code when something specific happens.”  
That something could be a file being uploaded, an API request, a scheduled task, or an event from another service. Then:

* You tell AWS what your needs are, like how long the code runs, how much memory it uses, and how long it can wait for a response.
    
* AWS handles all the setup and management of the hardware and software needed.
    
* You only pay for the time your code actually runs, not for the time it's sitting idle.
    
* When more events happen, the system automatically grows to handle them without you having to do anything.
    

This change in thinking is what really makes serverless technology powerful, whether you're using Lambda functions or containers in a serverless setup.

## Pizza, anyone? Explaining serverless with food

### Make it yourself vs order pizza

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767872600390/ed5602d0-f87e-4c6b-bbac-b8aa3c75b6f1.jpeg align="center")

To make it easier to understand, the speaker used a pizza example. Let’s imagine two choices for dinner:

1. **Option 1: Make it yourself**
    
    * You buy ingredients
        
    * You prepare everything
        
    * You cook, serve, and clean up
        
2. **Option 2: Just order pizza**
    
    * You specify what you want
        
    * Someone else handles the kitchen, oven, and cooking
        
    * You pay for the pizza, not for owning a restaurant
        

Traditional servers, like EC2, are like cooking at home. You take care of the kitchen (server), keep the oven running (patching, updates), and you pay for it all the time, even when you’re not cooking. You have full control, but you also have to take care of everything yourself.

Serverless is like ordering pizza. You just give your order (code), say what you want (toppings, size, base), and AWS handles the rest. You only pay for what you eat, not for keeping the kitchen open all day.

### Ordering your serverless pizza

The session continued by using the analogy to explain how to build a serverless application.

1. **Base (Runtime/Language)**
    
    * Choose Python, Node.js, Java, Go, .NET, Ruby, etc.
        
    * Or “bring your own base” using containers when you need something custom.
        
2. **Toppings (Resources)**
    
    * RAM from a small amount up to several GB
        
    * Temporary storage space
        
    * CPU that scales with memory
        
3. **Size (Code Complexity)**
    
    * Small: simple functions
        
    * Medium: moderate logic
        
    * Large: complex applications
        
4. **When should it run?**
    
    * Immediate on events (like file uploads)
        
    * Scheduled (cron-style jobs)
        
    * On-demand via API calls
        

This helped the students in the room better relate their daily experiences to the decisions made in cloud computing.

## Lambda in action (and where it struggles)

### A simple Lambda example: image resizer

To make it more clear, there was a slide that showed a Lambda function used to resize images that were uploaded to S3. The code used was:

1. `boto3` to talk to S3
    
2. `PIL` (Python Imaging Library) to open and resize the image
    
3. A `lambda_handler` function that:
    
    * Reads the file details from the S3 event
        
    * Downloads the image to `/tmp`
        
    * Creates a thumbnail
        
    * Saves the processed image back and returns a success status
        

This kind of situation is exactly where Lambda works best: for small, trigger-based, short-running tasks like image resizing, making thumbnails, simple API support, and light data processing.

### When Lambda hits the wall

But Lambda isn’t without its limits, and the speaker was very open about that. There was a slide called “When Lambda hits the wall” that listed situations like:

* Uploading a video → Lambda works great
    
* Generating a thumbnail → Lambda is perfect
    
* Transcoding a full video → Lambda fails
    

Why does it fail here? Because:

* Video processing might take 45 minutes
    
* Lambda has a hard timeout limit (15 minutes in the slides)
    
* You may need more control over the environment
    
* Larger dependencies or special tools may be required
    

So even though serverless technology is strong, you still need to choose the right tool within that serverless environment. That’s where AWS Fargate comes in.

## Lambda vs Fargate: same pizza shop, different options

### Comparing Lambda and Fargate

One slide showed a table comparing Lambda with Fargate using the same restaurant analogy:

1. **What it is**
    
    * Lambda: standard menu
        
    * Fargate: custom recipe
        
2. **Base options**
    
    * Lambda: pre-set runtimes
        
    * Fargate: any container image
        
3. **Customization**
    
    * Lambda: limited to what the menu supports
        
    * Fargate: fully customizable environment
        
4. **Execution time**
    
    * Lambda: up to the configured limit (15 minutes in the slide)
        
    * Fargate: effectively unlimited for long-running tasks
        
5. **Code size**
    
    * Lambda: limited package size
        
    * Fargate: no strict limit; your container image can hold more dependencies
        
6. **Use case**
    
    * Lambda: quick, short functions
        
    * Fargate: long processes, heavy workloads
        
7. **Cold starts**
    
    * Lambda: can happen
        
    * Fargate: more consistent performance once tasks are running
        

The bottom line? Lambda is like quickly ordering from a standard menu, while Fargate lets you bring your own recipe and ingredients but still avoids managing the kitchen yourself.

### Fargate – bring your own recipe and enjoy the freedom

Another slide described **Fargate** as “Bring Your Own Recipe”:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767872812604/e3fb5d78-0623-4dd2-932c-b9c3d7811d93.jpeg align="center")

* You package your app into a container (Docker image)
    
* AWS runs it for you without asking you to manage servers
    

Then came **“Fargate – The Freedom”** with three angles:

1. **More control**
    
    * Any programming language
        
    * Any runtime version
        
    * Custom OS-level dependencies
        
    * Specific tools and libraries you can’t easily run in Lambda
        
2. **More capacity**
    
    * Run for hours or days
        
    * No 15-minute limit
        
    * Much higher memory and CPU options
        
3. **More use cases**
    
    * Long-running processes
        
    * Legacy applications that expect a traditional environment
        
    * Microservices with specific runtime needs
        
    * Batch jobs and background processing
        

This made it clear that Fargate is still “serverless” in the sense that you don’t manage servers, but you get container-level flexibility.

## Architecture patterns you can try

### Practical patterns from the slides

One of the most helpful slides showed different architecture patterns that students could try at home. Some examples included:

1. **Event-driven API**
    
    * S3 upload → Lambda → DynamoDB
        
    * Great for things like uploading documents and storing metadata.
        
2. **Scheduled jobs**
    
    * EventBridge (cron) → Lambda → process data
        
    * Perfect for nightly reports, cleanup jobs, or scheduled notifications.
        
3. **Microservices**
    
    * API Gateway → Lambda or Fargate → backend services
        
    * Useful when building modular, independently deployable services.
        
4. **Data pipeline**
    
    * S3 → Lambda (trigger) → Fargate (heavy processing) → S3
        
    * A strong pattern when you need to combine quick triggers with long-running tasks.
        
5. **Webhook handler**
    
    * GitHub/Stripe → API Gateway → Lambda → action
        
    * Common for reacting to external events like payments or code pushes.
        

These patterns link what students learn in class to actual projects they might work on, like building apps for school, starting their own business, or doing internships.

## When NOT to use serverless

### Being honest about trade-offs

One slide caught my attention because it said: “Be honest – serverless isn’t always the best choice.” That’s a key point, especially for newbies who are excited about a fresh new idea. The slide listed some situations where serverless might not be the right fit:

* When you have steady and high traffic that could be handled more affordably with always-on infrastructure
    
* When you need a lot of control over the environment at a lower level
    
* When tasks run for a long time and go beyond what a serverless function can handle
    
* When you aren’t sure about your needs yet and might complicate things by using too many managed services too early
    

In the end, serverless is just another tool. The real skill is knowing when to use it and when something else, like containers or even basic EC2 instances, would work better.

## Lambda vs Fargate: a simple decision tree

### A mental model for choosing

There was also a clear decision tree to help choose between Lambda and Fargate. The simplified way of thinking about it went like this:

1. Do you need to run code at all?
    
2. Will it finish in under 15 minutes?
    
    * If **no** → consider Fargate for long-running processes with a custom environment.
        
3. If yes, is it a standard runtime (like Python, Node.js, etc.) with manageable dependencies?
    
    * If **yes** → Lambda is usually the fastest and cheapest option.
        
    * If **no** → again, Fargate or another container-based approach likely fits better.
        

This kind of straightforward flow is really useful when you're building your first few architectures and aren't sure which service to use.

## Key takeaways from the session

### The slide summary and my own reflections

The final “Key Takeaways” slide put everything together with points like:

* Serverless is like ordering pizza instead of running your own restaurant
    
* Understand **Lambda vs Fargate** instead of blindly choosing one
    
* Focus on code, not servers
    
* Pay for value, not idle time
    

For me personally, the biggest takeaway was that “serverless” isn’t just for Lambda. You can think serverless even when using containers, as long as AWS takes care of setting up and scaling your resources, and you focus mainly on your application.

## Conclusion

This session at AWS Student Community Day in Tirupati was really helpful because it reminded me that good tech talks don't just list features, they change the way you understand things. The pizza example, the open talk about the limits of Lambda, and the introduction to Fargate as a strong "serverless containers" option made the topics easier to grasp, especially for students who are just starting to learn about these services.

As an AWS Community Builder, events like this keep me motivated because they show how quickly curiosity can turn into actual projects when you get the right examples and ways of thinking. If this topic interests you, try picking a small use case from your own life, like processing images from your app or running a scheduled cleanup, and try building it using Lambda or Fargate. Getting your hands on these tools will teach you more than any presentation ever could.

## **About the Author**

*As an* ***AWS Community Builder***, I enjoy sharing the things I've learned through my own experiences and events, and I like to help others on their path. If you found this helpful or have any questions, don't hesitate to get in touch! 🚀

🔗 *Connect with me on* [*LinkedIn*](https://www.linkedin.com/in/chandra-prakash-reddy/)

## **References**

**Event:** AWS Student Community Day Tirupati

**Topic:** How AWS Lambda and Fargate Change the Way We Build Apps

**Date:** November 01, 2025

## **Also Published On**

[**AWS Builder Center**](https://builder.aws.com/content/37yXqqfEO6InqTyytcnBGHkMGLB/how-aws-lambda-and-fargate-change-the-way-we-build-apps)

[**Dev Community**](https://dev.to/aws-builders/how-aws-lambda-and-fargate-change-the-way-we-build-apps-dh1)