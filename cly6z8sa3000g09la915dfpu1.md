---
title: "Day-2 (90daysofdevops)"
datePublished: Thu Jul 04 2024 08:00:38 GMT+0000 (Coordinated Universal Time)
cuid: cly6z8sa3000g09la915dfpu1
slug: day-2-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720026055231/261d7ad3-7e3a-44c7-aa4f-8c2626a6ad62.jpeg
tags: devops, devops-articles, devops-journey, 90daysofdevops, devopscommunity

---

## Essential Linux Commands for Listing and Navigating Directories

Mastering the Linux filesystem involves understanding how to list contents and navigate directories efficiently. This guide covers essential commands with examples, making it easy for you to follow along.

### Listing Commands

The `ls` command is the go-to for listing files and directories. Various options modify its behavior, providing different levels of detail and filtering. Here are some useful `ls` commands:

#### 1\. Listing Files in Long Format with `ls -l`

```bash
$ ls -l
total 32
drwxr-xr-x 2 user user 4096 Jul  3 14:00 documents
-rw-r--r-- 1 user user 1234 Jul  3 13:55 example.txt
-rwxr-xr-x 1 user user 5678 Jul  3 13:56 script.sh
```

This command provides detailed information about each file and directory, including permissions, number of links, owner, group, size, and modification date.

#### 2\. Listing All Files, Including Hidden Ones with `ls -a`

```bash
$ ls -a
.  ..  .bashrc  .profile  documents  example.txt  script.sh
```

Hidden files (those starting with a dot) are included in the output.

#### 3\. Listing Files with a Specific Extension with `ls *.sh`

```bash
$ ls *.sh
backup.sh  install.sh  script.sh
```

Only files with the `.sh` extension are listed.

#### 4\. Listing Files and Directories with Inode Numbers with `ls -i`

```bash
$ ls -i
123456 documents  234567 example.txt  345678 script.sh
```

Inode numbers, unique identifiers for each file and directory, are displayed.

#### 5\. Listing Only Directories with `ls -d */`

```bash
$ ls -d */
documents/  projects/  scripts/
```

Only directories are listed in the output.

### Directory Commands

Navigating the Linux filesystem requires commands to move between directories and create new ones. Here are some essential `cd` and `mkdir` commands with examples:

#### 1\. Printing the Working Directory with `pwd`

```bash
$ pwd
/home/user/projects
```

The `pwd` command shows the current directory you are in.

#### 2\. Changing Directories with `cd`

##### Changing to a Specific Directory

```bash
$ cd /home/user/documents
$ pwd
/home/user/documents
```

##### Changing to the Home Directory

```bash
$ cd ~
$ pwd
/home/user

$ cd
$ pwd
/home/user
```

##### Changing to the Last Working Directory

```bash
$ cd /home/user/projects
$ cd /home/user/documents
$ cd -
/home/user/projects
```

##### Going One Level Back

```bash
$ cd /home/user/documents
$ cd ..
$ pwd
/home/user
```

##### Going Two Levels Back

```bash
$ cd /home/user/documents/reports
$ cd ../..
$ pwd
/home/user
```

#### 3\. Creating Directories with `mkdir`

##### Creating a New Directory

```bash
$ mkdir newFolder
$ ls
documents  newFolder  projects  script.sh
```

##### Creating a Hidden Directory

```bash
$ mkdir .NewFolder
$ ls -a
.  ..  .NewFolder  documents  projects  script.sh
```

##### Creating Multiple Directories at Once

```bash
$ mkdir A B C D
$ ls
A  B  C  D  documents  projects  script.sh
```

##### Creating a Directory in a Specific Location

```bash
$ mkdir /home/user/Mydirectory
$ ls /home/user
documents  Mydirectory  projects  script.sh
```

##### Creating Nested Directories

```bash
$ mkdir -p A/B/C/D
$ ls -R A
A:
B

A/B:
C

A/B/C:
D

A/B/C/D:
```

With these commands, you can efficiently list contents, navigate through the filesystem, and create directories in Linux. These foundational skills will help you manage your files and directories effectively.

#90daysofdevops