---
title: "Day 7 Task: Understanding Package Manager and Systemctl"
datePublished: Tue Jul 09 2024 18:42:06 GMT+0000 (Coordinated Universal Time)
cuid: clyercz58000309l04rgj4lk7
slug: day-7-task-understanding-package-manager-and-systemctl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720550512908/3e35d616-cd26-4868-81a5-83f6533bc747.jpeg
tags: devops, devops-articles, 90daysofdevops, devopscommunity

---

## Understanding Package Managers

### What is a Package Manager?

A package manager is a tool that automates the process of installing, upgrading, configuring, and removing software packages on an operating system. It simplifies software management by handling dependencies, versions, and other complexities.

### What is a Package?

A package is an archive file containing all the files necessary to install a software program. This includes the binary executable, configuration files, and metadata about dependencies. Packages can be GUI applications, command-line tools, or libraries required by other software programs.

### Different Kinds of Package Managers

Package managers differ based on the packaging system. Some examples include:

* **RPM-based systems:** Use `yum` and `dnf` (e.g., Fedora, RHEL, CentOS).
    
* **DEB-based systems:** Use `apt-get` and `aptitude` (e.g., Debian, Ubuntu).
    
* ## Tasks
    

**Install Docker and Jenkins:**

* Install Docker and Jenkins on your system from your terminal using package managers.
    

