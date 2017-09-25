
# Git Learnings:

`Git is a software which allows you to keep track of your changes in project.`

`GitHub is website for publishing your project managed by git so that many developers
can work simultaneously on different modules.`

Also you can make your project public so that other people can view and make
contributions to your projects.

Git is a version control system, a tool to manage your source code history. GitHub is a
hosting service for Git repositories. So they are not the same thing.
Git the tool, GitHub the service for projects that use Git.

# Basic Commands:
Initialize repository				 : 	`git init`
Adding files to stage 				 : 	`git add filename, git add *`
Committing to Repository 			 : 	`git commit -m "commit message"`
Add Remote Repository 				 : 	`git remote add origin URL`
Pushing changes to remote repository : 	`git push origin master/branchname`
Showing the commit history			 :  `git log`


## Difference between git pull and git merge:
`git pull does a git fetch followed by a git merge`

## If you do not wish to merge the remote branch into your local branch and want to do a force push, use the push command with -f 
`git push -f origin <branch>`
