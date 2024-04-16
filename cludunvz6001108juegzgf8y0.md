---
title: "User & Group Management"
datePublished: Sat Mar 30 2024 08:47:59 GMT+0000 (Coordinated Universal Time)
cuid: cludunvz6001108juegzgf8y0
slug: user-group-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711787684723/60a774b0-467d-431f-b4c3-4c1862e9448b.png
tags: ubuntu, operating-system, linux, technology, devops, opensource-inactive, linux-for-beginners, linux-basics, system-administration

---

## Introduction

* Linux relies on managing users and groups for system security and organization.
    
* Whether you're a system administrator or a regular user, understanding user and group management is essential.
    
* It helps keep the system safe and organized.
    
* Knowing how to handle users and groups is crucial for making the most out of Linux.
    

## **Why Manage Users and Groups?**

* **Security :** When you give the right permissions to users and groups, you keep sensitive stuff safe. This stops people from getting into your files or messing with your system without permission.
    
* **Resource Sharing :** Groups make it easy for people to share things like files and tools. This helps teams work together smoothly on projects.
    
* **Simplified Administration :** Handling permissions and access through groups makes it easier to manage the system. You can make changes for lots of users at once, which saves time and effort.
    

## **Key Concepts in User and Group Management**

* **User Accounts :** Every user in Linux has a special name that makes them unique. This name is called a username. Each username is linked to a user account, which holds important details like their password, where their stuff is stored, and what kind of commands they can use.
    
* **Group Accounts :** Groups are like clubs where users with similar needs hang out together. They help organize users based on what they need to do. Each group has its own name and a list of members who belong to it.
    
* **Permissions :** In Linux, permissions control who can do what with files and folders. They decide if someone can read, write, or run a file. These permissions help keep things safe and secure.
    
* **Superuser (root) :** The superuser, also known as root, is like the boss of the system. Root can do anything and go anywhere. It's needed for big tasks like installing new programs or changing system settings.
    

## Superuser (root) Command

### sudo

* `sudo` is like a magic word in Linux that lets regular users do powerful tasks, such as installing software or changing important settings, by temporarily gaining superuser (root) privileges.
    
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
    
* It shows a list of all user accounts, along with details such as the username, user ID (UID), group ID (GID), home directory, and default shell.
    
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
    
* When you run this command, it shows a list of all groups on the system, along with details such as the group name, group ID (GID), and a list of users who belong to each group.
    
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

* Managing users and groups in Linux keeps the system secure by controlling access. It's like giving keys to the right people for specific rooms. Setting this up properly helps prevent unauthorized access and harm.
    
* Groups in a computer system help people work together. They let users with similar needs share stuff and collaborate on projects. This makes teamwork easier and gets things done faster.
    
* Managing users and groups makes it easier for administrators to handle many users at once. This means they can make changes to lots of users all together, which saves them time and effort.
    
* User and group management helps system administrators control who can access what. This means users only get access to the stuff they really need to do their jobs.
    
* In Linux, managing users and groups is flexible and can change as needed. This means it's easy to add, change, or remove users and groups as the organization grows or changes. This helps keep the system efficient and safe as time goes on.