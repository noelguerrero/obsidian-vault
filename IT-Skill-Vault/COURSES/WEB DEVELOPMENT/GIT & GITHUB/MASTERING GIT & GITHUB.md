
### Version Control
- A system that keeps records of your changes
- Allows collaborative development
- Allows you to know who made the changes and when.
- Allows you to revert any changes

****
### GITHUB
- Largest web-based git repository hosting service.
- Allows for code collaboration with anyone online.


### GIT
- Distributed version control
- Allows developers to track and manage changes to their code overtime.
- Designed to be fast and efficient, even with large codebases. It utilizes advance algorithms, minimizing the disk space usage.

#### Key concepts of git

- **Repository** - Allows you to performing various operations on it to create different versions of a project.
![[Pasted image 20251024155333.png]]

- **Commits** - it is a stage where in you will add your version of the project from the local directory to repository.
![[Pasted image 20251024155525.png]]

- **Branches** - It contains your version or other version of the project.
![[Pasted image 20251024155948.png]]

- **Merging** - It is a concept of merging commits stored into multiple branches into one. ![[Pasted image 20251024160209.png]]

### GIT IMPORTANT COMMANDS

#### Starting a Project
- git init
- git clone
- git config

#### Commiting Changes
- git add
- git commit

#### Working with Branches
- git branch
- git checkout
- git merge
- git fetch

#### Syncing Changes
- git pull
- git push

#### Helper Commands
- git status
- git log


### Application of GIT Commands
#### `git config`

Setting up the configuration of git into the system
```
$ git config --global user.name "Noel Guerrero"
$ git config --global user.email noelguerrerojr@gmail.com
```

if hindi sinelect si main as a default branch during the installation you can do this.
```
$ git config --global init.default branch main
```


If you want to see other commands of `git config`
```
$ git config -h
```



#### INITIALIZING GIT REPOSITORY
- first create a sample folder with file (named: git-example)

type the directory (in this scenario the folder is in the desktop)
```
$ cd Desktop

$ cd git-example

$ git init
```
![[Pasted image 20251024163414.png]]


#### SHOW STATUS

```
$ git status
```
![[Pasted image 20251024163759.png]]
note: untracked files meaning it currently not move into git repository


#### STAGE OR MOVE THE FILE
```
$ git add testing.txt
```
when we $ git status
![[Pasted image 20251024164211.png]]as you can see we have changes that we need to commit.


#### UNSTAGE OR REMOVE THE FILE
`git rm --cached testing.txt`
![[Pasted image 20251024164516.png]]

when we show the status it comes back into untracked files
![[Pasted image 20251024164751.png]]


**How to add all the untracked file**
```
$ git add .
```
![[Pasted image 20251027153948.png]]


#### CLEAR THE COMMAND LINE
syntax:
`$ clear`

from this:
![[Pasted image 20251027171451.png]]

to this:
![[Pasted image 20251027171519.png]]


#### RESTORE THE PREVIOUS VERSION OR UPLOAD THE EDITED FILE
![[Pasted image 20251027154526.png]]
As you can see the file is already edited

IF you want to move the changes 
`$ git add testing.txt`
![[Pasted image 20251027155106.png]]

If you want to restore the previous version
`$ git restore testing.txt`
![[Pasted image 20251027154903.png]]



