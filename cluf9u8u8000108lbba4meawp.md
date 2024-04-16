---
title: "File Permissions"
datePublished: Sun Mar 31 2024 08:40:36 GMT+0000 (Coordinated Universal Time)
cuid: cluf9u8u8000108lbba4meawp
slug: file-permissions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711861538647/5f797ac4-6407-4049-9e3f-e9189c5ee426.png
tags: ubuntu, operating-system, linux, technology, devops, opensource-inactive, linux-for-beginners, linux-basics, linux-commands, system-administration

---

## Introduction

* File permissions in Linux are important for keeping files safe. They control who can do what with files and folders.
    
* If you're a Linux user or an administrator, knowing how to handle these permissions is really useful.
    
* Basically, file permissions decide who can do specific things with a file or folder, like reading, writing, or running it.
    
    * **Owner :** This is the person who owns the file or folder.
        
    * **Group :** This includes a bunch of users who have similar permissions.
        
    * **Others :** Everyone else who isn't the owner or part of the group.
        
* When you use the `ls` command, you only see file names by default.
    
* To get more details, you can use an "option" which is "flag" with the `ls` command.
    
* Options always start with a `-` symbol.
    
* For example, if you want a long listing, you type `ls -l` .
    
* With the long listing option, each file is shown on a separate line with extra information.
    

## How to check the permission of files

* **Syntax :**`ls -l`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711862537157/f47966e9-a68a-4e5c-bbfb-769b5e58abcc.png align="center")
    
* There's a lot of info in those lines like,
    
    * The first character indicates the type of file: '-' for a regular file, and 'd' for a directory.
        
    * The next nine characters (e.g., `rwxr-xr-x`) show the security settings.
        
    * The column after that indicates the owner of the file (e.g., `chandu`).
        
    * The subsequent column shows the group owner of the file, which often has special access (e.g., `chandu`).
        
    * Another column displays the size of the file in bytes.
        
    * Following that, you'll find the date and time the file was last modified.
        
    * The last column contains the name of the file or directory (e.g., Documents, Downloads, file\_name\_1.txt).
        

## What are the three file permission

| Permission | Description |
| --- | --- |
| Read (r) | View file contents or list directory contents. |
| Write (w) | Modify file contents or manage directory files. |
| Execute (x) | Run file or access directory contents. |

In Linux file permissions, we can add operators to modify the permission.

| **Operators** | Description |
| --- | --- |
| + | Add permissions |
| \- | Remove permissions |
| \= | Set the permissions to the specified values |

In Linux file permissions, we can specify which category option should we choose based on our requirements.

| **Option** | **Category** | **Description** |
| --- | --- | --- |
| u | User | Permissions apply only to the owner of the file or directory. Changes made here won't impact other users. |
| g | Group | Permissions apply only to the group assigned to the file or directory. They don't influence other users. |
| o | Others | Permissions in this category affect all users on the system except the owner and the group. Monitoring these permissions is crucial for system security. |
| a | All | This option includes all three categories: owner, group, and others. It allows you to specify permissions for everyone at once. |

## How to read the permission

Consider the example: "drwxr-xr--"

* `drwx` : The first four characters, `drwx` , denote the permissions for the file type and owner. In this case, it's a directory ("d") with "read", "write", and "execute" permissions for the owner.
    
* `r-x` : The next three characters, `r-x` , represent the permissions for the group. Members of the group have "read" and "execute" permissions but can't modify the directory contents.
    
* `r--` : Finally, the last three characters, `r--` , signify the permissions for others. Any user not in the owner's group or without special permissions can only "read" the directory's contents but can't modify them or execute files within it.
    

## Commands

### chmod

* This command is used to modify security permissions on files in Linux is called `chmod` .
    
* `Chmod` stands for "change mode."
    
* It refers to altering the access permissions of a file.
    
* These permissions, together called the file's security "mode," are shown using nine characters.
    
