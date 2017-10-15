# Git Learnings:

>Git is a version control system, a tool to manage your source code history. 
>GitHub is a hosting service for Git repositories. 
>So they are not the same thing.
>Git the tool, GitHub the service for projects that use Git.

Also you can make your project public so that other people can view and make
contributions to your projects.

# What is HEAD?:
>HEAD is a pointer which points to the last commit.
>It can be used to modify the last commits.

# Basic Commands:
Initialize repository				 : 	`git init`  
Adding files to stage 				 : 	`git add filename, git add *`  
Committing to Repository 			 : 	`git commit -m "commit message"`  
Add Remote Repository 				 : 	`git remote add origin URL`  
Pushing changes to remote repository : 	`git push origin master/branchname`  
Showing the commit history			 :  `git log`  

# Advances Commands:
1. Difference between Working copy and repository:  
Command `git diff` shows the differences between the working copy(green) and the repository(red).  

2. Difference between Staging and repository:  
Command `git diff --staged` shows the differences between the staging(green) area and the repository(red).  

3. Remove file from repository as well as working area:  
Command `git rm third.txt` removes the file from the working area as well as from
the repository. After deleting `git status` shows that the changes are not committed.  
Do a `git commit -m "This is the point in time where we deleted file.txt"`.
It helps later if we want to bring this file back from repository.  

4. How to Move and Rename Files:  
Command `git mv second.txt pudding.txt` to move or rename a file. `git status` shows the status and then use commit.  
Else we need to do rename manually and then do the following:  
`git add pudding.txt`, `git rm second.txt`, `git status` and then `git commit`.  

5. How to Commit Directly to the Repository:  
Command `git commit -am "message"` directly moves the changes to the repository from working area. Use this only for editing, comments or similar minor changes.
Don't use this command if you are performing any delete or insertion operations on file.  
`a: to add to staging area.`  
`m: normal commit.`  

6. How to checkout directly from repository:  
Command `git checkout -- filename` replaces the working copy of the file from the repository. This is normally done if you did something wrong with the file and want to take the last committed file from the repository in the working area.  

7. UnStage Files:  
Command `git reset HEAD index.html` takes the file from the staging area to the working area. After making any changes you push the file to the staging area but then later realize that it shouldn't be committed. Use the command to bring it back to the working area.  

8. Getting old version from the repository:  
Command `git checkout commit_id -- index.html` gets that particular file from the repository history of the file and places in the working area.  Use `git log` to see the commits history(commit id) from where you need to take the file.  We don't need to give the entire commit id, upto 6-8 digits of the commit id is also fine.  

9. Pushing to GitHub Repository:  
`git remote add ashGitRepo GitHubRepoUrl`  
`git remote`  
`git remote rm ashGitRepo`  

10. gitignore and GitHub Desktop:  
If you don't like the command prompt use the desktop version of GitHub.  
If you don't want to include set of files which are part of your IDE but not related to project, create a `.gitignore` file and give the file names in it.  
ex: To ignore all the files of an IDE starting with `.idea` , create an entry `.idea` in `.gitignore` file.  

11. Difference between git pull and git merge:  
`git pull` does a `git fetch` followed by a `git merge`  
If you do not wish to merge the remote branch into your local branch and want to do a force push, use the push command with -f  
`git push -f origin <branch>`

# Git Config Commands:
- git config --global user.name "John Doe"
- git config --global user.email johndoe@example.com
- git config user.name
- git config user.email

A List of other git commands can be checked here [git-commands-url]

# Modifying Commits:
>We can only modify the last commit.
We can't modify the commits in between because it violates the security and data integrity.

` git commit --amend -m "Message"`

This will commit the changes to the last commit. Though it updates the last commit,
however the commit id changes(SHA)[Secure Hash] and also the timestamp(obviously).

# What does the 'revert' command does?:
>It takes commit id as parameter and flips the action of the commit.
i.e anything that was added will be deleted and vice-versa.

` git revert 12454asasas`

It will ask for updating the commit message in a default editor. If we are happy
with the message simply close the editor and it will be commited.

# Git stashing:
> When you want to switch branches, but you don’t want to commit what you’ve been working on yet so you’ll stash the changes.

- To push a new stash onto your stack: `git stash`
- To see which stashes you’ve stored: `git stash list`
- You can reapply the one you just stashed by using the command: `git stash apply`
- If you want to apply one of the older stashes: `git stash apply stash@{2}`. If you don’t specify a stash, Git assumes the most recent stash and tries to apply it.
- To remove stash: `git stash drop XYZ`(with the name of the stash to remove)
- To apply the stash and then immediately drop it from your stack: `git stash pop`
- To create a branch from stash: `git stash branch`. This creates a new branch for you, checks out the commit you were on when you stashed your work, reapplies your work there, and then drops the stash if it applies successfully



[//]: # (These are reference links used in the body)
[git-commands-url]: <https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html>