---
title: "Key Components and Technologies in Cloud Computing"
datePublished: Thu Apr 18 2024 08:30:10 GMT+0000 (Coordinated Universal Time)
cuid: clv4ze5ur000i08le9tgv12pt
slug: key-components-and-technologies-in-cloud-computing
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1713094526367/1f5b6bb5-51ad-43f3-a9ef-ab4b3c86a86a.png
tags: cloudformation, microservices, cloud, cloud-computing, microservice, scalability, microservices-cio5jsgm601wbmd53xbqyvy44, virtualization, containerization, orchestration, cost-optimisation, hypervisor, cloud-security

---

## **Virtualization**

* Virtualization separates a service from the actual physical hardware it runs on.
    
* It makes a virtual copy of computer hardware using special software.
    
* Initially developed during the mainframe era.
    
* Virtualization lets multiple operating systems and applications run on the same hardware at the same time.
    
* This boosts hardware use and flexibility.
    
* Cloud providers use virtualization to save money, reduce hardware, and save energy.
    
* It allows one physical resource to be shared among many users or organizations.
    
* This is done by giving each user a virtual name for the part of the resource they're using, and showing them where it is when needed.
    
* Hardware virtualization is key to delivering Infrastructure-as-a-Service (IaaS) in cloud computing.
    
* Virtualization also covers virtual environments for running applications, storing data, and handling networking.
    
    * **Host Machine :** This is the main computer where the virtual machine will be made.
        
    * **Guest Machine :** The virtual machine itself is called the Guest Machine.
        

**Benefits of Virtualization**

* Virtualization reduces the need for physical hardware, saving money on purchasing and maintaining equipment.
    
* It allows better utilization of existing hardware by running multiple virtual machines on a single physical server.
    
* Virtualization enables quicker backup and restoration of virtual machines, improving disaster recovery capabilities.
    
* Virtualization makes it easier to scale resources up or down based on demand, without needing to add or remove physical servers.
    
* Virtualization allows for easy creation of testing environments, speeding up development cycles and reducing costs.
    
* Virtualization can extend the lifespan of older applications by running them on virtual machines, even if the underlying hardware becomes outdated.
    

**Drawbacks of Virtualization**

* Setting up virtualization, especially in the cloud, can cost a lot at first, though it can save money in the long run.
    
* Moving to the cloud means needing skilled staff who know how to work with it, either by hiring new people or training current employees.
    
* Storing data on third-party servers can make it more vulnerable to attacks from hackers, which could put sensitive information at risk.
    

## **Hypervisor**

* The hypervisor is a special program that manages virtual machines.
    
* There are two types of hypervisors: Type 1 and Type 2.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713097111518/cb3d9557-453e-40a4-9cc3-a6e2328980a0.png align="center")

**Type 1 Hypervisor / Bare Metal :**

* Runs directly on the computer's hardware.
    
* Examples include LynxSecure, RTS Hypervisor, Oracle VM, Xen, Sun xVM Server, and VirtualLogic VLX.
    
* Type 1 hypervisors don't need a separate host operating system.
    
* This setup is also called a 'Bare Metal'.
    

**Type 2 Hypervisor :**

* Runs as a software program on top of an existing operating system.
    
* Examples include Containers, VirtualBox, KVM, Microsoft Hyper V, VMWare Fusion, Virtual Server 2005 R2, Windows Virtual PC, and VMWare Workstation.
    

### **Containerization**

* Containerization is like packing an app and its stuff into a single box (container) so they stay organized and don't mess with other apps.
    
* Containerization makes managing applications easier by putting all their parts into one container. This container can run on a shared operating system without interfering with other containers.
    

**Key Technologies in Containerization**

* **Docker :**
    
    * Docker is a popular containerization platform.
        
    * It makes it easy to create, share, and run containers.
        
    * Docker Engine is what runs containers.
        
    * Docker Hub is where you can store and share container images in the cloud.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713098574818/c3118b4e-1845-4841-b1b4-325d62c5674c.jpeg align="center")

* **Kubernetes :**
    
    * Kubernetes, also known as K8s, is a free container management platform made by Google.
        
    * It handles tasks like deploying, expanding, and controlling applications in containers across groups of computers.
        
    * Kubernetes has tools like service finding, balancing loads, and fixing problems by itself, making sure applications work well and can grow easily.
        

**Benefits of Containerization in Cloud Computing**

* Containers bundle applications and everything they need to run, making them easy to move between different computer setups. Developers can create and test apps on their own computers and then put them on cloud servers without worrying about compatibility problems.
    
* Containers can be made more or fewer as needed, so apps can handle changes in how many people are using them without any trouble. Cloud systems can even do this automatically, adjusting the number of containers based on how busy the app is.
    
* Containers share the main system of the computer they're on, which means they use less space compared to regular virtual machines. This lets organizations get more out of their computers and save money when using cloud services.
    
* Containers keep everything the same across different stages of making an app, like testing and releasing it. Because everything the app needs is bundled together, there's less chance of something going wrong when moving it between different setups. This makes it more reliable when putting the app out for people to use.
    

### **Orchestration**

