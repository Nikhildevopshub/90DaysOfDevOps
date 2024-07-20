---
title: "Day 13 Task: Advance Git & GitHub for DevOps Engineers"
datePublished: Sat Jul 20 2024 17:08:28 GMT+0000 (Coordinated Universal Time)
cuid: clyudux1c000j09l318bz2clw
slug: day-13-task-advance-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721494803215/d2fbf2a8-e2b3-4bb3-ba5a-4e0ebaef2f9d.avif
tags: devops, devops-articles, 90daysofdevops, learninpublic

---

### Git Branching

Branches are a core concept in Git that allow you to isolate development work without affecting other parts of your repository. Each repository has one default branch and can have multiple other branches. You can merge a branch into another branch using a pull request.

Branches let you develop features, fix bugs, or safely experiment with new ideas in a contained area of your repository.

### Git Revert and Reset

Git reset and git revert are two commonly used commands that allow you to remove or edit changes you’ve made in the code in previous commits. Both commands can be very useful in different scenarios.

### Git Rebase and Merge

**What Is Git Rebase?**  
Git rebase is a command that lets users integrate changes from one branch to another, and the commit history is modified once the action is complete. Git rebase helps keep a clean project history.

**What Is Git Merge?**  
Git merge is a command that allows developers to merge Git branches while keeping the logs of commits on branches intact. Even though merging and rebasing do similar things, they handle commit logs differently.

For a better understanding of Git Rebase and Merge, check out this article.

---

### Tasks

#### Task 1: Feature Development with Branches

1. **Create a Branch and Add a Feature:**
    
    * Add a text file called `version01.txt` inside the `Devops/Git/` directory with “This is the first feature of our application” written inside.
        
    * Create a new branch from `master`:
        
        ```bash
        nikhil@nikhil-HP-ZBook-15:~/git$git checkout -b dev
        Switched to a new branch 'dev'
        ```
        
    * Commit your changes with a message reflecting the added feature:
        
        ```bash
        nikhil@nikhil-HP-ZBook-15:~/git$git add version01.txt
        nikhil@nikhil-HP-ZBook-15:~/git$git commit -m "Added new feature"
        ```
        
2. **Push Changes to GitHub:**
    
    * Push your local commits to the repository on GitHub:
        
        ```bash
        nikhil@nikhil-HP-ZBook-15:~/git$git push -u origin dev
        Enumerating objects: 3, done.
        Counting objects: 100% (3/3), done.
        Writing objects: 100% (3/3), 230 bytes | 230.00 KiB/s, done.
        Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
        To github.com:Nikhildevopshub/my-project.git
         * [new branch]      dev -> dev
        branch 'dev' set up to track 'origin/dev'.
        ```
        
3. **Add More Features with Separate Commits:**
    
    * Update `version01.txt` with the following lines, committing after each change:
        
        * 1st line: "This is the bug fix in development branch"
            
            ```bash
            nikhil@nikhil-HP-ZBook-15:~/git$echo "This is the bug fix in development branch" >> Devops/Git/version01.txt
            nikhil@nikhil-HP-ZBook-15:~/git$git commit -am "Added feature2 in development branch"
            ```
            
        * 2nd line: "This is gadbad code"
            
            ```bash
            nikhil@nikhil-HP-ZBook-15:~/git$echo "This is gadbad code" >> Devops/Git/version01.txt
            nikhil@nikhil-HP-ZBook-15:~/git$git commit -am "Added feature3 in development branch"
            ```
            
        * 3rd line: "This feature will gadbad everything from now"
            
            ```bash
            nikhil@nikhil-HP-ZBook-15:~/git$echo "This feature will gadbad everything from now" >> Devops/Git/version01.txt
            nikhil@nikhil-HP-ZBook-15:~/git$git commit -am "Added feature4 in development branch"
            ```
            
4. **Restore the File to a Previous Version:**
    
    * Revert or reset the file to where the content should be “This is the bug fix in development branch”:
        
        ```bash
        git revert HEAD~2
        ```
        

#### Task 2: Working with Branches

1. **Demonstrate Branches:**
    
    * Create 2 or more branches and take screenshots to show the branch structure.
        
2. **Merge Changes into Master:**
    
    * Make some changes to the `dev` branch and merge it into `master`:
        
        ```bash
        git checkout master
        git merge dev
        ```