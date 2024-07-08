---
title: "Day 6 Task: File Permissions and Access Control Lists"
datePublished: Mon Jul 08 2024 19:59:07 GMT+0000 (Coordinated Universal Time)
cuid: clydeo5dz000g09jtelzj2ct2
slug: day-6-task-file-permissions-and-access-control-lists
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720466759191/62ee9c5d-25b0-469b-a9db-5d1d69e52ac4.avif
tags: devops, devops-articles, devops-journey, 90daysofdevops, devopscommunity

---

## Tasks

* # **Understanding File Permissions:**
    
    * Create a simple file and run `ls -ltr`
        
    * Each of the three permissions are assigned to three defined categories of users. The categories are:
        
        * **Owner:** The owner of the file or application.
            
            * Use `chown` to change the ownership permission of a file or directory.
                
        * **Group:** The group that owns the file or application.
            
            * Use `chgrp` to change the group permission of a file or directory.
                
        * **Others:** All users with access to the system (outside the users in a group).
            
            * Use `chmod` to change the other users' permissions of a file or directory.
                
    * Task: Change the user permissions of the file and note the changes after running `ls -ltr`.
        
    
    **<mark>Output :-</mark>**
    
* ```bash
    nikhil@nikhil-HP-ZBook-15:~$ touch hello.txt
    nikhil@nikhil-HP-ZBook-15:~$ ls -ltr hello.txt 
    -rw-rw-r-- 1 nikhil nikhil 0 Jul  9 00:43 hello.txt
    nikhil@nikhil-HP-ZBook-15:~$ sudo chown nihal hello.txt 
    [sudo] password for nikhil: 
    chown: invalid user: ‘nihal’
    nikhil@nikhil-HP-ZBook-15:~$ cat /etc/passwd
    nikhil@nikhil-HP-ZBook-15:~$ sudo useradd -m nihal
    nikhil@nikhil-HP-ZBook-15:~$ cat /etc/passwd
    nikhil:x:1000:1000:NIKHIL,,,:/home/nikhil:/bin/bash
    admin:x:1001:1001:admin,,,:/home/admin:/bin/bash
    postfix:x:129:137::/var/spool/postfix:/usr/sbin/nologin
    nihal:x:1002:1002::/home/nihal:/bin/sh
    nikhil@nikhil-HP-ZBook-15:~$ sudo chown nihal hello.txt 
    nikhil@nikhil-HP-ZBook-15:~$ ls -ltr hello.txt 
    -rw-rw-r-- 1 nihal nikhil 0 Jul  9 00:43 hello.txt
    nikhil@nikhil-HP-ZBook-15:~$ sudo groupadd -g avengers
    groupadd: invalid group ID 'avengers'
    nikhil@nikhil-HP-ZBook-15:~$ sudo groupadd  avengers
    nikhil@nikhil-HP-ZBook-15:~$ cat /etc/group
    nihal:x:1002:
    avengers:x:1003:
    nikhil@nikhil-HP-ZBook-15:~$ 
    nikhil@nikhil-HP-ZBook-15:~$ ls -ltr hello.txt 
    -rw-rw-r-- 1 nihal nikhil 0 Jul  9 00:43 hello.txt
    nikhil@nikhil-HP-ZBook-15:~$ sudo chgrp avengers hello.txt 
    nikhil@nikhil-HP-ZBook-15:~$ ls -ltr hello.txt 
    -rw-rw-r-- 1 nihal avengers 0 Jul  9 00:43 hello.txt
    nikhil@nikhil-HP-ZBook-15:~$ chmod 700 hello.txt 
    chmod: changing permissions of 'hello.txt': Operation not permitted
    nikhil@nikhil-HP-ZBook-15:~$  sudo chmod 700 hello.txt 
    nikhil@nikhil-HP-ZBook-15:~$ ls -ltr hello.txt 
    -rwx------ 1 nihal avengers 0 Jul  9 00:43 hello.txt
    ```
    
    **Write an article about file permissions based on your understanding from the notes**
    

**ANS :**\-File permissions are a core aspect of Linux, crucial for system security and management. They determine who can read, write, or execute files and directories. This article will introduce you to the basics of Linux file permissions and guide you through using numeric values with the `chmod` command to set these permissions.

Understanding File Permissions:-

In Linux, every file and directory has associated permissions that control access for three types of users:

1. **Owner**: The user who owns the file.
    
2. **Group**: A set of users that the file belongs to.
    
3. **Others**: Everyone else who has access to the system.
    

* ### Examples
    
    #### Common Numeric Values
    
    * `7` (rwx) = 4 (read) + 2 (write) + 1 (execute)
        
    * `6` (rw-) = 4 (read) + 2 (write)
        
    * `5` (r-x) = 4 (read) + 1 (execute)
        
    * `4` (r--) = 4 (read)
        
    
* ### **Acess Control Lists (ACL):**
    
* Read about ACL and try out the commands `getfacl` and `setfacl`.
    
* Task: Create a directory and set specific ACL permissions for different users and groups. Verify the permissions using `getfacl`.
    

```bash
nikhil@nikhil-HP-ZBook-15:~$ mkdir swap
nikhil@nikhil-HP-ZBook-15:~$ ls
 backup           Documents   'MEGA downloads'   snap
 colors.txt       Downloads    nikhil.txt        swap
 Desktop          fruits.txt   Pictures          Templates
'Devops folder'   git          Public            test_cron_first.txt
 devops.txt       hello.txt    script.sh         Videos
nikhil@nikhil-HP-ZBook-15:~$ sudo setfacl -m u:nihal:rw swap
[sudo] password for nikhil: 
nikhil@nikhil-HP-ZBook-15:~$ sudo setfacl -m g:avengers:r swap
nikhil@nikhil-HP-ZBook-15:~$ getfacl swap
# file: swap
# owner: nikhil
# group: nikhil
user::rwx
user:nihal:rw-
group::rwx
group:avengers:r--
mask::rwx
other::r-x
```

### **Understanding Sticky Bit, SUID, and SGID**

Sticky bit, SUID (Set User ID), and SGID (Set Group ID) are special types of permissions that provide additional security and functionality.

* **Sticky Bit:** When set on a directory, it ensures that only the file owner, the directory owner, or the root user can delete or rename files within that directory.
    
* **SUID:** When set on an executable file, it allows the file to be executed with the permissions of the file owner.
    
* **SGID:** When set on a directory, files created within the directory inherit the group ownership of the directory.
    

### Tasks: Sticky Bit, SUID, and SGID

1. **Read about sticky bit, SUID, and SGID.**
    
2. **Task:** Create examples demonstrating the use of sticky bit, SUID, and SGID, and explain their significance.
    
    ```bash
     # Sticky Bit
     $ mkdir /tmp/sticky
     $ chmod +t /tmp/sticky
    
     # SUID
     $ sudo chmod u+s /usr/bin/passwd
    
     # SGID
     $ mkdir /tmp/sgid
     $ chmod g+s /tmp/sgid
    ```
    

* #90daysofdevops