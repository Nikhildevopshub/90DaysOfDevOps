---
title: "Day 9 Task: Shell Scripting Challenge Directory Backup with Rotation"
datePublished: Fri Jul 12 2024 15:03:16 GMT+0000 (Coordinated Universal Time)
cuid: clyitv3td00040ajpb60kc6j2
slug: day-9-task-shell-scripting-challenge-directory-backup-with-rotation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720796506898/5517a816-1394-4893-8401-74ead1f08868.avif
tags: devops, devops-articles, devops-journey, 90daysofdevops, learninpublic

---

Your task is to create a bash script that takes a directory path as a command-line argument and performs a backup of the directory. The script should create timestamped backup folders and copy all the files from the specified directory into the backup folder.

Additionally, the script should implement a rotation mechanism to keep only the last 3 backups. This means that if there are more than 3 backup folders, the oldest backup folders should be removed to ensure only the most recent backups are retained.

### **The Script**

Below is the Bash script named `backup_with_`[`rotation.sh`](http://rotation.sh) [that imp](http://rotation.sh/)l[ements the](http://rotation.sh/) described functionality:

```bash
#!/bin/bash

<<readme
This script takes backup of a directory with timestamped folders and implements rotation.
Usage:
./backup_with_rotation.sh <path of directory>
readme

# Ensure correct number of arguments
if [ $# -ne 1 ]; then
    echo "Usage: $0 <path of directory>"
    exit 1
fi

source_dir="$1"
target_dir="${source_dir}"

# Create target directory if it does not exist
if [ ! -d "$target_dir" ]; then
    mkdir -p "$target_dir"
fi

timestamp=$(date '+%Y-%m-%d_%H-%M-%S')

backup_dir="${target_dir}/backup_${timestamp}"

function create_backup {
    # Create the backup
    zip -r "${backup_dir}.zip" "${source_dir}" > /dev/null

    if [ $? -eq 0 ]; then
        echo "Backup created: ${backup_dir}.zip"
    else
        echo "Backup was not performed for $timestamp"
    fi
}

function perform_rotation {
    # List backups, sorted by modification time, newest first
    backups=($(ls -t "${target_dir}/backup_"*.zip))

    if [ "${#backups[@]}" -gt 3 ]; then
        backups_to_remove=("${backups[@]:3}")
        for backup in "${backups_to_remove[@]}"; do
            rm -f -- "$backup"
            if [ $? -eq 0 ]; then
                echo "Removed old backup: $backup"
            else
                echo "Failed to remove old backup: $backup"
            fi
        done
    fi
}

create_backup
perform_rotation
```

### Step-by-Step Explanation of the Script

```bash
#!/bin/bash

# Ensure the correct number of arguments is provided
if [ $# -ne 1 ]; then
    echo "Usage: $0 <path of directory>"
    exit 1
fi
```

* **Shebang (**`#!/bin/bash`): Specifies that this script should be interpreted and executed using Bash.
    
* **Argument Checking (**`if [ $# -ne 1 ]; then ... fi`):
    
    * `$#` represents the number of arguments passed to the script.
        
    * `-ne 1` checks if the number of arguments is not equal to 1.
        
    * If the condition is true (i.e., if the number of arguments is not exactly 1), it prints a usage message (`Usage: $0 <path of directory>`) and exits the script with status code 1.
        

```bash
source_dir="$1"
target_dir="${source_dir}"
```

* **Assigning Variables**:
    
    * `source_dir="$1"`: Assigns the first command-line argument (directory path) to the variable `source_dir`.
        
    * `target_dir="${source_dir}"`: Sets `target_dir` to the same value as `source_dir`. In this script, `target_dir` is intended to be the same as `source_dir` for simplicity.
        

```bash
if [ ! -d "$target_dir" ]; then
    mkdir -p "$target_dir"
fi
```

* **Creating Target Directory**:
    
    * Checks if the `target_dir` does not exist (`! -d "$target_dir"`).
        
    * If it doesn't exist, creates it using `mkdir -p "$target_dir"`. The `-p` flag ensures that intermediate directories are created as needed.
        

```bash
timestamp=$(date '+%Y-%m-%d_%H-%M-%S')
```

* **Generating Timestamp**:
    
    * `timestamp=$(date '+%Y-%m-%d_%H-%M-%S')`: Uses the `date` command to generate a timestamp in the format `YYYY-MM-DD_HH-MM-SS` and assigns it to the variable `timestamp`.
        

```bash
backup_dir="${target_dir}/backup_${timestamp}"
```

* **Defining Backup Directory**:
    
    * `backup_dir="${target_dir}/backup_${timestamp}"`: Constructs the name of the backup directory using the `target_dir` and `timestamp`. This will result in a directory path like `/path/to/directory/backup_YYYY-MM-DD_HH-MM-SS`.
        

```bash
function create_backup {
    zip -r "${backup_dir}.zip" "${source_dir}" > /dev/null

    if [ $? -eq 0 ]; then
        echo "Backup created: ${backup_dir}.zip"
    else
        echo "Backup was not performed for $timestamp"
    fi
}
```

* **Creating Backup Function** (`create_backup`):
    
    * `zip -r "${backup_dir}.zip" "${source_dir}" > /dev/null`: Creates a zip archive (`${backup_dir}.zip`) of the `source_dir`. The `-r` flag recursively includes all subdirectories and files.
        
    * `> /dev/null` redirects the output of `zip` command to `/dev/null`, suppressing unnecessary output.
        
    * `if [ $? -eq 0 ]; then ... fi`: Checks the exit status (`$?`) of the previous command (`zip`). If it's `0`, the backup creation was successful, and it prints a success message. Otherwise, it prints a failure message.
        

```bash
function perform_rotation {
    backups=($(ls -t "${target_dir}/backup_"*.zip))

    if [ "${#backups[@]}" -gt 3 ]; then
        backups_to_remove=("${backups[@]:3}")
        for backup in "${backups_to_remove[@]}"; do
            rm -f -- "$backup"
            if [ $? -eq 0 ]; then
                echo "Removed old backup: $backup"
            else
                echo "Failed to remove old backup: $backup"
            fi
        done
    fi
}
```

* **Backup Rotation Function** (`perform_rotation`):
    
    * `backups=($(ls -t "${target_dir}/backup_"*.zip))`: Lists all backup zip files (`backup_*.zip`) in `target_dir`, sorted by modification time (`-t` flag, newest first).
        
    * `${#backups[@]}` gives the number of elements (backups).
        
    * `if [ "${#backups[@]}" -gt 3 ]; then ... fi`: Checks if there are more than three backups.
        
    * `backups_to_remove=("${backups[@]:3}")`: Creates an array `backups_to_remove` containing all backups except the three newest ones (`"${backups[@]:3}"` selects elements starting from index 3).
        
    * `for backup in "${backups_to_remove[@]}"; do ... done`: Iterates over `backups_to_remove` array and removes each old backup file using `rm -f -- "$backup"`.
        
    * `if [ $? -eq 0 ]; then ... fi`: Checks if the removal was successful. If so, it prints a success message; otherwise, it prints a failure message.
        

### Running the Script

To run the script:

1. Save the script to a file (e.g., [`backup.sh`](http://backup.sh)).
    
2. Make the script executable: `chmod +x` [`backup.sh`](http://backup.sh).
    
3. Execute the script with the directory path as an argument:
    
    ```bash
    ./backup.sh /path/to/directory
    ```
    

Replace `/path/to/directory` with the actual directory path you want to backup.

#90daysofdevops