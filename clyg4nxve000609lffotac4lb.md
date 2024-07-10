---
title: "Day 8 Task: Shell Scripting Challenge"
datePublished: Wed Jul 10 2024 17:42:19 GMT+0000 (Coordinated Universal Time)
cuid: clyg4nxve000609lffotac4lb
slug: day-8-task-shell-scripting-challenge
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720630808172/bab08541-10af-4d16-a58a-c2742febf539.jpeg
tags: devops, devops-articles, devops-journey, 90daysofdevops, 90daysofdevopschallenge

---

### Task 1: Comments

In bash scripts, comments are used to add explanatory notes or disable certain lines of code. Your task is to create a bash script with comments explaining what the script does.

```bash
nikhil@nikhil-HP-ZBook-15:~/swap$ vim hello.sh
nikhil@nikhil-HP-ZBook-15:~/swap$ ./hello.sh 
hello welcome to shell scipting challenege
nikhil@nikhil-HP-ZBook-15:~/swap$ cat hello.sh 
#!/bin/bash
# this is comment 
echo "hello welcome to shell scipting challenege" #this print on the terminal 
```

### Task 2: Echo

The echo command is used to display messages on the terminal. Your task is to create a bash script that uses echo to print a message of your choice.

```bash
#!/bin/bash
# This script prints a message to the terminal

echo "Hello, World!"
```

### Task 3: Variables

Variables in bash are used to store data and can be referenced by their name. Your task is to create a bash script that declares variables and assigns values to them

```bash
#!/bin/bash
# This script declares variables and assigns values to them
name="Alice"
age=30
# Print the values of the variables
echo "Name: $name"
echo "Age: $age"

nikhil@nikhil-HP-ZBook-15:~/swap$ ./hello.sh 
Name: Alice
Age : 30
```

### Task 4: Using Variables

Now that you have declared variables, let's use them to perform a simple task. Create a bash script that takes two variables (numbers) as input and prints their sum using those variables.

```bash
#!/bin/bash
# This script takes two variables (numbers) as input and prints their sum
# Declare variables and assign values
num1=10
num2=20
# Calculate the sum
sum=$((num1 + num2))
# Print the sum
echo "The sum of $num1 and $num2 is $sum"

nikhil@nikhil-HP-ZBook-15:~/swap$ ./hello.sh 
The sum of 10 and 20 is 30
```

### Task 5: Using Built-in Variables

Bash provides several built-in variables that hold useful information. Your task is to create a bash script that utilizes at least three different built-in variables to display relevant information.

```bash
#!/bin/bash
# This script uses built-in variables to display relevant information

# Display the name of the script
echo "Script Name: $0"
# Display the number of arguments passed to the script
echo "Number of Arguments: $#"
# Display the current process ID
echo "Current Process ID: $$

nikhil@nikhil-HP-ZBook-15:~/swap$ ./hello.sh 
Script Name: ./hello.sh
Number of Arguments: 0
Current Process ID: 8701
```

### Task 6: Wildcards

Wildcards are special characters used to perform pattern matching when working with files. Your task is to create a bash script that utilizes wildcards to list all the files with a specific extension in a directory.

```bash
#!/bin/bash
# This script lists all the files with a specific extension in a directory

# Define the directory and file extension
directory="/path/to/directory"
extension="txt"
# List all files with the specified extension
echo "Listing all .$extension files in $directory:"
ls $directory/*.$extension

nikhil@nikhil-HP-ZBook-15:~$ ./script.sh 
Listing all .txt files in /home/nikhil/swap:
/home/nikhil/swap/filename.txt
```

#90daysofdevops