* For instance, if you wish to grant "read and write" permission to all users ("others") for the file "file\_name\_1.txt" .
    
    * **Syntax :**`chmod o+rw file_name_1.txt`
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711865503620/4aec5606-fd10-4b99-9f44-64bab4d60c7d.png align="center")
        
    * As you can see, it will add new permission of "write".
        
    * You can change multiple permissions simultaneously.
        
    * For instance, if you intend to revoke all permissions from all users, you would enter:
        
        * **Syntax :**`chmod ugo-rwx file_name_1.txt`
            
            or you can also use `chmod a-rwx file_name_1.txt`
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711866441094/e2ec7007-e6d9-493c-b5bd-92c0b375a779.png align="center")
            
    * Here is an another example,
        
    * This command mentioned grants read (r) and write (w) permissions to both the user (u) and the group (g) for the file "file\_name\_1.txt" . Additionally, it removes execute (`x`) permission from others (`o`).
        
        * **Syntax :**`chmod ug+rw,o-x file_name_1.txt`
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711867174295/11f53a34-08c9-458c-8aaf-99f6aa9b4584.png align="center")
            
    * Here, you can set the permissions for the user (u) to read (r), write (w), and execute (x), for the group (g) to read (r) and write (w), and adds read (r) permission for others (o) to the "file\_name\_2.txt" .
        
        * **Syntax :**`chmod u=rwx,g=rw,o+r file_name_2.txt`
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711867940070/d5a27199-8d6a-4671-8979-b131b740c5d9.png align="center")
            
    * Instead of using 'r', 'w', and 'x' to represent permissions, we can use octal notation.
        
    * Each digit in octal notation corresponds to the permissions for the user ('u'), group ('g'), or others ('o').
        
    * So, both methods achieve the same result.
        
    * For instance,
        
        * `chmod a+rwx file_name_1.txt`
            
        * `chmod 777 file_name_1.txt`
            
    * Both methods grant full read, write, and execute permissions (represented as code=7) to the entire group.
        
    * Here is an another example of octal notation
        
        * `chmod u=rwx,g=rw,o=r file_name_1.txt`
            
        * `chmod 764 file_name_1.txt`
            
    * Both methods grant read, write, and execute permissions to user and for group, it will grant read and write permissions and for other, it will grant read permission (represented as code=764).
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711873503171/469379ef-e9e4-42f1-a38d-6bb899545a25.avif align="center")
        

### umask

* Umask is a setting in Unix-like operating systems that determines the default permissions for newly created files and directories.
    
* Umask is represented using a numeric value, typically in octal format, which subtracts from the default permissions. For instance, a umask of `022` would remove write permission for group and others.
    
* By default, umask subtracts permissions from the maximum allowed permissions for files `666` and directories `777` , ensuring a level of security by default.
    
* Users can customize their umask setting to control the default permissions for their files and directories based on their preferences and security requirements.
    
* Here is a common umask settings,
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711869889945/c167aa54-c8b7-46c2-8afa-35b68e3d313d.png align="center")
    
    * **Syntax :**`umask`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711869966271/ca776242-78dd-40e1-b11d-9ec1dd98f0ad.png align="center")
    

### chown

* `chown` is a command in Unix-like operating systems used to change the ownership of files and directories.
    
* With `chown` , you can specify both the user (owner) and group ownership of the file or directory.
    
* For instance, `chown <user_name>:<group_name> <file_name>` changes the ownership of the file `file_name` to the user `user_name` and the group `group_name`.
    
* Generally, only the superuser (root) can change ownership to other users ensuring proper security measures.
    
    * **Syntax :**`sudo chown <user_name> <file_name>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711870929021/26301285-9c27-4dd6-8ae2-de1a65bd2455.png align="center")
    
* Make sure that user exist.
    
* If you want to know how to create user, please check it out this blog [**User & Group Management**](https://devopstour.hashnode.dev/user-group-management)
    

### chgrp

* `chgrp` is a command in Unix-like systems used to change the group ownership of files and directories.
    
* Unlike `chown`, which can change both user and group ownership, `chgrp` is specifically focused on modifying group ownership.
    
* Usually, only the superuser (root) or the file's current owner can change the group ownership of a file or directory, ensuring proper security measures.
    
    * **Syntax :**`sudo chgrp <group_name> <file_name>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711871466818/5bd56f00-43b2-4fbd-b148-ac47bbc2c4fd.png align="center")
    
* Make sure that group exist.
    
* If you want to know how to create group, please check it out this blog [**User & Group Management**](https://devopstour.hashnode.dev/user-group-management)
    

## Conclusion

* File permissions in Linux help control who can access, modify, or execute files and directories, ensuring data security and privacy.
    
* Permissions are assigned to three main categories of users: the file's owner, the group associated with the file, and all other users on the system.
    
* Permissions are granted through read, write, and execute settings, allowing users to view, edit, and run files as needed.
    
* The `chmod` command is used to change file permissions, allowing users to modify access levels based on their requirements.
    
* With file permissions, Linux users can customize to access rights for specific files and directories, ensuring that sensitive information remains protected while assisting collaboration and sharing.