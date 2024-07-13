---
title: "Day 10 Answers: Log Analyzer and Report Generator"
datePublished: Sat Jul 13 2024 17:39:32 GMT+0000 (Coordinated Universal Time)
cuid: clykevx6z000l0amihtlt8riz
slug: day-10-answers-log-analyzer-and-report-generator
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720892313201/ae8bd6bb-efb6-4e21-849b-002af91d8315.png
tags: devops, shell-script, devops-articles, 90daysofdevops, trainwithshubham

---

## Scenario

You are a system administrator responsible for managing a network of servers. Every day, a log file is generated on each server containing important system events and error messages. As part of your daily tasks, you need to analyze these log files, identify specific events, and generate a summary report.

## Task

Write a Bash script that automates the process of analyzing log files and generating a daily summary report. The script should perform the following steps:

1. **Input:** The script should take the path to the log file as a command-line argument.
    
2. **Error Count:** Analyze the log file and count the number of error messages. An error message can be identified by a specific keyword (e.g., "ERROR" or "Failed"). Print the total error count.
    
3. **Critical Events:** Search for lines containing the keyword "CRITICAL" and print those lines along with the line number.
    
4. **Top Error Messages:** Identify the top 5 most common error messages and display them along with their occurrence count.
    
5. **Summary Report:** Generate a summary report in a separate text file. The report should include:
    
    * Date of analysis
        
    * Log file name
        
    * Total lines processed
        
    * Total error count
        
    * Top 5 error messages with their occurrence count
        
    * List of critical events with line numbers
        
    
    ### **ANSWER**
    
