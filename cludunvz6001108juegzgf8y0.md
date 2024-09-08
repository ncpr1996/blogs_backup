---
title: "User & Group Management"
datePublished: Sat Mar 30 2024 08:47:59 GMT+0000 (Coordinated Universal Time)
cuid: cludunvz6001108juegzgf8y0
slug: user-group-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711787684723/60a774b0-467d-431f-b4c3-4c1862e9448b.png
tags: ubuntu, operating-system, linux, technology, devops, opensource-inactive, linux-for-beginners, linux-basics, system-administration

---

## Introduction

* Linux depends on user and group management for structure and security of the system.
    
* Knowing user and group administration is crucial whether you're a system administrator or just a normal user.
    
* It keeps the system well-organized and secure.
    
* Making the most of Linux requires an understanding of handling users and groups.
    

## **Why Manage Users and Groups?**

* **Security :** Sensitive information is protected when people and groups have the appropriate permissions. This prevents unauthorized users from accessing your files or interfering with your machine.
    
* **Resource Sharing :** Sharing resources like files and tools is made simple for members of groups. This promotes productive teamwork on projects.
    
* **Simplified Administration :** Managing the system is made simpler by handling access and permissions through groups. Time and effort can be saved by making modifications for multiple users at once.
    

## **Key Concepts in User and Group Management**

* **User Accounts :** In Linux, each user has a unique name that identifies them. It is known as a username. A user account, associated with every username, contains vital information such as the password, storage location, and available instructions.
    
* **Group Accounts :** Users that share similar needs can socialize together in groups, which are similar to clubs. They assist in grouping users according to the tasks they must do. Every group has a list of its members as well as its own name.
    
* **Permissions :** Permissions in Linux determine who has access to what data and folders. They determine a person's ability to operate, read, and write files. These rights contribute to the overall security and safety.
    
* **Superuser (root) :** The superuser, commonly referred to as root, is the equivalent of the system administrator. Root is infinitely flexible. Large-scale operations like installing new software or adjusting system settings require it.
    

## Superuser (root) Command

### sudo

* In Linux, `sudo` functions similarly to a magic word, granting ordinary users the temporary superuser (root) capabilities necessary to perform complex operations like installing programs or altering crucial configurations.
    
* **Syntax :** `sudo apt update`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711779235887/58420317-2efe-47e0-b42e-1ef3bd002795.png align="center")
    

## User Account Commands

### useradd

* `useradd` is a command used to create new user accounts.
    
* **Syntax :** `useradd -m <user_account_name>`
    
    * here, `-m` which stands for "make home directory"
        
    * Add `sudo` before the useradd command, if it shows "Permission denied".
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711780074495/85ea6193-8ce8-4fee-ac13-37dec9a700a6.png align="center")
    

### passwd

* `passwd` is a command used to create or modify a user's password.
    
* **Syntax :** `passwd <user_account_name>`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711781550955/93d38c4c-b643-4677-897a-6c1b063e0c1e.png align="center")
    
* In the above example, we execute the command for creating the password for the user.
    
* After creating the user password, we can switch the user by using
    
    `su <user_account>`
    
* here, `su` which stands for "switch user".
    

### How to check user account info

* The command `cat /etc/passwd` is used in Linux to display information about user accounts stored in the system's password file.
    
* All user accounts are listed, along with information about the username, home directory, default shell, user ID (UID), and group ID (GID).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711782068919/7112f266-7a11-4fd1-830d-8a5d2e0fb91b.png align="center")
    
* After executing the command, here you can find in the highlighted section.
    

### userdel

* `userdel` is a command used to delete a user.
    
* **Syntax :** `userdel <user_account_name>`
    
* Add `sudo` before the useradd command, if it shows "Permission denied".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711782411663/ace4f485-34a0-472c-aba3-b9859111ce7a.png align="center")
    
* After we deleted the user, we can check using the command `cat /etc/passwd`
    

## Group Account Commands

### groupadd

* `groupadd` is a command used to create new group accounts.
    
* **Syntax :** `groupadd <group_account_name>`
    
* Add `sudo` before the useradd command, if it shows "Permission denied".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711784177854/029d388f-c925-4a62-928b-5633ec175043.png align="center")
    
* In this example,we created four users and two groups and will be added four users in different groups.
    

### How to check group account info

* The `cat /etc/group` command in Linux is used to display information about groups stored in the system's group file.
    
* This command displays a list of all the groups that are present on the system, along with group IDs (GIDs), names, and user memberships in each group.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711784541261/425f6b27-ef5f-46f0-a2c7-cdb4a59af2b7.png align="center")
    
* After executing the command, here you can find in the highlighted section.
    

### gpasswd

* This command is used to add a user to a specific group.
    
* **Syntax :** `gpasswd -a <user_account_name> <group_account_name>`
    
* Add `sudo` before the useradd command, if it shows "Permission denied".
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711785400753/17415335-dccc-41bb-880a-eae29c52a70c.png align="center")

* we can check by using the command of `cat /etc/group`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711785515504/6a37fec3-0edb-4146-a63e-6a73d1fc9958.png align="center")
    
* We can also add "multiple user" in the group at a same time.
    
    * **Syntax :** `gpasswd -M <user_name-1>,<user_name-2> <group_name>`
        
    * here, `-M` which stands for "Multiple user".
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711785754694/be32879e-8175-4ba0-bd81-05b5bf46e86f.png align="center")
    
    * Add `sudo` before the useradd command, if it shows "Permission denied".
        
    * We can check by using the command `cat /etc/group`
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711785986537/86f9f91f-abe1-4008-b831-cd830fef04de.png align="center")
        

### groupdel

* `groupdel` is a command used to delete a group account.
    
* **Syntax :** `groupdel <group_account_name>`
    
* Add `sudo` before the useradd command, if it shows "Permission denied".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711786244942/b6432fa5-7ac4-44ca-93dd-ecbca0893137.png align="center")
    
* Check if it's deleted or not by using `cat /etc/group`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711786343838/14204f72-b0b2-4daf-82d3-cbb09d10314e.png align="center")
    
* Groups which we created are deleted.
    

## Conclusion

* By limiting access, managing users and groups in Linux maintains system security. It is similar to assigning room keys to the appropriate individuals. Proper setup helps in preventing loss and unwanted access.
    
* In a computer system, groups promote collaboration. They enable users with similar needs to work together on projects and exchange resources. This promotes teamwork and speeds up tasks.
    
* Administrators can manage several users at once more easily by managing users and groups. This saves them time and effort because they can modify a large number of users at once.
    
* Administrators of systems can restrict who has access to what information by using user and group management. This means that users only have access to the information that they actually need to perform their jobs.
    
* Linux allows for flexible user and group management that can be adjusted as needed. As the organization expands or undergoes changes, it will be simple to add, modify, or remove users and groups. Over time, this keeps the system secure and functional.