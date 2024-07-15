---
title: "Day 12 Task: Deep Dive in Git & GitHub for DevOps Engineers"
datePublished: Mon Jul 15 2024 18:41:39 GMT+0000 (Coordinated Universal Time)
cuid: clynbzi29000i09mbf6ch12he
slug: day-12-task-deep-dive-in-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721068680976/07006613-9c54-4ccc-a961-d6cf8c603bbc.webp
tags: github, git, devops, devops-articles, 90daysofdevops

---

### What is Git and Why is it Important?

![Git Logo](https://git-scm.com/images/logos/downloads/Git-Logo-2Color.png align="left")

Git is like a diary for computer code. It keeps track of every change made, so you can look back and see who did what and when. This is especially useful when many people are working on the same project, helping to avoid mistakes and making sure everyone is on the same page.

### Difference Between Main Branch and Master Branch

"Main" and "Master" are just names for the main version of your project. "Master" was used in the past, but now many people use "Main" instead. They both serve the same purpose.

### Difference Between Git and GitHub

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721068561962/509723e4-abac-4a84-8e73-5b6efd0c579a.webp align="center")

### How to Create a New Repository on GitHub

![GitHub New Repository](https://docs.github.com/assets/images/help/repository/repo-create.png align="left")

1. Log in to GitHub.
    
2. Click the "+" icon in the top-right corner and choose "New repository."
    
3. Name your repository (e.g., "DevOps").
    
4. Click "Create repository."
    

![Creating a Repository](https://docs.github.com/assets/images/help/repository/create-repository-name.png align="left")

### Difference Between a Local & Remote Repository and Connecting Local to Remote

* **Local Repository**: Your project saved on your computer.
    
* **Remote Repository**: Your project saved online (like on GitHub).
    

To connect your project on your computer to GitHub:

1. Open your project.
    
2. Link it to GitHub with:
    
    ```plaintext
    git remote add origin <remote-repository-URL>
    ```
    

### Tasks

#### Task 1: Set User Name and Email Address

1. Set your name:
    
    ```plaintext
    git config --global user.name "Your Name"
    ```
    
2. Set your email:
    
    ```plaintext
    git config --global user.email "your.email@example.com"
    ```
    

#### Task 2: Create a Repository Named "DevOps" on GitHub and Connect Local Repository

1. Create the repository on GitHub (steps above).
    
2. Open your project:
    
    ```plaintext
    git init
    ```
    
3. Connect it to GitHub:
    
    ```plaintext
    git remote add origin https://github.com/your-username/DevOps.git
    ```
    
4. Create a new file:
    
    ```plaintext
    mkdir -p DevOps/Git
    echo "Some content for Day-02" > DevOps/Git/Day-02.txt
    ```
    
5. Save the file to your project:
    
    ```plaintext
    git add DevOps/Git/Day-02.txt
    git commit -m "Add Day-02.txt with content"
    ```
    
6. Upload your project to GitHub:
    
    ```plaintext
    git push -u origin master
    ```
    

This makes sure your project on your computer is connected to GitHub, and your changes are saved online.