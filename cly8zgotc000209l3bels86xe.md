---
title: "Day 3 Task: Basic Linux Commands with a Twist  #90daysofdevops"
datePublished: Fri Jul 05 2024 17:42:20 GMT+0000 (Coordinated Universal Time)
cuid: cly8zgotc000209l3bels86xe
slug: day-3-task-basic-linux-commands-with-a-twist-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720193784957/d27df731-ec46-459e-8d11-19ee2dd8a230.jpeg
tags: ubuntu, devops, linux-for-beginners, devops-articles, 90daysofdevops

---

1. View the content of a file and display line numbers.
    
    ```bash
    nikhil@nikhil-HP-ZBook-15:~$ cat -n devops.txt
         1	hy I am in devops world
         2	I want to become a devops engineer
         3	as of now I am learning devops culture
    ```
    
    `cat -n filename` shows the content of `filename` with each line numbered.
    
2. ### 2\. Change the access permissions of files to make them readable, writable, and executable by the owner only.
    
    ```bash
    ls -l
    -rw-rw-r--  1 nikhil nikhil   101 Jul  5 21:02  devops.txt
    sudo chmod 700 devops.txt
    ls -l
    -rwx------  1 nikhil nikhil   101 Jul  5 21:02  devops.txt
    ```
    
    * `chmod 700 filename` sets the file permissions so that only the owner can read, write, and execute the file.
        
    
    ### 3\. Check the last 10 commands you have run.
    
    ```bash
    nikhil@nikhil-HP-ZBook-15:~$ history | tail -10
      271  ls
      272  ls-l
      273  ls -l
      274  sudo chmod 700 devops.txt
      275  ls -l
      276  history
      277  touch nikhil.txt
      278  sudo apt-get update
      279  tail -10
      280  history | tail -10
    ```
    
    * `history | tail -10` shows the last 10 commands you executed.
        
    
    ### 4\. Remove a directory and all its contents.
    
    ```bash
    nikhil@nikhil-HP-ZBook-15:~$ ls
     Desktop  'Devops folder'   Documents   git               nikhil.txt   Public   Templates
     devops    devops.txt       Downloads  'MEGA downloads'   Pictures     snap     Videos
    nikhil@nikhil-HP-ZBook-15:~$ cd devops
    nikhil@nikhil-HP-ZBook-15:~/devops$ ls
    file1.txt
    nikhil@nikhil-HP-ZBook-15:~/devops$ vim file1.txt 
    nikhil@nikhil-HP-ZBook-15:~/devops$ ls
    file1.txt
    nikhil@nikhil-HP-ZBook-15:~/devops$ cat file1.txt 
    hey dosto
    My name is filename
    nikhil@nikhil-HP-ZBook-15:~/devops$ cd ..
    nikhil@nikhil-HP-ZBook-15:~$ ls
     Desktop  'Devops folder'   Documents   git               nikhil.txt   Public   Templates
     devops    devops.txt       Downloads  'MEGA downloads'   Pictures     snap     Videos
    nikhil@nikhil-HP-ZBook-15:~$ rm devops
    rm: cannot remove 'devops': Is a directory
    nikhil@nikhil-HP-ZBook-15:~$ rmdir devops/
    rmdir: failed to remove 'devops/': Directory not empty
    nikhil@nikhil-HP-ZBook-15:~$ rm -r devops
    nikhil@nikhil-HP-ZBook-15:~$ ls
     Desktop          devops.txt   Downloads  'MEGA downloads'   Pictures   snap        Videos
    'Devops folder'   Documents    git         nikhil.txt        Public     Templates
    ```
    
    * `rm -r directoryname` deletes `directoryname` and all its contents.
        
    
    ### 5\. Create a fruits.txt file, add content (one fruit per line), and display the content.
    
    ```bash
    nikhil@nikhil-HP-ZBook-15:~$ touch fruits.txt
    nikhil@nikhil-HP-ZBook-15:~$ vim fruits.txt 
    nikhil@nikhil-HP-ZBook-15:~$ cat fruits.txt 
    apple
    bannana
    oranges
    grapes
    kiwi
    blueberry
    mango
    watermelon
    avocada
    strawberry
    ```
    
    * creates `fruits.txt` with each fruit on a new line.
        
    * `cat fruits.txt` displays the content of `fruits.txt`.
        
    
    ### 6\. Add content in devops.txt (one in each line) - Apple, Mango, Banana, Cherry, Kiwi, Orange, Guava. Then, append "Pineapple" to the end of the file.
    
    ```bash
    nikhil@nikhil-HP-ZBook-15:~$ vim devops.txt 
    nikhil@nikhil-HP-ZBook-15:~$ cat devops.txt 
    Apple
    mango
    banana
    cherry
    kiwi
    orange
    guava
    pineapple 
    ```
    
    * `devops.txt` appends "Pineapple" to the end of `devops.txt`.
        
    
    ### 7\. Show the first three fruits from the file in reverse order.
    
    ```bash
    nikhil@nikhil-HP-ZBook-15:~$ head -n 3 devops.txt | tac
    banana
    mango
    Apple
    ```
    
    * `head -n 3 devops.txt` gets the first three lines from `devops.txt`.
        
    * `tac` reverses the order of these lines.
        
    
    ### 8\. Show the bottom three fruits from the file, and then sort them alphabetically.
    
    ```bash
    nikhil@nikhil-HP-ZBook-15:~$ tail -3 devops.txt | sort
    guava
    orange
    pineapple 
    ```
    
    * `tail -3 devops.txt` gets the last three lines from `devops.txt`.
        
    * `sort` arranges them in alphabetical order.
        
    
    ### 9\. Create another file Colors.txt, add content (one color per line), and display the content.
    
    ```bash
    nikhil@nikhil-HP-ZBook-15:~$ touch colors.txt
    nikhil@nikhil-HP-ZBook-15:~$ vim colors.txt 
    nikhil@nikhil-HP-ZBook-15:~$ cat colors.txt 
    red
    pink
    white
    black
    orange
    puprle
    grey
    ```
    
    * creates `Colors.txt` with each color on a new line.
        
    * `cat Colors.txt` displays the content of `Colors.txt`.
        
    
    ### 10\. Add content in Colors.txt (one in each line) - Red, Pink, White, Black, Blue, Orange, Purple, Grey. Then, prepend "Yellow" to the beginning of the file.
    
    ```bash
    nikhil@nikhil-HP-ZBook-15:~$ vim colors.txt 
    nikhil@nikhil-HP-ZBook-15:~$ cat colors.txt 
    yellow
    red
    pink
    white
    black
    orange
    puprle
    grey
    ```
    
    * adds "Yellow" to the beginning of `Colors.txt`
        
    
    ### 11\. Find and display the lines that are common between fruits.txt and Colors.txt.
    
    ```bash
    nikhil@nikhil-HP-ZBook-15:~$ comm -12 <(sort fruits.txt) <(sort Colors.txt)
    sort: cannot read: Colors.txt: No such file or directory
    ```
    
    * ### Command Breakdown
        
        1. `comm`: This command is used to compare two sorted files line by line.
            
        2. `-12`: These are options for the `comm` command.
            
            * `-1` suppresses lines unique to the first file.
                
            * `-2` suppresses lines unique to the second file.
                
            * Combining them (`-12`) suppresses both unique lines, leaving only the lines common to both files.
                
        3. `<(sort fruits.txt)` and `<(sort Colors.txt)`: These are process substitutions.
            
            * `sort fruits.txt` sorts the contents of `fruits.txt`.
                
            * `sort Colors.txt` sorts the contents of `Colors.txt`.
                
            * `<()` passes the output of a command as a file input to another command.
                
        
    
    ### 12\. Count the number of lines, words, and characters in both fruits.txt and Colors.txt.
    
    ```bash
    oot@nikhil-HP-ZBook-15:/home/nikhil# wc colors.txt fruits.txt
      9   8  48 colors.txt
     11  10  81 fruits.txt
     20  18 129 total
    ```
    
    * `wc fruits.txt Colors.txt` displays the line, word, and character counts for both `fruits.txt` and `Colors.txt`.
        
    * ### Command Breakdown
        
        1. `wc`: This stands for "word count." It's a command-line utility that prints the number of lines, words, and characters in a file.
            
        2. `fruits.txt` and `Colors.txt`: These are the files we want to analyze with `wc`.
            
        
        When you run `wc` with multiple files, it outputs the counts for each file individually and then a total summary at the end.
        
    
    #90daysofdevops