---
title: "Day 4 Task: Basic Linux Shell Scripting for DevOps Engineers"
datePublished: Sat Jul 06 2024 14:00:06 GMT+0000 (Coordinated Universal Time)
cuid: clya6yqwa000008mjf0d653ws
slug: day-4-task-basic-linux-shell-scripting-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720270898189/0f339852-e626-49a8-8418-f1a5fbf75ac9.jpeg
tags: devops, shell-scripting, linux-for-beginners, 90daysofdevops, 90daysofdevops-chanllenge

---

## What is Kernel?

* **What it is:** The core part of an operating system.
    
* **What it does:** Manages hardware and software communication.
    
* **Analogy:** Like a factory manager, ensuring machines and workers work together.
    

## What is Shell?

* **What it is:** A program that lets you interact with the operating system.
    
* **What it does:** Translates your commands into actions.
    
* **Analogy:** Like a translator between you and the factory manager (kernel).
    

## What is Linux Shell Scripting?

* **What it is:** Writing a series of commands for the shell to execute.
    
* **What it does:** Automates tasks and manages system operations.
    
* **Analogy:** Like writing a set of instructions for the translator (shell) to perform tasks automatically.
    

### What is `#!/bin/bash` and `#!/bin/sh`?

The line `#!/bin/bash` or `#!/bin/sh` at the beginning of a script is called a shebang. It tells the system which interpreter to use to run the script:

* `#!/bin/bash` uses the Bash shell, which is more feature-rich.
    
* `#!/bin/sh` uses the default shell, which might be more basic.
    

### Shell Script Examples

**1.Write a Shell Script that prints** `I will complete #90DaysOfDevOps`**.**

```bash
nikhil@nikhil-HP-ZBook-15:~$ touch devops.sh
nikhil@nikhil-HP-ZBook-15:~$ vim devops.sh
#!/bin/bash
echo "I will complete  #90daysofdevops"
nikhil@nikhil-HP-ZBook-15:~$ sh devops.sh
I will complete  #90daysofdevops
```

This script simply prints "I willl complete #90daysofdevops" to the terminal.

**2\. Write a Shell Script that takes user input, input from arguments, and prints the variables.**

```bash
nikhil@nikhil-HP-ZBook-15:~$ vim script.sh 

#!/bin/bash

read -p "Enter ist number = " a
read -p "Enter 2nd number = " b

sum=$(($a + $b))
echo "Answer = $sum"
```

```bash
nikhil@nikhil-HP-ZBook-15:~$ sh script.sh 
Enter ist number = 435
Enter 2nd number = 64654
Answer = 65089
```

#### 3. **Example of an If-Else Statement in Shell Scripting**

If-else statements allow conditional execution of commands based on certain conditions.

**Example Script:**

```bash
nikhil@nikhil-HP-ZBook-15:~$ vim devop.sh

#!/bin/bash
num1=10
num2=20

if [ $num1 -gt $num2 ]
then
  echo "$num1 is greater than $num2"
else
  echo "$num1 is not greater than $num2"
fi


nikhil@nikhil-HP-ZBook-15:~$ sh devop.sh
10 is not greater than 20

```

This script compares two numbers and prints a message based on the comparison.

#90daysofdevops