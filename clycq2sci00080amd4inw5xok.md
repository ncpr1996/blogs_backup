---
title: "AWS Network & Security { Part - IV }"
seoTitle: "AWS Key Pairs: A Simple Guide to Secure Access"
seoDescription: "Learn how to create and manage AWS key pairs for secure access with this straightforward guide."
datePublished: Mon Jul 08 2024 08:30:39 GMT+0000 (Coordinated Universal Time)
cuid: clycq2sci00080amd4inw5xok
slug: aws-network-security-part-iv
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719292241646/18d1009f-ea9f-44aa-937c-88a0e8af58a5.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1720316662124/6aed29d5-000f-44af-a165-9a7e7721e781.png
tags: cloud, aws, cloud-computing, devops, best-practices, sre, aws-security, aws-certified-solutions-architect-associate, devops-articles, keypair, devopscommunity, ec2-instance, aws-security-best-practices, ssh-key-pair-for-ec2

---

## What is a Key Pairs in AWS EC2

* **Definition :** A key pair in AWS EC2 is a set of security credentials used to authenticate access to EC2 instances.
    
* **Components :** It consists of a public key and a private key.
    
* **Purpose :** The key pair ensures that only authorized users can connect to the EC2 instances.
    

## Key Features of Key Pairs

* **Secure Access** : Provides a secure way to connect to EC2 instances.
    
* **Public-Private Key Encryption** : Uses asymmetric encryption for secure communication.
    
* **SSH Access** : Commonly used for SSH (Secure Shell) access to Linux instances.
    
* **Integration** : Can be integrated with other AWS services for enhanced security.
    
* **No Passwords** : Eliminates the need for password-based authentication.
    

## How Key Pairs Work

* **Generation Process** :
    
    * **Public Key** : AWS generates and stores the public key on the EC2 instance.
        
    * **Private Key** : AWS provides the private key to you for download. It’s crucial to save it securely, as AWS does not retain a copy.
        
* **SSH Connection** :
    
    * **Client-Side** : When connecting to an EC2 instance, you use an SSH client (e.g., PuTTY, OpenSSH).
        
    * **Private Key Usage** : The SSH client uses the private key to encrypt a session initiation request.
        
    * **Public Key Verification** : The EC2 instance uses the stored public key to verify the private key, establishing a secure connection if they match.
        
* **Session Establishment** :
    
    * **Symmetric Key Exchange** : After the initial verification, the SSH protocol establishes a symmetric encryption key for the session, ensuring data exchanged is secure.
        
* **Encryption and Decryption** :
    
    * **Data Encryption** : Data sent to the EC2 instance is encrypted with the public key.
        
    * **Data Decryption** : Only the corresponding private key can decrypt this data, ensuring that intercepted data cannot be read without the private key.
        
* **Login Process** :
    
    * **Authorized Keys File** : On Linux instances, the public key is added to the `~/.ssh/authorized_keys` file of the specified user.
        
    * **Access Control** : Only users with the private key that matches the public key in the `authorized_keys` file can log in.
        
* **Key Pair Storage** :
    
    * **AWS Storage** : AWS stores only the public key.
        
    * **User Responsibility** : The user is responsible for storing and managing the private key securely.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720349418343/43f81155-f7dd-4992-b41d-c988b8d6007a.png align="center")
    
* **No Passwords Needed** :
    
    * **Key-Based Authentication** : Eliminates the need for passwords, reducing the risk of password-related vulnerabilities.
        
* **Revocation and Rotation** :
    
    * **Key Revocation** : If a private key is compromised, you can revoke access by removing the corresponding public key from the `authorized_keys` file.
        
    * **Key Rotation** : Regularly updating key pairs helps mitigate the risk of key compromise. We can learn about key updates in the upcoming blogs. For example, if we delete the key file, how can we create another key and attach it to the EC2 instance?
        

## Creating a Key Pair During Instance Launch

