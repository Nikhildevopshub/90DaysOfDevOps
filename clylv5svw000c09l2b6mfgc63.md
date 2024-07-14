---
title: "Day 11 Task: Error Handling in Shell Scripting"
datePublished: Sun Jul 14 2024 18:02:53 GMT+0000 (Coordinated Universal Time)
cuid: clylv5svw000c09l2b6mfgc63
slug: day-11-task-error-handling-in-shell-scripting
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720980068889/8426add0-a752-41ec-8511-2eb2440bb176.webp
tags: devops, shell-scripting, devops-articles, devops-journey, 90daysofdevops

---

## Learning Objectives

Understanding how to handle errors in shell scripts is crucial for creating robust and reliable scripts. Today, you'll learn how to use various techniques to handle errors effectively in your bash scripts.

## Topics to Cover

1. **Understanding Exit Status**: Every command returns an exit status (0 for success and non-zero for failure). Learn how to check and use exit statuses.
    
2. **Using** `if` Statements for Error Checking: Learn how to use `if` statements to handle errors.
    
3. **Using** `trap` for Cleanup: Understand how to use the `trap` command to handle unexpected errors and perform cleanup.
    
4. **Redirecting Errors**: Learn how to redirect errors to a file or `/dev/null`.
    
5. **Creating Custom Error Messages**: Understand how to create meaningful error messages for debugging and user information.
    

## Tasks with Answers

### Task 1: Checking Exit Status

* Write a script that attempts to create a directory and checks if the command was successful. If not, print an error message.
    
* ```bash
    #!/bin/bash
    mkdir my_directory
    if [ $? -ne 0 ];0 ]; then
      echo "Error: Failed to create directory 'my_directory'."
    fi
    ```
    
    ### Task 2: Using `if` Statements for Error Checking
    
    Modify the script from Task 1 to include more commands (e.g., creating a file inside the directory) and use `if` statements to handle errors at each step.
    
    ```bash
    #!/bin/bash
    mkdir my_directory
    if [ $? -ne 0 ]; then
      echo "Error: Failed to create directory 'my_directory'."
      exit 1
    fi
    
    touch my_directory/my_file.txt
    if [ $? -ne 0 ]; then
      echo "Error: Failed to create file 'my_file.txt' in 'my_directory'."
      exit 1
    fi
    
    echo "Directory and file created successfully."
    ```
    
    ### Task 3: Using `trap` for Cleanup
    
    Write a script that creates a temporary file and sets a trap to delete the file if the script exits unexpectedly.
    
    ```bash
    #!/bin/bash
    temp_file=$(mktemp)
    trap "rm -f $temp_file" EXIT
    
    echo "Temporary file created: $temp_file"
    
    # Simulate some work
    sleep 5
    
    echo "Script completed. Temporary file will be deleted."
    ```
    
    ### Task 4: Redirecting Errors
    
    Write a script that tries to read a non-existent file and redirects the error message to a file called `error.log`.
    
    ```bash
    #!/bin/bash
    
    cat non_existent_file 2>error.log
    ```
    
    ### Task 5: Creating Custom Error Messages
    
    Modify one of the previous scripts to include custom error messages that provide more context about what went wrong.
    
    ```bash
    #!/bin/bash
    mkdir my_directory
    if [ $? -ne 0 ]; then
      echo "Error: Failed to create directory 'my_directory'. Ensure you have the necessary permissions and that the directory doesn't already exist."
      exit 1
    fi
    
    touch my_directory/my_file.txt
    if [ $? -ne 0 ]; then
      echo "Error: Failed to create file 'my_file.txt' in 'my_directory'. Ensure you have the necessary permissions."
      exit 1
    fi
    
    echo "Directory and file created successfully."
    ```