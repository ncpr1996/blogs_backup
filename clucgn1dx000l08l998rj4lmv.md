---
title: "Hard Link & Soft Link"
datePublished: Fri Mar 29 2024 09:27:38 GMT+0000 (Coordinated Universal Time)
cuid: clucgn1dx000l08l998rj4lmv
slug: hard-link-soft-link
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711697550759/62ebc9ad-479f-4f31-911a-748c47910b12.png
tags: ubuntu, operating-system, linux, technology, opensource, linux-for-beginners, linux-basics, system-administration

---

### Introduction

* In Linux, a link is a shortcut that allows multiple names to refer to the same file or folder, making it easier to organize and access your data.
    
* Links are handy because they help you manage your files better, save space on your computer, and create connections between different files.
    

**Here's why links are useful :**

* **Better File Management :** Links let you organize your files by making multiple references to the same data. This means you don't have to make copies of files, which saves space and keeps things well arranged.
    
* **Saving Space :** Instead of copying files, you can use links, which saves disk space. This is especially helpful for large files or when you need the same file in different places.
    
* **Symbolic Relationships :** Links allow you to create symbolic relationships between files or folders. This makes it easier to create shortcuts or aliases for files, making them easier to find and use in your file system.
    

### Types of links

* Hard Link
    
* Soft Link
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711704131470/ba0e0f99-8366-48b9-9ce5-a1afaf4b0787.jpeg align="center")

### Inode Number

* In Unix-like operating systems like Linux, there's something called an "inode" (index node). It's like a file's or directory's ID card.
    
* Each file or directory has its own inode, and it holds important info about them.
    
* Here's what's inside an inode :
    
    * **Metadata :** This is like a file's or directory's details. It includes :
        
        * Type of the file (like a regular file, a directory, or a symbolic link).
            
        * Permissions, which control who can read, write, or execute the file.
            
        * Info about who owns the file and what group it belongs to.
            
        * Timestamps that tell you when the file was last read, modified, or changed.
            
        * The size of the file, measured in bytes.
            
* **Pointers to Data Blocks :**
    
    * For regular files, the inode has pointers to blocks on the disk where the file's data is stored.
        
    * It might have direct pointers for small files or indirect pointers (like single, double, or triple) for larger files that can't fit entirely in the inode.
        
* **File System Pointer :**
    
    * Besides data block pointers, the inode usually has a pointer to the file system's data structure, such as the superblock or the inode table.
        
    * This helps the file system find and manage the inode efficiently.
        
* **Unique Identifier (Inode Number) :**
    
    * Each inode in the file system has a unique ID called an inode number.
        
    * This number is like an index or ID for the file or directory and stays the same throughout its life.
        
    * Inode numbers are assigned in order when files or directories are created.
        
    * They're used by the file system to quickly find and access the right inode and its data blocks.
        

### Hard Link

* When a hard link is created for a file, it adds another filename that directly points to the same file's inode.
    
* All hard links to the same file share the same data blocks on the disk.
    
* Unlike symbolic links (soft links) that point to the target file's path, hard links directly reference the inode.
    
* This makes hard links identical to the original file in terms of data content.
    
* Since all hard links point to the same inode and share data blocks, any changes made to the file via one hard link will affect all other hard links to the same file.
    
* For example, renaming a file through one hard link will rename it for all other hard links.
    
* If you change permissions, ownership, or timestamps of a file using one hard link, those changes will apply to all other hard links to the same file.
    
* All the hard links to a file act as one. So, no matter which link you use to look at or change the file, it always looks and behaves the same.
    
    * Syntax : `ln <source_file> <hard_link_name>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711700692934/f9987312-ce24-47de-891c-209300da26ea.png align="center")
    
* In the above example, if we updated the data in "filename\_2.txt" file. It behaves same as "filename\_1.txt" and act as one.
    
* Both files shares the same Inode number.
    
    * Syntax : `ln -i <source_file> <hard_link_name>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711703877095/81f53e30-9c4e-4af3-8fe4-85b196c8a4f8.png align="center")
    

### Soft Link

* Unlike hard links that can only point to files on the same filesystem, soft links (symbolic links) can point to files and directories located on different filesystems.
    
* This makes symbolic links handy for creating references across different storage locations.
    
* When you create a symbolic link, it keeps the permissions of the target file or directory.
    
* However, the symbolic link itself has its own permissions, deciding who can read, write, or execute it.
    
* Users accessing symbolic links need appropriate permissions to access the target file or directory.
    
* This is determined by both the permissions of the target and the permissions of the link itself.
    
* In listings generated by commands like "ls -l," symbolic links are identified by a special indicator (usually an "l" character) in the file permissions field.
    
* This indicator distinguishes symbolic links from regular files and directories, making it clear that it's a link rather than the actual file or directory.
    
    * Syntax : `ln -s <target> <link_name>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711701973455/a322ed49-3998-456b-a6d2-48c6d820d66e.png align="center")
    
* In the above example, it will create a shortcut.txt in Desktop location.
    
* we can also check that both files are linked by soft links by using the following command.
    
    * Syntax : `ls -l <path of soft link>`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711702287935/1a1438b6-e363-45f4-9dfe-648d952dfc4f.png align="center")
    
    * In this case, I created the soft link in Desktop location so that I can easily access the file.
        

### Conclusion

1. Hard links directly connect to the original file's data on the disk, while soft links contain the path to the original file.
    
2. Hard links share the same inode number and file details as the original file, whereas soft links have their own set of file details and permissions.
    
3. Changes made to the original file are reflected in all hard links, but soft links remain unaffected by changes to the original file.
    
4. Hard links are limited to working within the same filesystem, whereas soft links can point to files or directories across different filesystems.
    
5. Even if the original file is deleted, hard links still access the data, while soft links become broken or inactive if the original file is deleted.