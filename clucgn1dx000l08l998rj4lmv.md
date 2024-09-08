---
title: "Hard Link & Soft Link"
datePublished: Fri Mar 29 2024 09:27:38 GMT+0000 (Coordinated Universal Time)
cuid: clucgn1dx000l08l998rj4lmv
slug: hard-link-soft-link
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711697550759/62ebc9ad-479f-4f31-911a-748c47910b12.png
tags: ubuntu, operating-system, linux, technology, opensource, linux-for-beginners, linux-basics, system-administration

---

### Introduction

* A link in Linux is a shortcut that makes data organization and access easier by allowing several names to refer to the same file or folder.
    
* Links are useful because they enable better file management, free up computer space, and establish links between various files.
    

**Here's why links are useful :**

* **Better File Management :** Links allow you to group files together by referencing the same information more than once. As a result, you may conserve space and maintain organization by not having to create duplicates of your files.
    
* **Saving Space :** Use links instead of copying files to conserve disk space. When you require the same file in multiple locations or with huge files, this is really useful.
    
* **Symbolic Relationships :** You can establish symbolic relationships between files or directories using links. This simplifies the process of creating file aliases or shortcuts, which improves file system accessibility and usability.
    

### Types of links

* Hard Link
    
* Soft Link
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711704131470/ba0e0f99-8366-48b9-9ce5-a1afaf4b0787.jpeg align="center")

### Inode Number

* Linux and other Unix-like operating systems have a concept known as a "inode" (index node). It's similar to the ID card of a file or directory.
    
* Every file or directory has an inode, which contains vital information about it.
    
* What's within an inode is as follows:
    
    * **Metadata :** This is similar to the details of a file or directory. It consists of:
        
        * The file type (such as a directory, an ordinary file, or a symbolic link).
            
        * The file's permissions determine who can read, write, and execute it.
            
        * Details about the group to which the file belongs and who owns it.
            
        * Timestamps that indicate the most recent time the file was read, edited, or modified.
            
        * The size of the file, measured in bytes.
            
* **Pointers to Data Blocks :**
    
    * In the case of normal files, the inode contains pointers to disk blocks containing the contents for the file.
        
    * For smaller files, it may have direct pointers; for bigger files that cannot fit entirely in the inode, it may have indirect pointers (such as single, double, or triple pointers).
        
* **File System Pointer :**
    
    * The inode typically contains a pointer to the file system's data structure, such as the superblock or the inode table, in addition to data block pointers.
        
    * This enables effective inode management and discovery by the file system.
        
* **Unique Identifier (Inode Number) :**
    
    * An inode number is a special ID assigned to each inode in the file system.
        
    * This number is unique to the file or directory and serves as an index or ID for it.
        
    * When files or directories are created, inode numbers are assigned sequentially.
        
    * The file system uses them to quickly locate and access the appropriate inode and its data blocks.
        

### Hard Link

* A hard link for a file adds a new filename that goes directly to the inode of the original file.
    
* The disk's data blocks are shared by all hard links pointing to the same file.
    
* Hard links refer directly to the inode, while symbolic links, also known as soft links, point to the path to the destination file.
    
* As a result, the data content of hard links is exactly the same as that of the original file.
    
* Any modifications made to a file via one hard link will impact all other hard links to the same file since all hard links share data blocks and point to the same inode.
    
* Renaming a file via one hard link, for example, renames it for all other hard links.
    
* Using one hard link to alter a file's ownership, privileges, or timestamps will affect any future hard links that point to the same file.
    
* A file's hard links function as a single unit. Thus, the file always appears and functions the same regardless of whatever link you use to view or edit it.
    
    * Syntax : `ln <source_file> <hard_link_name>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711700692934/f9987312-ce24-47de-891c-209300da26ea.png align="center")
    
* In the above example, if we updated the data in "filename\_2.txt" file. It behaves same as "filename\_1.txt" and act as one.
    
* Both files shares the same Inode number.
    
    * Syntax : `ln -i <source_file> <hard_link_name>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711703877095/81f53e30-9c4e-4af3-8fe4-85b196c8a4f8.png align="center")
    

### Soft Link

* Soft links, also known as symbolic links, have the ability to point to files and directories on separate filesystems, compared to hard links, which can only point to files on the same filesystem.
    
* Symbolic connections are therefore useful for establishing references between several storage sites.
    
* A symbolic link that you create maintains the target file or directory's permissions.
    
* On the other hand, the symbolic link itself controls who can execute, read, and write it.
    
* In order to access the target file or directory through symbolic links, users must have the necessary permissions.
    
* The permissions of the link itself as well as the target itself determine this.
    
* Symbolic links are indicated in listings produced by commands like as `ls -l` by a unique indicator (often a "l" character) in the file permissions field.
    
* This indicator lets you know that a link is all that's there and not the actual file or directory, allowing you to easily distinguish symbolic links from regular files and directories.
    
    * Syntax : `ln -s <target> <link_name>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711701973455/a322ed49-3998-456b-a6d2-48c6d820d66e.png align="center")
    
* In the above example, it will create a shortcut.txt in Desktop location.
    
* we can also check that both files are linked by soft links by using the following command.
    
    * Syntax : `ls -l <path of soft link>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711702287935/1a1438b6-e363-45f4-9dfe-648d952dfc4f.png align="center")
    
    * In this case, I created the soft link in Desktop location so that I can easily access the file.
        

### Conclusion

1. Soft links only contain the path to the original file; hard links connect directly to the original file's data on the disk.
    
2. Soft links have their own set of file permissions and details, but hard links have the same inode number and file details as the original file.
    
3. All hard links automatically update to reflect changes made to the original file, however soft links are not impacted by changes made to the original file.
    
4. While soft links can point to files or directories across various filesystems, hard links are restricted to operating within the same filesystem.
    
5. Hard links maintain access to the data even if the original file is removed, however soft links break or stop working if the original file is removed.