* **AWS Management Console** :
    
    * **Step 1 : Launch Instance** :
        
        * Go to the EC2 dashboard.
            
        * Click on "Launch Instance".
            
    * **Step 2 : Choose an Amazon Machine Image (AMI)** :
        
        * Select an AMI that suits your needs (e.g., Amazon Linux 2, Ubuntu).
            
    * **Step 3 : Choose an Instance Type**:
        
        * Select the instance type (e.g., t2.micro).
            
    * **Step 4 : Configure Key Pair** :
        
        * **Create a New Key Pair**:
            
            * select "Create new key pair".
                
            * Provide a name for your key pair.
                
            * Choose the key pair file format:
                
                * **PEM** (for SSH clients).
                    
                * **PPK** (for PuTTY).
                    
            * Click on "Create key pair".
                
            * Download the private key file (.pem or .ppk). Save it securely, as you won't be able to download it again.
                
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719226120230/faeb8423-a02e-48fd-8d2c-181741f6584b.png align="center")
            
        * **Use an Existing Key Pair**:
            
            * If you already have a key pair, you can select it from the "Key pair name" dropdown list.
                
            * You can create the Key pair by navigate to the EC2 dashboard, choose "Key Pairs," and create a new key pair.
                
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719226255211/a51f294c-cc3b-4bb9-a937-7c419d1d0408.png align="center")
            
    * **Step 5 :**
        
        * **Configure other details :**
            
            * Like security groups , storage , number of instances, advance details.
                

## Best practices for Key Pairs

* **Secure Storage** :
    
    * **Encryption** : Store private keys in an encrypted format using tools like AWS KMS or third-party solutions.
        
    * **Access Control** : Restrict access to the private key to only those who need it.
        
* **Regular Rotation** :
    
    * **Schedule Key Rotations** : Regularly rotate key pairs to minimize the risk of long-term exposure.
        
    * **Automate Rotation** : Use scripts or tools to automate key rotation and distribution.
        
* **Backup** :
    
    * **Secure Backup** : Keep backups of private keys in secure, encrypted locations.
        
    * **Disaster Recovery** : Ensure backups are part of your disaster recovery plan.
        
* **Access Control** :
    
    * **Least Privilege Principle** : Grant the minimum permissions necessary for users to perform their tasks.
        
    * **IAM Policies** : Use AWS IAM policies to control who can create, use, and manage key pairs.
        
* **Monitoring and Auditing** :
    
    * **Log Access** : Enable logging to track who accesses and uses your key pairs.
        
    * **Review Logs** : Regularly review logs for any unusual or unauthorized access attempts.
        
* **Key Pair Management** :
    
    * **Tagging** : Use tags to organize and identify key pairs for easier management.
        
    * **Documentation** : Maintain documentation for all key pairs, including creation dates and usage contexts.
        
* **Environment Segregation** :
    
    * **Separate Keys for Different Environments** : Use different key pairs for development, testing, and production environments to isolate access.
        
    * **Project-specific Keys** : Create key pairs specific to projects or teams to limit access scope.
        
* **Emergency Access Procedures** :
    
    * **Backup Admin Key** : Have a backup administrative key pair stored securely for emergency access.
        
    * **Emergency Plans** : Develop and document procedures for what to do if a key pair is compromised.
        
* **Avoid Hardcoding Keys** :
    
    * **Configuration Management** : Use configuration management tools to manage key distribution rather than hardcoding them in scripts or applications.
        
    * **Environment Variables** : Store key paths in environment variables or secure configuration stores.
        

## Use Cases

* **SSH Access** : Secure SSH access to Linux/Unix-based EC2 instances.
    
* **Remote Administration** : Managing and administrating remote servers.
    
* **Automated Scripts** : Automated deployment scripts that require secure access.
    
* **Multi-Factor Authentication** : Enhanced security with multi-factor authentication for instance access.
    

## Pros and Cons

### Pros :

* **Enhanced Security** : Provides a high level of security for accessing instances.
    
* **Simplicity** : Easy to set up and use.
    
* **No Passwords** : Reduces the risk of password-related attacks.
    

### Cons :

* **Key Management** : Requires careful management and storage of private keys.
    
* **Loss of Key** : Losing the private key can lock you out of the instance.
    
* **Initial Setup** : Requires initial setup and configuration.
    

## Conclusion

* **Summary** : AWS Key Pairs are essential for securely accessing EC2 instances, leveraging public-private key encryption for robust security.
    
* **Recommendation** : Follow best practices to ensure secure and efficient use of key pairs, making them an integral part of your cloud security strategy.
    

## References

* [**Key Pairs**](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)