6. ### Step-by-Step Explanation
    
    #### 1\. Script Header
    
    ```bash
    #!/bin/bash
    ```
    
    * This line indicates that the script should be run using the Bash shell.
        
    
    #### 2\. Function to Display Usage Information
    
    ```bash
    usage() {
            echo "Usage: $0 /path/to/logfile"
            exit 1
    }
    ```
    
    * **Function** `usage`: This function prints how to use the script and then exits.
        
    * `$0`: Represents the name of the script.
        
    * `exit 1`: Stops the script with a status code of 1, indicating an error.
        
    
    #### 3\. Checking the Number of Arguments
    
    ```bash
    if [ $# -ne 1 ]; then
            usage
    fi
    ```
    
    * `if [ $# -ne 1 ]`: Checks if the number of arguments (`$#`) is not equal to (`-ne`) 1.
        
    * `usage`: Calls the `usage` function to show how to use the script.
        
    
    #### 4\. Assigning the Log File Argument to a Variable
    
    ```bash
    log_file=$1
    ```
    
    * `log_file=$1`: Assigns the first argument passed to the script to the variable `log_file`.
        
    
    #### 5\. Checking if the Log File Exists
    
    ```bash
    if [ ! -f "$log_file" ]; then
            echo "Error: log file $log_file does not exist."
            exit 1
    fi
    ```
    
    * `if [ ! -f "$log_file" ]`: Checks if the file (`-f`) does not (`!`) exist.
        
    * `echo`: Prints an error message.
        
    * `exit 1`: Stops the script with an error status code.
        
    
    #### 6\. Defining Variables
    
    ```bash
    error_keyword="ERROR"
    critical_keyword="CRITICAL"
    date=$(date +"%Y-%m-%d")
    summary_report="summary_report_$date.txt"
    archive_dir="processed_logs"
    total_lines=$(wc -l < "$log_file")
    ```
    
    * `error_keyword="ERROR"`: Defines the keyword to search for errors.
        
    * `critical_keyword="CRITICAL"`: Defines the keyword to search for critical events.
        
    * `date=$(date +"%Y-%m-%d")`: Gets the current date in `YYYY-MM-DD` format.
        
    * `summary_report="summary_report_$date.txt"`: Defines the name of the summary report file.
        
    * `archive_dir="processed_logs"`: Defines the directory to archive processed logs.
        
    * `total_lines=$(wc -l < "$log_file")`: Counts the total number of lines in the log file.
        
    
    #### 7\. Creating the Archive Directory if It Does Not Exist
    
    ```bash
    mkdir -p "$archive_dir"
    ```
    
    * `mkdir -p "$archive_dir"`: Creates the directory `archive_dir` if it does not already exist.
        
    
    #### 8\. Creating the Summary Report
    
    ```bash
    {
            echo "Date of analysis: $date"
            echo "Log file name: $log_file"
            echo "Total lines in the log file: $total_lines"
    } > "$summary_report"
    ```
    
    * `{ ... } > "$summary_report"`: Collects multiple lines of output and writes them to `summary_report`.
        
    * `echo`: Prints text to the summary report.
        
    
    #### 9\. Counting Total Errors
    
    ```bash
    error_count=$(grep -c "$error_keyword" "$log_file")
    echo "Total error count: $error_count" >> "$summary_report"
    ```
    
    * `error_count=$(grep -c "$error_keyword" "$log_file")`: Counts the number of lines containing the error keyword.
        
    * `echo ... >> "$summary_report"`: Appends the error count to the summary report.
        
    
    #### 10\. Listing Critical Events with Line Numbers
    
    ```bash
    critical_events=$(grep -n "$critical_keyword" "$log_file")
    if [ -z "$critical_events" ]; then
            echo "No critical events found." >> "$summary_report"
    else
            echo "List of critical events with line number:" >> "$summary_report"
            echo "$critical_events" >> "$summary_report"
    fi
    ```
    
    * `critical_events=$(grep -n "$critical_keyword" "$log_file")`: Finds lines containing the critical keyword and their line numbers.
        
    * `if [ -z "$critical_events" ]`: Checks if `critical_events` is empty.
        
    * `echo ... >> "$summary_report"`: Appends messages to the summary report.
        
    
    #### 11\. Finding and Listing Top 5 Error Messages
    
    ```bash
    top_five=$(grep -i "$error_keyword" "$log_file" | awk '{print $1,$2,$3,$4,$5}' | sort | uniq -c | sort -nr | head -n 5)
    if [ -z "$top_five" ]; then
            echo "No error messages found." >> "$summary_report"
    else
            echo "Top 5 error messages with their occurrence count:" >> "$summary_report"
            echo "$top_five" >> "$summary_report"
    fi
    ```
    
    * `top_five=$(grep -i "$error_keyword" "$log_file" | awk '{print $1,$2,$3,$4,$5}' | sort | uniq -c | sort -nr | head -n 5)`:
        
        * `grep -i "$error_keyword" "$log_file"`: Finds lines with the error keyword, case insensitive.
            
        * `awk '{print $1,$2,$3,$4,$5}'`: Prints the first five fields of each line.
            
        * `sort | uniq -c`: Sorts lines and counts unique occurrences.
            
        * `sort -nr`: Sorts the counts in descending order.
            
        * `head -n 5`: Gets the top 5 lines.
            
    * `if [ -z "$top_five" ]`: Checks if `top_five` is empty.
        
    * `echo ... >> "$summary_report"`: Appends messages to the summary report.
        
    
    #### 12\. Moving Processed Log to Archive Directory
    
    ```bash
    mv "$log_file" "$archive_dir/"
    echo "Summary report created: $summary_report"
    echo "Log file moved to archive directory: $archive_dir/"
    ```
    
    * `mv "$log_file" "$archive_dir/"`: Moves the log file to the archive directory.
        
    * `echo`: Prints messages indicating the creation of the summary report and the archiving of the log file.
        
    
    ### Final Output
    
    * The script produces a summary report named `summary_report_YYYY-MM-DD.txt` (with the current date) containing:
        
        * Date of analysis
            
        * Log file name
            
        * Total lines in the log file
            
        * Total error count
            
        * List of critical events with line numbers (if any)
            
        * Top 5 error messages with their occurrence count (if any)
            
    * The log file is moved to the `processed_logs` directory.