```bash
nikhil@nikhil-HP-ZBook-15:~$ sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
[sudo] password for nikhil: 
Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 https://repo.protonvpn.com/debian stable InRelease                       
Hit:3 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:4 http://in.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:5 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:6 https://ppa.launchpadcontent.net/git-core/ppa/ubuntu jammy InRelease     
Hit:7 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease
Get:8 https://mega.nz/linux/repo/xUbuntu_22.04 ./ InRelease [2,961 B]
Fetched 2,961 B in 1s (2,155 B/s)    
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
lsb-release is already the newest version (11.1.0ubuntu4).
lsb-release set to manually installed.
ca-certificates is already the newest version (20230311ubuntu0.22.04.1).
ca-certificates set to manually installed.
gnupg is already the newest version (2.2.27-3ubuntu2.1).
gnupg set to manually installed.
The following packages were automatically installed and are no longer required:
  libmediainfo0v5 libmms0 libtinyxml2-9 libzen0v5
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  curl
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 194 kB of archives.
After this operation, 454 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 curl amd64 7.81.0-1ubuntu1.16 [194 kB]
Fetched 194 kB in 1s (137 kB/s)
Selecting previously unselected package curl.
(Reading database ... 220291 files and directories currently installed.)
Preparing to unpack .../curl_7.81.0-1ubuntu1.16_amd64.deb ...
Unpacking curl (7.81.0-1ubuntu1.16) ...
Setting up curl (7.81.0-1ubuntu1.16) ...
Processing triggers for man-db (2.10.2-1) ...
nikhil@nikhil-HP-ZBook-15:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
nikhil@nikhil-HP-ZBook-15:~$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
nikhil@nikhil-HP-ZBook-15:~$ sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
Get:1 https://download.docker.com/linux/ubuntu jammy InRelease [48.8 kB]
Get:2 https://download.docker.com/linux/ubuntu jammy/stable amd64 Packages [35.6 kB]
Hit:3 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:4 https://repo.protonvpn.com/debian stable InRelease                       
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:6 http://in.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:7 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:8 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease 
Hit:9 https://ppa.launchpadcontent.net/git-core/ppa/ubuntu jammy InRelease
Get:10 https://mega.nz/linux/repo/xUbuntu_22.04 ./ InRelease [2,961 B]
Fetched 87.4 kB in 1s (97.0 kB/s)     
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmediainfo0v5 libmms0 libtinyxml2-9 libzen0v5
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  docker-buildx-plugin docker-ce-rootless-extras docker-compose-plugin
  libslirp0 pigz slirp4netns
Suggested packages:
  aufs-tools cgroupfs-mount | cgroup-lite
The following NEW packages will be installed:
  containerd.io docker-buildx-plugin docker-ce docker-ce-cli
  docker-ce-rootless-extras docker-compose-plugin libslirp0 pigz slirp4netns
0 upgraded, 9 newly installed, 0 to remove and 8 not upgraded.
Need to get 122 MB of archives.
After this operation, 437 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 https://download.docker.com/linux/ubuntu jammy/stable amd64 containerd.io amd64 1.7.18-1 [30.5 MB]
Get:2 http://in.archive.ubuntu.com/ubuntu jammy/universe amd64 pigz amd64 2.6-1 [63.6 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 libslirp0 amd64 4.6.1-1build1 [61.5 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu jammy/universe amd64 slirp4netns amd64 1.0.1-2 [28.2 kB]
Get:5 https://download.docker.com/linux/ubuntu jammy/stable amd64 docker-buildx-plugin amd64 0.15.1-1~ubuntu.22.04~jammy [29.8 MB]
Get:6 https://download.docker.com/linux/ubuntu jammy/stable amd64 docker-ce-cli amd64 5:27.0.3-1~ubuntu.22.04~jammy [14.6 MB]
Get:7 https://download.docker.com/linux/ubuntu jammy/stable amd64 docker-ce amd64 5:27.0.3-1~ubuntu.22.04~jammy [25.3 MB]
Get:8 https://download.docker.com/linux/ubuntu jammy/stable amd64 docker-ce-rootless-extras amd64 5:27.0.3-1~ubuntu.22.04~jammy [9,319 kB]
Get:9 https://download.docker.com/linux/ubuntu jammy/stable amd64 docker-compose-plugin amd64 2.28.1-1~ubuntu.22.04~jammy [12.5 MB]
Fetched 122 MB in 12s (10.6 MB/s)                                              
Selecting previously unselected package pigz.
(Reading database ... 220298 files and directories currently installed.)
Preparing to unpack .../0-pigz_2.6-1_amd64.deb ...
Unpacking pigz (2.6-1) ...
Selecting previously unselected package containerd.io.
Preparing to unpack .../1-containerd.io_1.7.18-1_amd64.deb ...
Unpacking containerd.io (1.7.18-1) ...
Selecting previously unselected package docker-buildx-plugin.
Preparing to unpack .../2-docker-buildx-plugin_0.15.1-1~ubuntu.22.04~jammy_amd64.deb ...
Unpacking docker-buildx-plugin (0.15.1-1~ubuntu.22.04~jammy) ...
Selecting previously unselected package docker-ce-cli.
Preparing to unpack .../3-docker-ce-cli_5%3a27.0.3-1~ubuntu.22.04~jammy_amd64.deb ...
Unpacking docker-ce-cli (5:27.0.3-1~ubuntu.22.04~jammy) ...
Selecting previously unselected package docker-ce.
Preparing to unpack .../4-docker-ce_5%3a27.0.3-1~ubuntu.22.04~jammy_amd64.deb ...
Unpacking docker-ce (5:27.0.3-1~ubuntu.22.04~jammy) ...
Selecting previously unselected package docker-ce-rootless-extras.
Preparing to unpack .../5-docker-ce-rootless-extras_5%3a27.0.3-1~ubuntu.22.04~jammy_amd64.deb ...
Unpacking docker-ce-rootless-extras (5:27.0.3-1~ubuntu.22.04~jammy) ...
Selecting previously unselected package docker-compose-plugin.
Preparing to unpack .../6-docker-compose-plugin_2.28.1-1~ubuntu.22.04~jammy_amd64.deb ...
Unpacking docker-compose-plugin (2.28.1-1~ubuntu.22.04~jammy) ...
Selecting previously unselected package libslirp0:amd64.
Preparing to unpack .../7-libslirp0_4.6.1-1build1_amd64.deb ...
Unpacking libslirp0:amd64 (4.6.1-1build1) ...
Selecting previously unselected package slirp4netns.
Preparing to unpack .../8-slirp4netns_1.0.1-2_amd64.deb ...
Unpacking slirp4netns (1.0.1-2) ...
Setting up docker-buildx-plugin (0.15.1-1~ubuntu.22.04~jammy) ...
Setting up containerd.io (1.7.18-1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /lib/systemd/system/containerd.service.
Setting up docker-compose-plugin (2.28.1-1~ubuntu.22.04~jammy) ...
Setting up docker-ce-cli (5:27.0.3-1~ubuntu.22.04~jammy) ...
Setting up libslirp0:amd64 (4.6.1-1build1) ...
Setting up pigz (2.6-1) ...
Setting up docker-ce-rootless-extras (5:27.0.3-1~ubuntu.22.04~jammy) ...
Setting up slirp4netns (1.0.1-2) ...
Setting up docker-ce (5:27.0.3-1~ubuntu.22.04~jammy) ...
Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /lib/systemd/system/docker.service.
Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /lib/systemd/system/docker.socket.
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.8) ...
nikhil@nikhil-HP-ZBook-15:~$ sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
c1ec31eb5944: Pull complete 
Digest: sha256:94323f3e5e09a8b9515d74337010375a456c909543e1ff1538f5116d38ab3989
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

nikhil@nikhil-HP-ZBook-15:~$ curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
nikhil@nikhil-HP-ZBook-15:~$ sudo apt-get update
sudo apt-get install jenkins
Hit:1 https://download.docker.com/linux/ubuntu jammy InRelease
Ign:2 https://pkg.jenkins.io/debian binary/ InRelease                          
Get:3 https://pkg.jenkins.io/debian binary/ Release [2,044 B]                  
Get:4 https://pkg.jenkins.io/debian binary/ Release.gpg [833 B]                
Get:5 https://pkg.jenkins.io/debian binary/ Packages [62.9 kB]                 
Hit:6 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:7 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:8 https://repo.protonvpn.com/debian stable InRelease                       
Hit:9 http://in.archive.ubuntu.com/ubuntu jammy InRelease                      
Get:10 https://mega.nz/linux/repo/xUbuntu_22.04 ./ InRelease [2,961 B]
Hit:11 https://ppa.launchpadcontent.net/git-core/ppa/ubuntu jammy InRelease    
Hit:12 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:13 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease
Fetched 68.8 kB in 1s (52.0 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmediainfo0v5 libmms0 libtinyxml2-9 libzen0v5
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  net-tools
The following NEW packages will be installed:
  jenkins net-tools
0 upgraded, 2 newly installed, 0 to remove and 8 not upgraded.
Need to get 91.4 MB of archives.
After this operation, 94.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:2 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 net-tools amd64 1.60+git20181103.0eebece-1ubuntu5 [204 kB]
Get:1 https://pkg.jenkins.io/debian binary/ jenkins 2.466 [91.2 MB]            
Fetched 91.4 MB in 11s (8,023 kB/s)                                            
Selecting previously unselected package net-tools.
(Reading database ... 220557 files and directories currently installed.)
Preparing to unpack .../net-tools_1.60+git20181103.0eebece-1ubuntu5_amd64.deb ...
Unpacking net-tools (1.60+git20181103.0eebece-1ubuntu5) ...
Selecting previously unselected package jenkins.
Preparing to unpack .../archives/jenkins_2.466_all.deb ...
Unpacking jenkins (2.466) ...
Setting up net-tools (1.60+git20181103.0eebece-1ubuntu5) ...
Setting up jenkins (2.466) ...
Created symlink /etc/systemd/system/multi-user.target.wants/jenkins.service → /lib/systemd/system/jenkins.service.
Could not execute systemctl:  at /usr/bin/deb-systemd-invoke line 142.
Processing triggers for man-db (2.10.2-1) ...
nikhil@nikhil-HP-ZBook-15:~$ sudo systemctl start jenkins
Job for jenkins.service failed because the control process exited with error code.
See "systemctl status jenkins.service" and "journalctl -xeu jenkins.service" for details.
nikhil@nikhil-HP-ZBook-15:~$ sudo systemctl enable jenkins
Synchronizing state of jenkins.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable jenkins
nikhil@nikhil-HP-ZBook-15:~$ docker --version
Docker version 27.0.3, build 7d4bcd8
nikhil@nikhil-HP-ZBook-15:~$ sudo systemctl status jenkins
× jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor prese>
     Active: failed (Result: exit-code) since Tue 2024-07-09 22:50:47 IST; 2min>
   Main PID: 9917 (code=exited, status=1/FAILURE)
        CPU: 7ms

Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled resta>
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integ>
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request r>
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with res>
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuo>
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request r>
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with res>
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuo>
lines 1-14/14 (END)...skipping...
× jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2024-07-09 22:50:47 IST; 2min 44s ago
   Main PID: 9917 (code=exited, status=1/FAILURE)
        CPU: 7ms

Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 5.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server
lines 1-14/14 (END)


× jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2024-07-09 22:50:47 IST; 2min 44s ago
   Main PID: 9917 (code=exited, status=1/FAILURE)
        CPU: 7ms

Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 5.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
lines 1-14/14 (END)
nikhil@nikhil-HP-ZBook-15:~$ sudo journalctl -u jenkins.service
Jul 09 22:50:45 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:50:45 nikhil-HP-ZBook-15 jenkins[9792]: jenkins: failed to find a valid Java installation
Jul 09 22:50:45 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Main process exited, code=exited, status=1/FAILURE
Jul 09 22:50:45 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:45 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 1.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:50:46 nikhil-HP-ZBook-15 jenkins[9817]: jenkins: failed to find a valid Java installation
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Main process exited, code=exited, status=1/FAILURE
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 2.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:50:46 nikhil-HP-ZBook-15 jenkins[9868]: jenkins: failed to find a valid Java installation
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Main process exited, code=exited, status=1/FAILURE
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 3.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:50:46 nikhil-HP-ZBook-15 jenkins[9893]: jenkins: failed to find a valid Java installation
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Main process exited, code=exited, status=1/FAILURE
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 4.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:50:46 nikhil-HP-ZBook-15 jenkins[9917]: jenkins: failed to find a valid Java installation
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Main process exited, code=exited, status=1/FAILURE
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 5.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
nikhil@nikhil-HP-ZBook-15:~$ sudo systemctl cat jenkins.service
# /lib/systemd/system/jenkins.service
#
# This file is managed by systemd(1). Do NOT edit this file manually!
# To override these settings, run:
#
#     systemctl edit jenkins
#
# For more information about drop-in files, see:
#
#     https://www.freedesktop.org/software/systemd/man/systemd.unit.html
#

[Unit]
Description=Jenkins Continuous Integration Server
Requires=network.target
After=network.target

[Service]
Type=notify
NotifyAccess=main
ExecStart=/usr/bin/jenkins
Restart=on-failure
SuccessExitStatus=143

# Configures the time to wait for start-up. If Jenkins does not signal start-up
# completion within the configured time, the service will be considered failed
# and will be shut down again. Takes a unit-less value in seconds, or a time span
# value such as "5min 20s". Pass "infinity" to disable the timeout logic.
#TimeoutStartSec=90

# Unix account that runs the Jenkins daemon
# Be careful when you change this, as you need to update the permissions of
# $JENKINS_HOME, $JENKINS_LOG, and (if you have already run Jenkins)
# $JENKINS_WEBROOT.
User=jenkins
Group=jenkins

# Directory where Jenkins stores its configuration and workspaces
Environment="JENKINS_HOME=/var/lib/jenkins"
WorkingDirectory=/var/lib/jenkins

# Location of the Jenkins WAR
#Environment="JENKINS_WAR=/usr/share/java/jenkins.war"

nikhil@nikhil-HP-ZBook-15:~$ sudo apt-get install openjdk-11-jdk
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmediainfo0v5 libmms0 libtinyxml2-9 libzen0v5
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  ca-certificates-java fonts-dejavu-extra java-common libatk-wrapper-java libatk-wrapper-java-jni libice-dev libpthread-stubs0-dev libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxt-dev openjdk-11-jdk-headless openjdk-11-jre openjdk-11-jre-headless x11proto-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  default-jre libice-doc libsm-doc libx11-doc libxcb-doc libxt-doc openjdk-11-demo openjdk-11-source visualvm fonts-ipafont-gothic fonts-ipafont-mincho fonts-wqy-microhei
  | fonts-wqy-zenhei
The following NEW packages will be installed:
  ca-certificates-java fonts-dejavu-extra java-common libatk-wrapper-java libatk-wrapper-java-jni libice-dev libpthread-stubs0-dev libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxt-dev openjdk-11-jdk openjdk-11-jdk-headless openjdk-11-jre openjdk-11-jre-headless x11proto-dev xorg-sgml-doctools xtrans-dev
0 upgraded, 20 newly installed, 0 to remove and 8 not upgraded.
Need to get 120 MB of archives.
After this operation, 274 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 java-common all 0.72build2 [6,782 B]
Get:2 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 openjdk-11-jre-headless amd64 11.0.23+9-1ubuntu1~22.04.1 [42.5 MB]
Get:3 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 ca-certificates-java all 20190909ubuntu1.2 [12.1 kB]                                                        
Get:4 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 fonts-dejavu-extra all 2.37-2build1 [2,041 kB]                                                                      
Get:5 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 libatk-wrapper-java all 0.38.0-5build1 [53.1 kB]                                                                    
Get:6 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 libatk-wrapper-java-jni amd64 0.38.0-5build1 [49.0 kB]                                                              
Get:7 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 xorg-sgml-doctools all 1:1.11-1.1 [10.9 kB]                                                                         
Get:8 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 x11proto-dev all 2021.5-1 [604 kB]                                                                                  
Get:9 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 libice-dev amd64 2:1.0.10-1build2 [51.4 kB]                                                                         
Get:10 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 libpthread-stubs0-dev amd64 0.4-1build2 [5,516 B]                                                                  
Get:11 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 libsm-dev amd64 2:1.2.3-1build2 [18.1 kB]                                                                          
Get:12 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 libxau-dev amd64 1:1.0.9-1build5 [9,724 B]                                                                         
Get:13 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 libxdmcp-dev amd64 1:1.1.3-0ubuntu5 [26.5 kB]                                                                      
Get:14 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 xtrans-dev all 1.4.0-1 [68.9 kB]                                                                                   
Get:15 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 libxcb1-dev amd64 1.14-3ubuntu3 [86.5 kB]                                                                          
Get:16 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libx11-dev amd64 2:1.7.5-1ubuntu0.3 [744 kB]                                                               
Get:17 http://in.archive.ubuntu.com/ubuntu jammy/main amd64 libxt-dev amd64 1:1.2.1-1 [396 kB]                                                                                 
Get:18 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 openjdk-11-jre amd64 11.0.23+9-1ubuntu1~22.04.1 [214 kB]                                                   
Get:19 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 openjdk-11-jdk-headless amd64 11.0.23+9-1ubuntu1~22.04.1 [73.5 MB]                                         
Get:20 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 openjdk-11-jdk amd64 11.0.23+9-1ubuntu1~22.04.1 [13.9 kB]                                                  
Fetched 120 MB in 1min 3s (1,913 kB/s)                                                                                                                                         
Selecting previously unselected package java-common.
(Reading database ... 220621 files and directories currently installed.)
Preparing to unpack .../00-java-common_0.72build2_all.deb ...
Unpacking java-common (0.72build2) ...
Selecting previously unselected package openjdk-11-jre-headless:amd64.
Preparing to unpack .../01-openjdk-11-jre-headless_11.0.23+9-1ubuntu1~22.04.1_amd64.deb ...
Unpacking openjdk-11-jre-headless:amd64 (11.0.23+9-1ubuntu1~22.04.1) ...
Selecting previously unselected package ca-certificates-java.
Preparing to unpack .../02-ca-certificates-java_20190909ubuntu1.2_all.deb ...
Unpacking ca-certificates-java (20190909ubuntu1.2) ...
Selecting previously unselected package fonts-dejavu-extra.
Preparing to unpack .../03-fonts-dejavu-extra_2.37-2build1_all.deb ...
Unpacking fonts-dejavu-extra (2.37-2build1) ...
Selecting previously unselected package libatk-wrapper-java.
Preparing to unpack .../04-libatk-wrapper-java_0.38.0-5build1_all.deb ...
Unpacking libatk-wrapper-java (0.38.0-5build1) ...
Selecting previously unselected package libatk-wrapper-java-jni:amd64.
Preparing to unpack .../05-libatk-wrapper-java-jni_0.38.0-5build1_amd64.deb ...
Unpacking libatk-wrapper-java-jni:amd64 (0.38.0-5build1) ...
Selecting previously unselected package xorg-sgml-doctools.
Preparing to unpack .../06-xorg-sgml-doctools_1%3a1.11-1.1_all.deb ...
Unpacking xorg-sgml-doctools (1:1.11-1.1) ...
Selecting previously unselected package x11proto-dev.
Preparing to unpack .../07-x11proto-dev_2021.5-1_all.deb ...
Unpacking x11proto-dev (2021.5-1) ...
Selecting previously unselected package libice-dev:amd64.
Preparing to unpack .../08-libice-dev_2%3a1.0.10-1build2_amd64.deb ...
Unpacking libice-dev:amd64 (2:1.0.10-1build2) ...
Selecting previously unselected package libpthread-stubs0-dev:amd64.
Preparing to unpack .../09-libpthread-stubs0-dev_0.4-1build2_amd64.deb ...
Unpacking libpthread-stubs0-dev:amd64 (0.4-1build2) ...
Selecting previously unselected package libsm-dev:amd64.
Preparing to unpack .../10-libsm-dev_2%3a1.2.3-1build2_amd64.deb ...
Unpacking libsm-dev:amd64 (2:1.2.3-1build2) ...
Selecting previously unselected package libxau-dev:amd64.
Preparing to unpack .../11-libxau-dev_1%3a1.0.9-1build5_amd64.deb ...
Unpacking libxau-dev:amd64 (1:1.0.9-1build5) ...
Selecting previously unselected package libxdmcp-dev:amd64.
Preparing to unpack .../12-libxdmcp-dev_1%3a1.1.3-0ubuntu5_amd64.deb ...
Unpacking libxdmcp-dev:amd64 (1:1.1.3-0ubuntu5) ...
Selecting previously unselected package xtrans-dev.
Preparing to unpack .../13-xtrans-dev_1.4.0-1_all.deb ...
Unpacking xtrans-dev (1.4.0-1) ...
Selecting previously unselected package libxcb1-dev:amd64.
Preparing to unpack .../14-libxcb1-dev_1.14-3ubuntu3_amd64.deb ...
Unpacking libxcb1-dev:amd64 (1.14-3ubuntu3) ...
Selecting previously unselected package libx11-dev:amd64.
Preparing to unpack .../15-libx11-dev_2%3a1.7.5-1ubuntu0.3_amd64.deb ...
Unpacking libx11-dev:amd64 (2:1.7.5-1ubuntu0.3) ...
Selecting previously unselected package libxt-dev:amd64.
Preparing to unpack .../16-libxt-dev_1%3a1.2.1-1_amd64.deb ...
Unpacking libxt-dev:amd64 (1:1.2.1-1) ...
Selecting previously unselected package openjdk-11-jre:amd64.
Preparing to unpack .../17-openjdk-11-jre_11.0.23+9-1ubuntu1~22.04.1_amd64.deb ...
Unpacking openjdk-11-jre:amd64 (11.0.23+9-1ubuntu1~22.04.1) ...
Selecting previously unselected package openjdk-11-jdk-headless:amd64.
Preparing to unpack .../18-openjdk-11-jdk-headless_11.0.23+9-1ubuntu1~22.04.1_amd64.deb ...
Unpacking openjdk-11-jdk-headless:amd64 (11.0.23+9-1ubuntu1~22.04.1) ...
Selecting previously unselected package openjdk-11-jdk:amd64.
Preparing to unpack .../19-openjdk-11-jdk_11.0.23+9-1ubuntu1~22.04.1_amd64.deb ...
Unpacking openjdk-11-jdk:amd64 (11.0.23+9-1ubuntu1~22.04.1) ...
Setting up java-common (0.72build2) ...
Setting up libpthread-stubs0-dev:amd64 (0.4-1build2) ...
Setting up xtrans-dev (1.4.0-1) ...
Setting up fonts-dejavu-extra (2.37-2build1) ...
Setting up xorg-sgml-doctools (1:1.11-1.1) ...
Setting up libatk-wrapper-java (0.38.0-5build1) ...
Setting up libatk-wrapper-java-jni:amd64 (0.38.0-5build1) ...
Setting up openjdk-11-jre-headless:amd64 (11.0.23+9-1ubuntu1~22.04.1) ...
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/java to provide /usr/bin/java (java) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jjs to provide /usr/bin/jjs (jjs) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode
Setting up openjdk-11-jre:amd64 (11.0.23+9-1ubuntu1~22.04.1) ...
Setting up openjdk-11-jdk-headless:amd64 (11.0.23+9-1ubuntu1~22.04.1) ...
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jar to provide /usr/bin/jar (jar) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/javac to provide /usr/bin/javac (javac) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/javap to provide /usr/bin/javap (javap) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jcmd to provide /usr/bin/jcmd (jcmd) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jdeprscan to provide /usr/bin/jdeprscan (jdeprscan) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jdeps to provide /usr/bin/jdeps (jdeps) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jfr to provide /usr/bin/jfr (jfr) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jimage to provide /usr/bin/jimage (jimage) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jlink to provide /usr/bin/jlink (jlink) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jmod to provide /usr/bin/jmod (jmod) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jps to provide /usr/bin/jps (jps) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jshell to provide /usr/bin/jshell (jshell) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jaotc to provide /usr/bin/jaotc (jaotc) in auto mode
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jhsdb to provide /usr/bin/jhsdb (jhsdb) in auto mode
Setting up openjdk-11-jdk:amd64 (11.0.23+9-1ubuntu1~22.04.1) ...
update-alternatives: using /usr/lib/jvm/java-11-openjdk-amd64/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode
Setting up ca-certificates-java (20190909ubuntu1.2) ...
head: cannot open '/etc/ssl/certs/java/cacerts' for reading: No such file or directory
Adding debian:Microsoft_RSA_Root_Certificate_Authority_2017.pem
Adding debian:CFCA_EV_ROOT.pem
Adding debian:emSign_Root_CA_-_C1.pem
Adding debian:COMODO_Certification_Authority.pem
Adding debian:E-Tugra_Global_Root_CA_RSA_v3.pem
Adding debian:DigiCert_High_Assurance_EV_Root_CA.pem
Adding debian:T-TeleSec_GlobalRoot_Class_3.pem
Adding debian:D-TRUST_Root_Class_3_CA_2_2009.pem
Adding debian:Secure_Global_CA.pem
Adding debian:COMODO_ECC_Certification_Authority.pem
Adding debian:GlobalSign_Root_CA_-_R3.pem
Adding debian:GTS_Root_R2.pem
Adding debian:emSign_Root_CA_-_G1.pem
Adding debian:TunTrust_Root_CA.pem
Adding debian:GlobalSign_Root_E46.pem
Adding debian:Hellenic_Academic_and_Research_Institutions_RootCA_2015.pem
Adding debian:GLOBALTRUST_2020.pem
Adding debian:Telia_Root_CA_v2.pem
Adding debian:Security_Communication_RootCA3.pem
Adding debian:ssl-cert-snakeoil.pem
Adding debian:Autoridad_de_Certificacion_Firmaprofesional_CIF_A62634068_2.pem
Adding debian:GlobalSign_Root_CA.pem
Adding debian:Trustwave_Global_Certification_Authority.pem
Adding debian:AffirmTrust_Premium.pem
Adding debian:HARICA_TLS_ECC_Root_CA_2021.pem
Adding debian:DigiCert_Assured_ID_Root_G2.pem
Adding debian:SwissSign_Silver_CA_-_G2.pem
Adding debian:GlobalSign_Root_CA_-_R6.pem
Adding debian:QuoVadis_Root_CA_2.pem
Adding debian:SZAFIR_ROOT_CA2.pem
Adding debian:DigiCert_TLS_RSA4096_Root_G5.pem
Adding debian:DigiCert_Assured_ID_Root_CA.pem
Adding debian:USERTrust_ECC_Certification_Authority.pem
Adding debian:emSign_ECC_Root_CA_-_C3.pem
Adding debian:UCA_Global_G2_Root.pem
Adding debian:Baltimore_CyberTrust_Root.pem
Adding debian:Certainly_Root_R1.pem
Adding debian:Go_Daddy_Root_Certificate_Authority_-_G2.pem
Adding debian:ISRG_Root_X1.pem
Adding debian:UCA_Extended_Validation_Root.pem
Adding debian:SecureTrust_CA.pem
Adding debian:QuoVadis_Root_CA_3.pem
Adding debian:QuoVadis_Root_CA_2_G3.pem
Adding debian:DigiCert_Global_Root_G2.pem
Adding debian:OISTE_WISeKey_Global_Root_GB_CA.pem
Adding debian:Security_Communication_ECC_RootCA1.pem
Adding debian:emSign_ECC_Root_CA_-_G3.pem
Adding debian:Entrust_Root_Certification_Authority_-_G2.pem
Adding debian:Certainly_Root_E1.pem
Adding debian:Microsec_e-Szigno_Root_CA_2009.pem
Adding debian:TWCA_Global_Root_CA.pem
Adding debian:D-TRUST_EV_Root_CA_1_2020.pem
Adding debian:DigiCert_TLS_ECC_P384_Root_G5.pem
Adding debian:AffirmTrust_Premium_ECC.pem
Adding debian:Amazon_Root_CA_1.pem
Adding debian:Autoridad_de_Certificacion_Firmaprofesional_CIF_A62634068.pem
Adding debian:Certum_Trusted_Network_CA_2.pem
Adding debian:AC_RAIZ_FNMT-RCM_SERVIDORES_SEGUROS.pem
Adding debian:Hellenic_Academic_and_Research_Institutions_ECC_RootCA_2015.pem
Adding debian:Hongkong_Post_Root_CA_3.pem
Adding debian:certSIGN_Root_CA_G2.pem
Adding debian:ePKI_Root_Certification_Authority.pem
Adding debian:ACCVRAIZ1.pem
Adding debian:IdenTrust_Commercial_Root_CA_1.pem
Adding debian:Starfield_Class_2_CA.pem
Adding debian:QuoVadis_Root_CA_1_G3.pem
Adding debian:Amazon_Root_CA_3.pem
Adding debian:HARICA_TLS_RSA_Root_CA_2021.pem
Adding debian:GTS_Root_R4.pem
Adding debian:SwissSign_Gold_CA_-_G2.pem
Adding debian:Entrust.net_Premium_2048_Secure_Server_CA.pem
Adding debian:QuoVadis_Root_CA_3_G3.pem
Adding debian:Certum_Trusted_Network_CA.pem
Adding debian:GlobalSign_Root_R46.pem
Adding debian:COMODO_RSA_Certification_Authority.pem
Adding debian:T-TeleSec_GlobalRoot_Class_2.pem
Adding debian:Trustwave_Global_ECC_P384_Certification_Authority.pem
Adding debian:SSL.com_EV_Root_Certification_Authority_RSA_R2.pem
Adding debian:SSL.com_Root_Certification_Authority_RSA.pem
Adding debian:Certum_EC-384_CA.pem
Adding debian:Entrust_Root_Certification_Authority_-_EC1.pem
Adding debian:GTS_Root_R3.pem
Adding debian:DigiCert_Global_Root_CA.pem
Adding debian:DigiCert_Global_Root_G3.pem
Adding debian:AffirmTrust_Commercial.pem
Adding debian:NetLock_Arany_=Class_Gold=_Főtanúsítvány.pem
Adding debian:TUBITAK_Kamu_SM_SSL_Kok_Sertifikasi_-_Surum_1.pem
Adding debian:GDCA_TrustAUTH_R5_ROOT.pem
Adding debian:E-Tugra_Certification_Authority.pem
Adding debian:AffirmTrust_Networking.pem
Adding debian:GlobalSign_ECC_Root_CA_-_R4.pem
Adding debian:Trustwave_Global_ECC_P256_Certification_Authority.pem
Adding debian:Amazon_Root_CA_2.pem
Adding debian:Atos_TrustedRoot_2011.pem
Adding debian:GTS_Root_R1.pem
Adding debian:TeliaSonera_Root_CA_v1.pem
Adding debian:certSIGN_ROOT_CA.pem
Adding debian:Certigna.pem
Adding debian:ISRG_Root_X2.pem
Adding debian:Certigna_Root_CA.pem
Adding debian:DigiCert_Assured_ID_Root_G3.pem
Adding debian:USERTrust_RSA_Certification_Authority.pem
Adding debian:Go_Daddy_Class_2_CA.pem
Adding debian:e-Szigno_Root_CA_2017.pem
Adding debian:HiPKI_Root_CA_-_G1.pem
Adding debian:Entrust_Root_Certification_Authority.pem
Adding debian:SSL.com_Root_Certification_Authority_ECC.pem
Adding debian:vTrus_Root_CA.pem
Adding debian:vTrus_ECC_Root_CA.pem
Adding debian:Izenpe.com.pem
Adding debian:GlobalSign_ECC_Root_CA_-_R5.pem
Adding debian:OISTE_WISeKey_Global_Root_GC_CA.pem
Adding debian:SSL.com_EV_Root_Certification_Authority_ECC.pem
Adding debian:Entrust_Root_Certification_Authority_-_G4.pem
Adding debian:Buypass_Class_2_Root_CA.pem
Adding debian:Security_Communication_Root_CA.pem
Adding debian:Amazon_Root_CA_4.pem
Adding debian:TWCA_Root_Certification_Authority.pem
Adding debian:Hongkong_Post_Root_CA_1.pem
Adding debian:Starfield_Services_Root_Certificate_Authority_-_G2.pem
Adding debian:CA_Disig_Root_R2.pem
Adding debian:Buypass_Class_3_Root_CA.pem
Adding debian:E-Tugra_Global_Root_CA_ECC_v3.pem
Adding debian:IdenTrust_Public_Sector_Root_CA_1.pem
Adding debian:ANF_Secure_Server_Root_CA.pem
Adding debian:XRamp_Global_CA_Root.pem
Adding debian:Certum_Trusted_Root_CA.pem
Adding debian:Starfield_Root_Certificate_Authority_-_G2.pem
Adding debian:D-TRUST_BR_Root_CA_1_2020.pem
Adding debian:Comodo_AAA_Services_root.pem
Adding debian:Security_Communication_RootCA2.pem
Adding debian:Microsoft_ECC_Root_Certificate_Authority_2017.pem
Adding debian:SecureSign_RootCA11.pem
Adding debian:DigiCert_Trusted_Root_G4.pem
Adding debian:D-TRUST_Root_Class_3_CA_2_EV_2009.pem
Adding debian:AC_RAIZ_FNMT-RCM.pem
Adding debian:Actalis_Authentication_Root_CA.pem
Adding debian:NAVER_Global_Root_Certification_Authority.pem
done.
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for fontconfig (2.13.1-4.2ubuntu5) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for ca-certificates (20230311ubuntu0.22.04.1) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...

done.
done.
Processing triggers for sgml-base (1.30) ...
Setting up x11proto-dev (2021.5-1) ...
Setting up libxau-dev:amd64 (1:1.0.9-1build5) ...
Setting up libice-dev:amd64 (2:1.0.10-1build2) ...
Setting up libsm-dev:amd64 (2:1.2.3-1build2) ...
Setting up libxdmcp-dev:amd64 (1:1.1.3-0ubuntu5) ...
Setting up libxcb1-dev:amd64 (1.14-3ubuntu3) ...
Setting up libx11-dev:amd64 (2:1.7.5-1ubuntu0.3) ...
Setting up libxt-dev:amd64 (1:1.2.1-1) ...
nikhil@nikhil-HP-ZBook-15:~$ sudo service jenkins start
Job for jenkins.service failed because the control process exited with error code.
See "systemctl status jenkins.service" and "journalctl -xeu jenkins.service" for details.
nikhil@nikhil-HP-ZBook-15:~$ sudo lsof -i :8080
nikhil@nikhil-HP-ZBook-15:~$ sudo journalctl -u jenkins.service
Jul 09 22:50:45 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:50:45 nikhil-HP-ZBook-15 jenkins[9792]: jenkins: failed to find a valid Java installation
Jul 09 22:50:45 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Main process exited, code=exited, status=1/FAILURE
Jul 09 22:50:45 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:45 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 1.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:50:46 nikhil-HP-ZBook-15 jenkins[9817]: jenkins: failed to find a valid Java installation
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Main process exited, code=exited, status=1/FAILURE
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 2.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:50:46 nikhil-HP-ZBook-15 jenkins[9868]: jenkins: failed to find a valid Java installation
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Main process exited, code=exited, status=1/FAILURE
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 3.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:50:46 nikhil-HP-ZBook-15 jenkins[9893]: jenkins: failed to find a valid Java installation
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Main process exited, code=exited, status=1/FAILURE
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 4.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:50:46 nikhil-HP-ZBook-15 jenkins[9917]: jenkins: failed to find a valid Java installation
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Main process exited, code=exited, status=1/FAILURE
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:46 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 5.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:47 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
Jul 09 22:50:53 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
Jul 09 22:58:06 nikhil-HP-ZBook-15 systemd[1]: Starting Jenkins Continuous Integration Server...
Jul 09 22:58:06 nikhil-HP-ZBook-15 jenkins[12278]: Running with Java 11 from /usr/lib/jvm/java-11-openjdk-amd64, which is older than the minimum required version (Java 17).

nikhil@nikhil-HP-ZBook-15:~$ java -version
openjdk version "11.0.23" 2024-04-16
OpenJDK Runtime Environment (build 11.0.23+9-post-Ubuntu-1ubuntu122.04.1)
OpenJDK 64-Bit Server VM (build 11.0.23+9-post-Ubuntu-1ubuntu122.04.1, mixed mode, sharing)
nikhil@nikhil-HP-ZBook-15:~$ sudo apt-get install openjdk-11-jdk
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
openjdk-11-jdk is already the newest version (11.0.23+9-1ubuntu1~22.04.1).
The following packages were automatically installed and are no longer required:
  libmediainfo0v5 libmms0 libtinyxml2-9 libzen0v5
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
nikhil@nikhil-HP-ZBook-15:~$ sudo systemctl restart jenkins
sudo systemctl status jenkins
Job for jenkins.service failed because the control process exited with error code.
See "systemctl status jenkins.service" and "journalctl -xeu jenkins.service" for details.
● jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
     Active: activating (auto-restart) (Result: exit-code) since Tue 2024-07-09 23:00:05 IST; 13ms ago
    Process: 12552 ExecStart=/usr/bin/jenkins (code=exited, status=1/FAILURE)
   Main PID: 12552 (code=exited, status=1/FAILURE)
        CPU: 533ms
nikhil@nikhil-HP-ZBook-15:~$ sudo journalctl -xeu jenkins.service
░░ Subject: Unit failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ The unit jenkins.service has entered the 'failed' state with result 'exit-code'.
Jul 09 23:00:07 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
░░ Subject: A start job for unit jenkins.service has failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ A start job for unit jenkins.service has finished with a failure.
░░ 
░░ The job identifier is 5669 and the job result is failed.
Jul 09 23:00:07 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 5.
░░ Subject: Automatic restarting of a unit has been scheduled
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ Automatic restarting of the unit jenkins.service has been scheduled, as the result for
░░ the configured Restart= setting for the unit.
Jul 09 23:00:07 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
░░ Subject: A stop job for unit jenkins.service has finished
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ A stop job for unit jenkins.service has finished.
░░ 
░░ The job identifier is 5742 and the job result is done.
Jul 09 23:00:07 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 23:00:07 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
░░ Subject: Unit failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ The unit jenkins.service has entered the 'failed' state with result 'exit-code'.
Jul 09 23:00:07 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
░░ Subject: A start job for unit jenkins.service has failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ A start job for unit jenkins.service has finished with a failure.
░░ 
░░ The job identifier is 5742 and the job result is failed.

nikhil@nikhil-HP-ZBook-15:~$ sudo tail -n 100 /var/log/jenkins/jenkins.log
tail: cannot open '/var/log/jenkins/jenkins.log' for reading: No such file or directory
nikhil@nikhil-HP-ZBook-15:~$ java -version
openjdk version "11.0.23" 2024-04-16
OpenJDK Runtime Environment (build 11.0.23+9-post-Ubuntu-1ubuntu122.04.1)
OpenJDK 64-Bit Server VM (build 11.0.23+9-post-Ubuntu-1ubuntu122.04.1, mixed mode, sharing)
nikhil@nikhil-HP-ZBook-15:~$ sudo apt-get install openjdk-11-jdk
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
openjdk-11-jdk is already the newest version (11.0.23+9-1ubuntu1~22.04.1).
The following packages were automatically installed and are no longer required:
  libmediainfo0v5 libmms0 libtinyxml2-9 libzen0v5
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
nikhil@nikhil-HP-ZBook-15:~$ sudo chown -R jenkins:jenkins /var/lib/jenkins
nikhil@nikhil-HP-ZBook-15:~$ sudo lsof -i :8080
nikhil@nikhil-HP-ZBook-15:~$ sudo systemctl restart jenkins
sudo systemctl status jenkins
Job for jenkins.service failed because the control process exited with error code.
See "systemctl status jenkins.service" and "journalctl -xeu jenkins.service" for details.
● jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
     Active: activating (auto-restart) (Result: exit-code) since Tue 2024-07-09 23:03:11 IST; 13ms ago
    Process: 12884 ExecStart=/usr/bin/jenkins (code=exited, status=1/FAILURE)
   Main PID: 12884 (code=exited, status=1/FAILURE)
        CPU: 587ms
nikhil@nikhil-HP-ZBook-15:~$ sudo journalctl -xeu jenkins.service
░░ Subject: Unit failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ The unit jenkins.service has entered the 'failed' state with result 'exit-code'.
Jul 09 23:03:13 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
░░ Subject: A start job for unit jenkins.service has failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ A start job for unit jenkins.service has finished with a failure.
░░ 
░░ The job identifier is 6107 and the job result is failed.
Jul 09 23:03:14 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 5.
░░ Subject: Automatic restarting of a unit has been scheduled
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ Automatic restarting of the unit jenkins.service has been scheduled, as the result for
░░ the configured Restart= setting for the unit.
Jul 09 23:03:14 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
░░ Subject: A stop job for unit jenkins.service has finished
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ A stop job for unit jenkins.service has finished.
░░ 
░░ The job identifier is 6180 and the job result is done.
Jul 09 23:03:14 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 23:03:14 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
░░ Subject: Unit failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ The unit jenkins.service has entered the 'failed' state with result 'exit-code'.
Jul 09 23:03:14 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
░░ Subject: A start job for unit jenkins.service has failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ A start job for unit jenkins.service has finished with a failure.
░░ 
░░ The job identifier is 6180 and the job result is failed.

nikhil@nikhil-HP-ZBook-15:~$ sudo tail -n 100 /var/log/jenkins/jenkins.log
tail: cannot open '/var/log/jenkins/jenkins.log' for reading: No such file or directory
nikhil@nikhil-HP-ZBook-15:~$ sudo journalctl -xeu jenkins.service
░░ Subject: Unit failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ The unit jenkins.service has entered the 'failed' state with result 'exit-code'.
Jul 09 23:03:13 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
░░ Subject: A start job for unit jenkins.service has failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ A start job for unit jenkins.service has finished with a failure.
░░ 
░░ The job identifier is 6107 and the job result is failed.
Jul 09 23:03:14 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Scheduled restart job, restart counter is at 5.
░░ Subject: Automatic restarting of a unit has been scheduled
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ Automatic restarting of the unit jenkins.service has been scheduled, as the result for
░░ the configured Restart= setting for the unit.
Jul 09 23:03:14 nikhil-HP-ZBook-15 systemd[1]: Stopped Jenkins Continuous Integration Server.
░░ Subject: A stop job for unit jenkins.service has finished
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ A stop job for unit jenkins.service has finished.
░░ 
░░ The job identifier is 6180 and the job result is done.
Jul 09 23:03:14 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Start request repeated too quickly.
Jul 09 23:03:14 nikhil-HP-ZBook-15 systemd[1]: jenkins.service: Failed with result 'exit-code'.
░░ Subject: Unit failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ The unit jenkins.service has entered the 'failed' state with result 'exit-code'.
Jul 09 23:03:14 nikhil-HP-ZBook-15 systemd[1]: Failed to start Jenkins Continuous Integration Server.
░░ Subject: A start job for unit jenkins.service has failed
░░ Defined-By: systemd
░░ Support: http://www.ubuntu.com/support
░░ 
░░ A start job for unit jenkins.service has finished with a failure.
░░ 
░░ The job identifier is 6180 and the job result is failed.

nikhil@nikhil-HP-ZBook-15:~$ java -version
openjdk version "11.0.23" 2024-04-16
OpenJDK Runtime Environment (build 11.0.23+9-post-Ubuntu-1ubuntu122.04.1)
OpenJDK 64-Bit Server VM (build 11.0.23+9-post-Ubuntu-1ubuntu122.04.1, mixed mode, sharing)
nikhil@nikhil-HP-ZBook-15:~$ sudo apt-get install openjdk-11-jdk
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
openjdk-11-jdk is already the newest version (11.0.23+9-1ubuntu1~22.04.1).
The following packages were automatically installed and are no longer required:
  libmediainfo0v5 libmms0 libtinyxml2-9 libzen0v5
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
nikhil@nikhil-HP-ZBook-15:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  libmediainfo0v5 libmms0 libtinyxml2-9 libzen0v5
0 upgraded, 0 newly installed, 4 to remove and 8 not upgraded.
After this operation, 7,431 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 221799 files and directories currently installed.)
Removing libmediainfo0v5:amd64 (21.09+dfsg-4) ...
Removing libmms0:amd64 (0.6.4-3) ...
Removing libtinyxml2-9:amd64 (9.0.0+dfsg-3) ...
Removing libzen0v5:amd64 (0.4.39-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.8) ...
nikhil@nikhil-HP-ZBook-15:~$ sudo systemctl cat jenkins.service
# /lib/systemd/system/jenkins.service
#
# This file is managed by systemd(1). Do NOT edit this file manually!
# To override these settings, run:
#
#     systemctl edit jenkins
#
# For more information about drop-in files, see:
#
#     https://www.freedesktop.org/software/systemd/man/systemd.unit.html
#

[Unit]
Description=Jenkins Continuous Integration Server
Requires=network.target
After=network.target

[Service]
Type=notify
NotifyAccess=main
ExecStart=/usr/bin/jenkins
Restart=on-failure
SuccessExitStatus=143

# Configures the time to wait for start-up. If Jenkins does not signal start-up
# completion within the configured time, the service will be considered failed
# and will be shut down again. Takes a unit-less value in seconds, or a time span
# value such as "5min 20s". Pass "infinity" to disable the timeout logic.
#TimeoutStartSec=90

# Unix account that runs the Jenkins daemon
# Be careful when you change this, as you need to update the permissions of
# $JENKINS_HOME, $JENKINS_LOG, and (if you have already run Jenkins)
# $JENKINS_WEBROOT.
User=jenkins
Group=jenkins

# Directory where Jenkins stores its configuration and workspaces
Environment="JENKINS_HOME=/var/lib/jenkins"
WorkingDirectory=/var/lib/jenkins

# Location of the Jenkins WAR
#Environment="JENKINS_WAR=/usr/share/java/jenkins.war"

nikhil@nikhil-HP-ZBook-15:~$ ls -l /usr/bin/jenkins
-rwxr-xr-x 1 root root 4592 Jul  3 00:08 /usr/bin/jenkins
nikhil@nikhil-HP-ZBook-15:~$ sudo ls -l /var/lib/jenkins
sudo chown -R jenkins:jenkins /var/lib/jenkins
total 0
nikhil@nikhil-HP-ZBook-15:~$ sudo mkdir -p /var/log/jenkins
sudo chown -R jenkins:jenkins /var/log/jenkins
nikhil@nikhil-HP-ZBook-15:~$ sudo lsof -i :8080
nikhil@nikhil-HP-ZBook-15:~$ sudo -u jenkins /usr/bin/jenkins
Running with Java 11 from /usr/lib/jvm/java-11-openjdk-amd64, which is older than the minimum required version (Java 17).
Supported Java versions are: [17, 21]
See https://jenkins.io/redirect/java-support/ for more information.
nikhil@nikhil-HP-ZBook-15:~$ ls -l /usr/bin/jenkins
-rwxr-xr-x 1 root root 4592 Jul  3 00:08 /usr/bin/jenkins
nikhil@nikhil-HP-ZBook-15:~$ sudo ls -l /var/lib/jenkins
sudo chown -R jenkins:jenkins /var/lib/jenkins
total 0
nikhil@nikhil-HP-ZBook-15:~$ sudo lsof -i :8080
nikhil@nikhil-HP-ZBook-15:~$ sudo -u jenkins /usr/bin/jenkins
Running with Java 11 from /usr/lib/jvm/java-11-openjdk-amd64, which is older than the minimum required version (Java 17).
Supported Java versions are: [17, 21]
See https://jenkins.io/redirect/java-support/ for more information.
nikhil@nikhil-HP-ZBook-15:~$ sudo apt-get update
sudo apt-get install openjdk-17-jdk
Hit:1 https://download.docker.com/linux/ubuntu jammy InRelease
Ign:2 https://pkg.jenkins.io/debian binary/ InRelease                                                                                                                     
Hit:3 https://pkg.jenkins.io/debian binary/ Release                                                                                                                          
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                  
Get:6 http://security.ubuntu.com/ubuntu jammy-security InRelease [129 kB]                                                                                                      
Hit:7 https://repo.protonvpn.com/debian stable InRelease                                                                                                                       
Hit:8 http://in.archive.ubuntu.com/ubuntu jammy InRelease                                                                    
Get:9 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease [128 kB]                                            
Hit:10 https://ppa.launchpadcontent.net/git-core/ppa/ubuntu jammy InRelease                                                    
Get:11 https://mega.nz/linux/repo/xUbuntu_22.04 ./ InRelease [2,961 B]                                                         
Hit:12 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease
Get:13 http://in.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [654 kB]
Get:14 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [1,790 kB]
Get:15 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [1,101 kB]
Get:16 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [716 kB]
Fetched 4,522 kB in 3s (1,387 kB/s)                         
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  openjdk-17-jdk-headless openjdk-17-jre openjdk-17-jre-headless
Suggested packages:
  openjdk-17-demo openjdk-17-source visualvm fonts-ipafont-gothic fonts-ipafont-mincho fonts-wqy-microhei | fonts-wqy-zenhei
The following NEW packages will be installed:
  openjdk-17-jdk openjdk-17-jdk-headless openjdk-17-jre openjdk-17-jre-headless
0 upgraded, 4 newly installed, 0 to remove and 8 not upgraded.
Need to get 120 MB of archives.
After this operation, 272 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 openjdk-17-jre-headless amd64 17.0.11+9-1~22.04.1 [48.2 MB]
Get:2 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 openjdk-17-jre amd64 17.0.11+9-1~22.04.1 [203 kB]                                                       
Get:3 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 openjdk-17-jdk-headless amd64 17.0.11+9-1~22.04.1 [71.1 MB]                                             
Get:4 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 openjdk-17-jdk amd64 17.0.11+9-1~22.04.1 [10.8 kB]                                                      
Fetched 120 MB in 60s (1,997 kB/s)                                                                                                                                             
Selecting previously unselected package openjdk-17-jre-headless:amd64.
(Reading database ... 221779 files and directories currently installed.)
Preparing to unpack .../openjdk-17-jre-headless_17.0.11+9-1~22.04.1_amd64.deb ...
Unpacking openjdk-17-jre-headless:amd64 (17.0.11+9-1~22.04.1) ...
Selecting previously unselected package openjdk-17-jre:amd64.
Preparing to unpack .../openjdk-17-jre_17.0.11+9-1~22.04.1_amd64.deb ...
Unpacking openjdk-17-jre:amd64 (17.0.11+9-1~22.04.1) ...
Selecting previously unselected package openjdk-17-jdk-headless:amd64.
Preparing to unpack .../openjdk-17-jdk-headless_17.0.11+9-1~22.04.1_amd64.deb ...
Unpacking openjdk-17-jdk-headless:amd64 (17.0.11+9-1~22.04.1) ...
Selecting previously unselected package openjdk-17-jdk:amd64.
Preparing to unpack .../openjdk-17-jdk_17.0.11+9-1~22.04.1_amd64.deb ...
Unpacking openjdk-17-jdk:amd64 (17.0.11+9-1~22.04.1) ...
Setting up openjdk-17-jre-headless:amd64 (17.0.11+9-1~22.04.1) ...
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/java to provide /usr/bin/java (java) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jpackage to provide /usr/bin/jpackage (jpackage) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode
Setting up openjdk-17-jre:amd64 (17.0.11+9-1~22.04.1) ...
Setting up openjdk-17-jdk-headless:amd64 (17.0.11+9-1~22.04.1) ...
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jar to provide /usr/bin/jar (jar) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/javac to provide /usr/bin/javac (javac) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/javap to provide /usr/bin/javap (javap) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jcmd to provide /usr/bin/jcmd (jcmd) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jdeprscan to provide /usr/bin/jdeprscan (jdeprscan) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jdeps to provide /usr/bin/jdeps (jdeps) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jfr to provide /usr/bin/jfr (jfr) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jimage to provide /usr/bin/jimage (jimage) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jlink to provide /usr/bin/jlink (jlink) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jmod to provide /usr/bin/jmod (jmod) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jps to provide /usr/bin/jps (jps) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jshell to provide /usr/bin/jshell (jshell) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jhsdb to provide /usr/bin/jhsdb (jhsdb) in auto mode
Setting up openjdk-17-jdk:amd64 (17.0.11+9-1~22.04.1) ...
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
nikhil@nikhil-HP-ZBook-15:~$ java -version
openjdk version "17.0.11" 2024-04-16
OpenJDK Runtime Environment (build 17.0.11+9-Ubuntu-122.04.1)
OpenJDK 64-Bit Server VM (build 17.0.11+9-Ubuntu-122.04.1, mixed mode, sharing)
nikhil@nikhil-HP-ZBook-15:~$ openjdk version "17.0.7" 2023-04-18
OpenJDK Runtime Environment (build 17.0.7+7-Ubuntu-0ubuntu120.04)
OpenJDK 64-Bit Server VM (build 17.0.7+7-Ubuntu-0ubuntu120.04, mixed mode, sharing)
Command 'openjdk' not found, but can be installed with:
sudo snap install openjdk
bash: syntax error near unexpected token `('
bash: syntax error near unexpected token `('
nikhil@nikhil-HP-ZBook-15:~$ sudo snap install openjdk
openjdk 22.0.1+8 from John Neffenger (jgneff) installed
nikhil@nikhil-HP-ZBook-15:~$ openjdk version "17.0.7" 2023-04-18
OpenJDK Runtime Environment (build 17.0.7+7-Ubuntu-0ubuntu120.04)
OpenJDK 64-Bit Server VM (build 17.0.7+7-Ubuntu-0ubuntu120.04, mixed mode, sharing)
/var/snap/openjdk/1764/openjdk.env
bash: syntax error near unexpected token `('
bash: syntax error near unexpected token `('
nikhil@nikhil-HP-ZBook-15:~$ sudo nano /etc/default/jenkins
nikhil@nikhil-HP-ZBook-15:~$ sudo systemctl daemon-reload
nikhil@nikhil-HP-ZBook-15:~$ sudo systemctl restart jenkins
nikhil@nikhil-HP-ZBook-15:~$ sudo systemctl status jenkins
● jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2024-07-09 23:19:30 IST; 7s ago
   Main PID: 15036 (java)
      Tasks: 59 (limit: 28273)
     Memory: 649.7M
        CPU: 26.174s
     CGroup: /system.slice/jenkins.service
             └─15036 /usr/bin/java -Djava.awt.headless=true -jar /usr/share/java/jenkins.war --webroot=/var/cache/jenkins/war --httpPort=8080

Jul 09 23:19:17 nikhil-HP-ZBook-15 jenkins[15036]: 9a8ee2483f4b4bcfbd85eacf2d23691d
Jul 09 23:19:17 nikhil-HP-ZBook-15 jenkins[15036]: This may also be found at: /var/lib/jenkins/secrets/initialAdminPassword
Jul 09 23:19:17 nikhil-HP-ZBook-15 jenkins[15036]: *************************************************************
Jul 09 23:19:17 nikhil-HP-ZBook-15 jenkins[15036]: *************************************************************
Jul 09 23:19:17 nikhil-HP-ZBook-15 jenkins[15036]: *************************************************************
Jul 09 23:19:25 nikhil-HP-ZBook-15 jenkins[15036]: 2024-07-09 17:49:25.675+0000 [id=63]        INFO        h.m.DownloadService$Downloadable#load: Obtained the updated data fil>
Jul 09 23:19:25 nikhil-HP-ZBook-15 jenkins[15036]: 2024-07-09 17:49:25.676+0000 [id=63]        INFO        hudson.util.Retrier#start: Performed the action check updates server>
Jul 09 23:19:30 nikhil-HP-ZBook-15 jenkins[15036]: 2024-07-09 17:49:30.579+0000 [id=37]        INFO        jenkins.InitReactorRunner$1#onAttained: Completed initialization
Jul 09 23:19:30 nikhil-HP-ZBook-15 jenkins[15036]: 2024-07-09 17:49:30.608+0000 [id=26]        INFO        hudson.lifecycle.Lifecycle#onReady: Jenkins is fully up and running
Jul 09 23:19:30 nikhil-HP-ZBook-15 systemd[1]: Started Jenkins Continuous Integration Server.
lines 1-20/20 (END)...skipping...
● jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2024-07-09 23:19:30 IST; 7s ago
   Main PID: 15036 (java)
      Tasks: 59 (limit: 28273)
     Memory: 649.7M
        CPU: 26.174s
     CGroup: /system.slice/jenkins.service
             └─15036 /usr/bin/java -Djava.awt.headless=true -jar /usr/share/java/jenkins.war --webroot=/var/cache/jenkins/war --httpPort=8080

Jul 09 23:19:17 nikhil-HP-ZBook-15 jenkins[15036]: 9a8ee2483f4b4bcfbd85eacf2d23691d
Jul 09 23:19:17 nikhil-HP-ZBook-15 jenkins[15036]: This may also be found at: /var/lib/jenkins/secrets/initialAdminPassword
Jul 09 23:19:17 nikhil-HP-ZBook-15 jenkins[15036]: *************************************************************
Jul 09 23:19:17 nikhil-HP-ZBook-15 jenkins[15036]: *************************************************************
Jul 09 23:19:17 nikhil-HP-ZBook-15 jenkins[15036]: *************************************************************
Jul 09 23:19:25 nikhil-HP-ZBook-15 jenkins[15036]: 2024-07-09 17:49:25.675+0000 [id=63]        INFO        h.m.DownloadService$Downloadable#load: Obtained the updated data fil>
Jul 09 23:19:25 nikhil-HP-ZBook-15 jenkins[15036]: 2024-07-09 17:49:25.676+0000 [id=63]        INFO        hudson.util.Retrier#start: Performed the action check updates server>
Jul 09 23:19:30 nikhil-HP-ZBook-15 jenkins[15036]: 2024-07-09 17:49:30.579+0000 [id=37]        INFO        jenkins.InitReactorRunner$1#onAttained: Completed initialization
Jul 09 23:19:30 nikhil-HP-ZBook-15 jenkins[15036]: 2024-07-09 17:49:30.608+0000 [id=26]        INFO        hudson.lifecycle.Lifecycle#onReady: Jenkins is fully up and running
Jul 09 23:19:30 nikhil-HP-ZBook-15 systemd[1]: Started Jenkins Continuous Integration Server.
```

* Today we have learned how to installed docker and jenkins and also learned
    
* how to troubledhoot if we are faced any issue reagrding installation and rectify the error code and resolve the issue with help of chatgpt and ubuntu comunities sites.
    

### Installing Docker and Jenkins Using Package Managers on Ubuntu and CentOS

#### Introduction

Installing software on Linux systems like Ubuntu and CentOS is made easy through package managers. Package managers automate the process of downloading, installing, and managing software packages, ensuring dependencies are handled efficiently.

#### Docker

**Ubuntu:**

* Docker can be installed on Ubuntu using the `apt` package manager.
    
* Ensure your package index is up to date with `sudo apt update`.
    
* Install Docker with `sudo apt install docker-ce`.
    
* Start and enable Docker services with `sudo systemctl start docker` and `sudo systemctl enable docker`.
    

**CentOS:**

* CentOS users install Docker via `yum`, a package manager for RPM-based distributions.
    
* Begin by updating your package list with `sudo yum update`.
    
* Add the Docker repository and install it using `sudo yum install docker-ce`.
    
* Start Docker with `sudo systemctl start docker` and enable it to start on boot with `sudo systemctl enable docker`.
    

#### Jenkins

**Ubuntu:**

* Jenkins can be installed on Ubuntu using the Jenkins Debian package.
    
* Import the Jenkins repository key and add the repository to your system.
    
* Update the package index with `sudo apt update`.
    
* Install Jenkins with `sudo apt install jenkins`.
    
* Start and enable Jenkins using `sudo systemctl start jenkins` and `sudo systemctl enable jenkins`.
    

**CentOS:**

* On CentOS, Jenkins is installed from the Jenkins repository using `yum`.
    
* Download the Jenkins repository configuration and import the GPG key.
    
* Install Jenkins with `sudo yum install jenkins`.
    
* Start Jenkins using `sudo systemctl start jenkins` and enable it with `sudo systemctl enable jenkins`.
    

### Understanding `systemctl` and `systemd`

#### What is `systemctl`?

`systemctl` is a command-line utility used to examine and control the state of `systemd`, which is a system and service manager for Unix-like operating systems. It allows administrators to manage services, view their status, start or stop them, enable or disable them to start at boot, and more.

#### What is `systemd`?

`systemd` is a replacement for the traditional SysVinit system initialization and service management daemon found in Unix-like operating systems. It provides a range of features:

* **Service Management:** Controls the startup and management of daemons and services.
    
* **Unit File Configuration:** Services, sockets, devices, mounts, and other system resources are managed through unit configuration files.
    
* **Logging:** Integrates with the journaling system (`systemd-journald`) for centralized logging.
    
* **Dependency Management:** Handles service dependencies and parallelization of service startup.
    
* **Security:** Implements various security and resource control features.
    

#### Key `systemctl` Commands:

* **Start a Service:** `sudo systemctl start servicename`
    
* **Stop a Service:** `sudo systemctl stop servicename`
    
* **Restart a Service:** `sudo systemctl restart servicename`
    
* **Enable a Service to Start on Boot:** `sudo systemctl enable servicename`
    
* **Disable a Service from Starting on Boot:** `sudo systemctl disable servicename`
    
* **Check Service Status:** `sudo systemctl status servicename`
    
* **Reload Service Configuration:** `sudo systemctl reload servicename`
    
* **View Service Logs:** `sudo journalctl -u servicename`
    

#### Benefits of `systemd`:

* **Improved Performance:** Faster boot times and parallelized startup of services.
    
* **Centralized Logging:** Facilitates easy access and management of system logs.
    
* **Dependency Management:** Ensures services start in the correct order based on dependencies.
    
* **Resource Control:** Provides better management of system resources like CPU, memory, and disk usage.
    

1. **Check Docker Service Status:**
    
    * Check the status of the Docker service on your system (ensure you have completed the installation tasks above).
        
2. ```bash
    sudo systemctl status docker
    ```
    
    * **Check Jenkins Service Status (Before):**
        
        Before stopping Jenkins, check its current status to ensure it's running:
        
        ```bash
        sudo systemctl status jenkins
        ```
        
        This command will display detailed information about the Jenkins service, including its current state, recent logs, and more.
        
    * **Verify Jenkins Service is Stopped (After):**
        
        After stopping Jenkins, verify its status again to ensure it has stopped successfully:
        
        ```bash
        sudo systemctl status jenkins
        ```
        
        **Read About Systemctl vs. Service:**
        
        * Read about the differences between the `systemctl` and `service` commands.
            
        * Example: `systemctl status docker` vs. `service docker status`.
            
    
    ### systemctl
    
    * **Usage:** `systemctl` is the primary command-line utility for controlling `systemd`, the system and service manager.
        
    * **Functionality:**
        
        * **Service Management:** Start, stop, restart, enable, disable services.
            
        * **View Service Status:** Check the current status of services.
            
        * **Manage Units:** Handle other systemd units like sockets, mounts, timers, etc.
            
        * **Logging:** Access and manage logs through `systemd-journald`.
            
    * **Example:**
        
        * Check Docker service status:
            
            ```bash
            sudo systemctl status docker
            ```
            
    
    ### service
    
    * **Usage:** `service` is a command-line script that wraps around `systemctl` and provides a simplified interface for managing services.
        
    * **Functionality:**
        
        * **Service Management:** Start, stop, restart, check status of services.
            
        * **Limited to SysVinit Scripts:** Typically used with traditional SysVinit scripts rather than systemd units.
            
        * **Compatibility:** Provides compatibility with older Linux distributions that haven't fully adopted systemd.
            
    * **Example:**
        
        * Check Docker service status:
            
            ```bash
            sudo service docker status
            ```
            
    
    ### Analyzing Docker Service Logs
    
    1. **View Docker Service Logs:**
        
        ```bash
        sudo journalctl -u docker.service
        ```
        
    
    ### Analyzing Jenkins Service Logs
    
    1. **View Jenkins Service Logs:**
        
        ```bash
        sudo journalctl -u jenkins.service
        ```
        
    
    #90daysofdevops