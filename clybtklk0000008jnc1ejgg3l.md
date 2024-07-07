---
title: "Day 5 Task: Advanced Linux Shell Scripting for DevOps Engineers with User Management"
datePublished: Sun Jul 07 2024 17:20:43 GMT+0000 (Coordinated Universal Time)
cuid: clybtklk0000008jnc1ejgg3l
slug: day-5-task-advanced-linux-shell-scripting-for-devops-engineers-with-user-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720368302427/fe54dcc1-d8e5-47b5-9274-3d9d5ef25097.jpeg
tags: bash, devops, 90daysofdevops, devopsculture

---

**Create Directories Using Shell Script:**

* Example : When executed as `./`[`createDirectories.sh`](http://createDirectories.sh) `day 1 90`, it creates 90 directories as `day1 day2 day3 ... day90`.
    
* ```bash
    #!/bin/bash
    
    for ((i=1; i<=90; i++ ));
    do
            dirname="day$i"
            mkdir "$dirname"
            echo "created directory : $dirname"
    done  
    ```
    
    **Create a Script to Backup All Your Work:**
    
    * Backups are an important part of a DevOps Engineer's day-to-day activities. The video in the references will help you understand how a DevOps Engineer takes backups
        
    * ```bash
        #!/bin/bash
        
        backup_dir="/path/to/backup"
        source_dir="/path/to/source"
        
        # Create a compressed backup file with timestamp
        tar -czf "$backup_dir/backup_$(date +%Y%m%d_%H%M%S).tar.gz" "$source_dir"
        
        echo "The backup is completed successfully"
        ```
        
        * `#!/bin/bash`: Shebang line that specifies the script should be interpreted by Bash.
            
        * `backup_dir="/path/to/backup"`: Variable that holds the path to the backup directory.
            
        * `source_dir="/path/to/source"`: Variable that holds the path to the source directory to be backed up.
            
        * `tar -czf "$backup_dir/backup_$(date +%Y%m%d_%H%M%S).tar.gz" "$source_dir"`: Creates a compressed archive (`tar.gz`) named with a timestamp (`$(date +%Y%m%d_%H%M%S)`) inside the specified backup directory (`$backup_dir`), containing the contents of the source directory (`$source_dir`).
            
        * `echo "The backup is completed successfully"`: Prints a message indicating the backup process is complete.
            
        
        3. **Cron and Crontab to Automate the Backup Script:**
            
        
        A `crontab` (Cron table) in shell scripting is a configuration file used to schedule and automate tasks (Cron jobs) to run at specified times or intervals.
        
        ```bash
        * * * * * command_to_execute
        - - - - -
        | | | | |
        | | | | +----- day of week (0 - 7) (Sunday=0 or 7)
        | | | +------- month (1 - 12)
        | | +--------- day of month (1 - 31)
        | +----------- hour (0 - 23)
        +------------- minute (0 - 59)
        ```
        
        ```bash
        crontab -e
        0 5  * /path/to/backup.sh 
        ```
        
        Above code is defined in way that it will run 5 AM every day every month and every week.
        
        ```bash
        0: At minute 0
        5: At hour 5 AM
        *: Every day of the month
        *: Every month
        *: Every day of the week
        ```
        
        4. **User Management:**
            
        
        In Linux, users are accounts used for tasks, each identified by a unique User ID (UID). System users have <mark>IDs from 0 to 999, while regular users start from 1000.</mark> Users are created with `useradd`, and their details, including usernames, can be checked in cat `/etc/passwd` or using the `id` command.
        
    

#90daysofdevops