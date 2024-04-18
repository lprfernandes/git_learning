GIT

clone - bring a repo into a folder on local machine
add - track the files and changes
commit - save files in git
push - upload git commits to a remote repo
pull - download changes from remote repo

## Creating from github

1. New repo
2. Create new file README.md
3. Commit new file
4. click in commits to see every commit
5. we can diff in each commit

6. Check git install with

    git --version

7. Install if not installed yet
8. On vscode open an empty folder.
9. In vscode open the terminal and then write

    git clone www.something.git

10. cd into the folder and it will indicate the master branch
11. on the readme file make some change
12. on the terminal will see the untracked changes by:

    git status

12. To track all we add

    git add .

13. After that we can commit by

    git commit -m "Initial commit from vscode"

14. In order to push to the remote repo we must have ssh keys. We'll connect our local machine to our remotes. In ps:

    ssh-keygen -t rsa -b4096 "lprfernandes@gmail.com"

The files are saved in the users dir .ssh. There are 2 files, one private key and one public key (.pub). We're going to upload our .pub key to github.
Settings/SSH and keys/ new ssh key/ and paste the token.


15. After the commit we can push, but before pushing we must create a remote. To create a remote

    git remote add origin wwwurloftherepo.git


16. To see if the remote was added successfuly we can check all the remotes by:

    git remove -v


17. Then we can push to origin. The -u means that we're creating an upstream defaulting the origin and the destination of the push

    git push -u origin master

18. In the next pushes we can no longer mention the upstream as it is already default and push by simply:

    git push

19. If we don't have access rights or if we need a code review we have to create a pull request before we merge our changes in.

## Git Branching

Master branch - were the trunk of the prod code is
Feature branch - to dev a feature and then merge it to master branch.
Hot Fix branch - branches from master to fix bugs and then merges back.

1. Check the branches of the repo by:

    git branch

2. To create a branch:

    git checkout -b feature/login

3. We change the file, add the change to staging and then commit

4. Now we switched to master branch:

    git checkout master

5. The changes aren't in this master branch but only on the other. To bring those changes to the master branch we must push and then merge if we have the rights to merge to master, if not, we must create a pull request. Before we merge we must see the code by diffing

    git diff feature/login

6. Change back to the branch feature/login to push and then create the pull request by

    git checkout feature/login
    git push -u origin feature/login

7. On github we can create the pull request manually. Then agree to merge. As we merge, if we are on the master branch, the changes don't appear.
Now we need to pull the changes to the local git.

    git pull

8. After the pr is merged back to branch, now we can delete the feature branch. 

    git branch -d feature/login

9. Now we create another branch

    git branch -b quick-test
    
10. And if we change another file in this branch, instead of adding again in a separate command, we can shorthand it to -a in the commit because this file is already known to git and we're only modifiyng it.

    git commit -am "initial commit"

11. if now we change the same file in the same line in the master branch, if we try to merge,
there will be a conflict. We can inspect it by

    git diff master

12. If we merge the master branch to our quick-test (to update the master code in our version)

    git merge master

We get a conflict. To fix, we can accept changes or accept the version in the IDE.

## Undoing

To undo staging

    git reset

To undo last commit

    git reset HEAD~1

To log all commits

    git log

To go back to a specific commit

    git reset hashofthecommit

If we want to force delete commits from a certain point

    git reset --hard hashofthecommit

## Forking

Find the repo you want to copy, click fork.
We can change files, commit and then push. We can also create a merge request to the original repo that was forked.







## Apps
GitKraken Git Gui
GitKraken Boards
GitKraken Timeline
Source Tree

## Environments
System - All users
Global - All repos of the current user
Local - The current repo

git config --global user.name "Luís Fernandes"
git config --global user.email lprfernandes@gmail.com
git config --global core.editor "code --wait"
git config --global -e //opens config file
git config --global core.autocrlf true //if in windows and input if in mac

## Start the repo

mkdir Moon //creates dir Moon
cd Moon //opens dir Moon
git init //Initializes the git repo
echo hello > file1.txt //creates file1.txt with text hello
echo hello > file2.txt //creates file2.txt with text hello 
git status //gets the status of the repo
git add . //adds alls the files to the staging area.
echo world >> file1.txt //appends text world to the file1.txt
git status //gets the status of the repo saying that once again there are changes to add to the stating area
git add file1.txt //adds the new version of file1.txt to the staging area
git status //gets the status of the repo saying that there are no changes and the local version is the same of the staging area
git commit -m "initial commit" //commits the stating area files to the repo

## Best practices for commits
It should be logically separated. Ex if we're bug fixing and then we find a typo we shouldn't commit both things in the same commit.


## Git Ignore

echo logs/ > .gitignore
code .gitignore

## Git 

git ls-files //shows the files in staging area
git rm --cached -r bin/ //removes from staging area

git diff --staged //to see whats in the staging area thats going on the next commit


//to set vscode as the default diff tool

git config --global diff.tool vscode
git config --global diff.tool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"

git config --global -e


//see the difftool
git difftool

//View the history
git log

//To check commits
git show (short code)
git show HEAD (last commit)
git show HEAD~1 (previous to last commit)
...
files are represented using blobs and dirs are represesented by trees

//restore files
git restore --staged file1.txt