#### EXCLUDE FILES
- First we create container that store ignore files (such as ignored modules, environment variable that shouldn't expose in the git repository).
```
$ touch .gitignore
```
![[Pasted image 20251027155916.png]]
you can add the name of the files, so that they cannot be pushed or cannot see in the repository

Example:
We create a file name ignore file.txt and when we show the status it come up in the untracked files
![[Pasted image 20251027160328.png]]

And when we put the name of it in the .gitignore
![[Pasted image 20251027160253.png]]

It will not show but since the .gitignore now contains the file it shows a status that its been modified or edited.
![[Pasted image 20251027160442.png]]



#### COMMITING A FILE
Tips: commit files by batch or the files must be related on each other.

Syntax:
`$ git commit -m "Add Message or the contents of files here"`

Example:
`$ git commit -m "Added Initialize file"`
![[Pasted image 20251027161536.png]]


#### SETTING UP GITHUB ACCOUNT
- Log in GitHub
- Create a new repository

**You will use this command if**

when you want to create a new repository on the command line and connect it.
```
echo "# git-practice" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/noelguerrero/git-practice.git
git push -u origin main
```


Or push an existing repository
```
git remote add origin https://github.com/noelguerrero/git-practice.git
git branch -M main
git push -u origin main
```

**And when we follow it this will show**
![[Pasted image 20251027162852.png]]

You can sign that and you will be redirecting to git manager and connect the local repository and your git hub repository. But if you want to use the token.

- Go to https://github.com/settings/tokens
- Generate a token 
- go to token and paste the generated token
![[Pasted image 20251027163906.png]]

And this will be the output:
![[Pasted image 20251027164128.png]]



#### CREATING GIT BRANCH
syntax: 
`$ git branch branchname`

example:
`$ git branch example`

note: when you creating a branch in main make sure your in the main first, or when you creating a branch of a branch make sure you're in that specific branch

#### SHOWING THE LIST OF BRANCH
example and syntax:
`$ git branch --list`
![[Pasted image 20251027170417.png]]


#### SWITCH TO A SPECIFIC BRANCH
syntax:
`$ git checkout branchname`

example:
`$ git checkout example`
![[Pasted image 20251027170746.png]]
tips: you can identify in the label next to the file location what specific branch are you. 

#### SWITCH BACK TO MAIN?
syntax and example:
`$ git checkout main`
![[Pasted image 20251027170903.png]]

#### DELETE BRANCH
Syntax:
`$ git branch -d branchname`

Example:
`$ git branch -d example`
![[Pasted image 20251027171255.png]]


#### SHORCUT TO CREATE BRACH AND AT THE SAME TIME SWITCH TO THAT BRANCH

Syntax:
`$ git checkout -b branchname`

Exampple
`$ git checkout -b feature1`
![[Pasted image 20251027171850.png]]


#### GETTING THE CHANGES FROM MAIN TO SPECIFIC BRANCH
- first we need to sync the changes from main to that specific branch

how can we do that?
```
$ git pull origin main
```
![[Pasted image 20251027172313.png]]


#### PUSHING CHANGES TO THE MAIN REPOSITORY
- first we create changes (e.g adding text to a text file)

On bash
- go to main branch
- check the status
- stage or move the changes
- commit the stage
- push the changes


Example:

```
$ git checkout main
$ git status
$ git add .
$ git commit -m "New Text Added"
$ git push origin main
```
![[Pasted image 20251027173314.png]]
Note: sometimes after typing the push, there is a tab or window that requesting the personal token, just paste the token and it will push the changes.


#### TO AVOID THAT WINDOW TO POP UP
This will prevent the window that requesting a token to pop up.
`$ git config --global credential.helper wincred`

#### SHORCUT OF CREATING A BRANCH AND GETTING THE CHANGES OF THE MAIN AT THE SAME TIME
Syntax:
`$ git checkout -b branchname origin/main`

Example: 
`$ git checkout -b hotfix origin/main`
![[Pasted image 20251028145927.png]]


#### MERGE SYNTAX
Syntax:
`$ git merge -m "message" branchname`

Example:
`$ git merge -m "merging hotfix changes into main" hotfix`
note: i type this syntax in main branch because i want to merge the hotfix changes into main branch.

#### HOW TO MERGING A BRANCHES
In this scenario we create a another branch and add changes, then we merge that specific branch into main 

- first we edit the file in the hotfix branch
- add the changes
- commit the changes
- then push it into hotfix branch (not in the main)
```
$ git add .
$ git commit -m "testing 2"
$ git push origin hotfix
```
![[Pasted image 20251028150705.png]]

**Merging the branch**
`$ git merge -m "merging hotfix changes" hotfix`
`$ git push origin main` - to push the changes in the local repository into GitHub repository 
![[Pasted image 20251028152219.png]]
note: make sure you're in the main branch when typing this code.


#### HOW CAN WE RESOLVE MERGE CONFLICT
In this scenario example their is a developer that fixing a bug to a file, and also youre fixing it too and then when you merge the update branch into main it will crash out.

**Dev 1**
The Dev1 Edit the file
![[Pasted image 20251028152928.png]]

**Dev 2**
They didn't know that dev 1 is fixing that but so it fix it too. The Dev 2 create a branch that fixing that bug 
![[Pasted image 20251028153302.png]]

**Assuming that we will in the feature1 branch**
```
$ git add .
$ git commit -m "fixing the bug by dev2"
$ git push origin feature1
```
![[Pasted image 20251028153629.png]]

**Going to main and merge the file**
note: it will crash because Dev1 also added a changes to the main 

since dev 1 have changes i pull the changes into main
```
$ git checkout main
$ git pull origin main
```

Then i merge the feature1 branch into main
`$ git merge -m origin feature1`
![[Pasted image 20251028154321.png]]

**HOW TO SOLVE IT?**
Open that specific file and you will see something like this
![[Pasted image 20251028154514.png]]
note:
This part is from the current main branch
```
<<<<<<< HEAD
Edited by Dev1
```

And this part is from feature 1 branch
```
Edited by Dev 2
>>>>>>> feature1
```

And the separated by:
```
=======
```


**From their you will decide which part you retain and which part you remove**
in this scenario i remove the changes of Dev 2

![[Pasted image 20251028155341.png]]
I removed the symbols and changes of dev 2 and i retain the changes of dev 1 that currently in the main

**And when i display the status this will show**
![[Pasted image 20251028155548.png]]

If we don't want to proceed in the merging you can abort the merging by typing this `$ git merge --abort`

But since we already fix the problem you can add and commit.
```
$ git add .
$ git commit -m "Fixed Merge conflict"
$ git push origin main
```
![[Pasted image 20251028160057.png]]


#### CLONING
This is the process of copy the remote repository (GitHub repository) to our local repository that don't need any set ups.

- Go to repository
- Click the code
- And this will show
![[Pasted image 20251028160415.png]]
In this scenario we use HTTPS

- Copy the link
- And in Gitbash go to desktop and type this
```
$ cd Desktop
$ git clone https://github.com/noelguerrero/git-practice.git
```
![[Pasted image 20251028161700.png]]