* Cloud Orchestration is like the conductor of an orchestra, ensuring that all the instruments (or services) play together harmoniously in the cloud.
    
* It automates the entire process of deploying services, from start to finish, by defining and enforcing a set of rules and procedures.
    
* By using Cloud Orchestration tools, businesses can streamline their operations and achieve faster deployment times, as manual tasks are replaced with automated workflows.
    
* These tools take advantage of the capabilities offered by Infrastructure as a Service (IaaS) providers, such as AWS or Azure, to orchestrate complex deployments with minimal human intervention.
    
* Kubernetes (K8s) is a cloud orchestration tool that automates deployment, scaling, and management of containerized applications across server clusters.
    
* It ensures smooth operation of containerized workloads in the cloud environment.
    
* Kubernetes is an essential component of cloud orchestration, working alongside tools like Terraform, Ansible, and AWS CloudFormation.
    

**Benefits of Orchestration**

* It uses programmed techniques to manage connections and interactions among deployed workflows, whether in public or private cloud infrastructure.
    
* Orchestrated solutions provided by cloud managers offer self-service resource configuration, speeding up service delivery compared to manual configuration based on individual requests.
    
* This platform integrates permission checks and security measures, standardizing templates and enforcing security practices. Admins can review and enhance existing automation scripts.
    
* It is primarily used for deploying servers, managing customer service networks, creating VMs, and accessing specific software in a cloud model.
    

**Advantages**

* Orchestration systematically boosts benefits like speed and saving money through automation.
    
* It helps businesses quickly deploy advanced apps and services while keeping things organized and easy to control.
    
* By using a single portal and cloud-inspired IT service model, orchestration makes everything automated and easy to monitor.
    
* This flexibility speeds up making, launching, and running different services offered by different systems.
    

### **Microservices**

* Historically, software was made using big, single-piece structures called monolithic architectures.
    
* These got tricky as software got more complicated. They weren't good at growing with the complexity.
    
* When you installed or updated them, it was hard and often caused downtime. You couldn't really pick and choose parts.
    
* Cloud microservices are a different way of building software.
    
* Instead of one big piece, you break it down into smaller parts that work independently.
    
* Each part does its own job and talks to the others using clear rules.
    
* This method makes it faster to build and grow software than the old way.
    
* Microservices let you update and change things without disrupting everything else.
    
* They also let you quickly add new features without making users wait.
    
* For example, you could update something every week, and users wouldn't even notice.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713102062509/c8b01ba4-684e-4484-8877-344a4c41c914.png align="center")

**What do cloud microservices help with ?**

* **Problem** : Traditional ways of building big applications are causing trouble.
    
    * They get slower and more complicated as they grow.
        
    * Adding new stuff makes everything more messy, leading to longer times to build and test, and more bugs.
        
* **Solution** : Use cloud microservices instead.
    
    * Break the big application into small parts, each managed by a small team.
        
    * Each part works independently and can be updated without messing up everything else.
        

**Advantages of microservices over traditional methods**

* Parts are made separately, making things less tangled and complex.
    
* Parts can grow or shrink when needed without needing expensive stuff.
    
* If one part breaks, it doesn't ruin everything else. Also, parts can talk to each other better.
    
* Each part is made with the best tools for the job.
    
* It's easy to add new things or fix bugs quickly without causing problems for users.
    

**How Cloud Microservices Work ?**

* **Breaking Down Services** :
    
    * Split the application into small services, each focusing on one task.
        
    * These services can be worked on and changed independently.
        
* **Separate Development and Deployment** :
    
    * Each service is developed and deployed on its own.
        
    * Different teams can use different tools for their services.
        
* **Using APIs for Communication** :
    
    * Services talk to each other through clear rules (APIs).
        
    * This makes sharing information between services easy.
        
* **Keeping Things Flexible** :
    
    * Services are independent, so changes in one don't affect others.
        
    * You can update one part without touching the whole application.
        
* **Scaling Services Independently** :
    
    * Each service can grow or shrink based on its needs.
        
    * Busy services can get bigger, while less used ones stay small.
        
* **Managing Data** :
    
    * Each service can have its own database, using the best technology for its job.
        
    * Data sharing between services can be handled smartly.
        
* **Dealing with Failures** :
    
    * If one service has a problem, it doesn't crash everything.
        
    * Services can handle problems without bringing down the whole application.
        
* **Making Updates Easier** :
    
    * Microservices work well with quick updates and changes.
        
    * You can add new features without slowing down the whole system. Since each service is deployed independently, updates and new features can be released quickly without disrupting the entire application by enabling deployments and Continuous Delivery with DevOps Practices.
        
* **Watching and Fixing Issues** :
    
    * Tools help keep an eye on how each service is doing.
        
    * This helps to fix problems before they become big issues.
        

## **Conclusion**

* Virtualization, Containerization, orchestration and microservices are key parts of modern computing.
    
* Virtualization optimizes hardware usage, leading to cost savings and increased flexibility.
    
* Containerization organizes applications for better management and scalability.
    
* Orchestration helps everything run smoothly by automating tasks, making IT work better for the future.
    
* Microservices break down software into manageable parts, making updates faster and keeping it flexible.