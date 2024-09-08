---
title: "File Permissions"
datePublished: Sun Mar 31 2024 08:40:36 GMT+0000 (Coordinated Universal Time)
cuid: cluf9u8u8000108lbba4meawp
slug: file-permissions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711861538647/5f797ac4-6407-4049-9e3f-e9189c5ee426.png
tags: ubuntu, operating-system, linux, technology, devops, opensource-inactive, linux-for-beginners, linux-basics, linux-commands, system-administration

---

## Introduction

* In Linux, file permissions are crucial to the security of files. They manage the rights of users to access files and folders.
    
* It's quite helpful to know how to manage these permissions if you're an administrator or Linux user.
    
* In essence, file permissions control who has the ability to read, write, and execute a file or folder.
    
    * **Owner :** This is the person who owns the file or folder.
        
    * **Group :** This includes a bunch of users who have similar permissions.
        
    * **Others :** Everyone else who isn't the owner or part of the group.
        
* By default, the `ls` command displays only file names.
    
* You can use the "option" of "flag" with the ls command to obtain extra information.
    
* Options always start with a `-` symbol.
    
* For example, if you want a long listing, you type `ls -l` .
    
* Each file is displayed on a separate line with additional information when the long listing option is selected.
    

## How to check the permission of files

* **Syntax :**`ls -l`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711862537157/f47966e9-a68a-4e5c-bbfb-769b5e58abcc.png align="center")
    
* Many details are contained on those lines, including as
    
    * The first character ('-' for an ordinary file and 'd' for a directory) identifies the kind of file.
        
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
    
* It refers to changing a file's access permissions.
    
* The combination of these permissions is known as the file's security "mode," and it is shown in nine characters.
    
* For example, let's say you want to allow all users ("others") to "read and write" the file "file\_name\_1.txt".
    
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

* In operating systems like Unix, the Umask setting controls the default permissions for newly created files and directories.
    
* Umask is expressed as a number that deducts from the default permissions; this number is usually expressed in octal format. For example, removing write permission for the group and others would result in an umask of `022`.
    
* Umask ensures a level of protection by default by deducting rights for files `666` and directories `777` from the maximum allowed permissions.
    
* In order to manage the default permissions for their files and directories according to their preferences and security needs, users can adjust the umask parameter.
    
* Here is a common umask settings,
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711869889945/c167aa54-c8b7-46c2-8afa-35b68e3d313d.png align="center")
    
    * **Syntax :**`umask`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711869966271/ca776242-78dd-40e1-b11d-9ec1dd98f0ad.png align="center")
    

### chown

* In operating systems similar to Unix, the command `chown` is used to modify the ownership of files and directories.
    
* With `chown` , you can specify both the user (owner) and group ownership of the file or directory.
    
* For instance, `chown <user_name>:<group_name> <file_name>` changes the ownership of the file `file_name` to the user `user_name` and the group `group_name`.
    
* In most cases, ownership can only be transferred to other users by the superuser (root), guaranteeing appropriate security protocols.
    
    * **Syntax :**`sudo chown <user_name> <file_name>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711870929021/26301285-9c27-4dd6-8ae2-de1a65bd2455.png align="center")
    
* Make sure that user exist.
    
* If you want to know how to create user, please check it out this blog [**User & Group Management**](https://devopstour.hashnode.dev/user-group-management)
    

### chgrp

* On Unix-like systems, the `chgrp` command modifies the group ownership of files and directories.
    
* `Chgrp` is dedicated to changing group ownership, in opposite of `chown`, which can alter both user and group ownership.
    
* Usually, only the superuser (root) or the file's current owner can change the group ownership of a file or directory, ensuring proper security measures.
    
    * **Syntax :**`sudo chgrp <group_name> <file_name>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711871466818/5bd56f00-43b2-4fbd-b148-ac47bbc2c4fd.png align="center")
    
* Make sure that group exist.
    
* If you want to know how to create group, please check it out this blog [**User & Group Management**](https://devopstour.hashnode.dev/user-group-management)
    

## Conclusion

* In Linux, file permissions assist in limiting who has the ability to view, alter, or execute files and folders, protecting the security and privacy of data.
    
* Three primary user groups are granted permissions: the owner of the file, the group linked to the file, and every other user on the system.
    
* Users can see, edit, and execute files as needed thanks to permissions that are granted through read, write, and execute settings.
    
* Users can adjust the access levels of a file according to their needs by using the `chmod` command to update the file permissions.
    
* Linux users can use file permissions to customize access privileges for certain files and directories, protecting sensitive data and promoting sharing and cooperation.