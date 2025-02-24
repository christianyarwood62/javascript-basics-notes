# Branches
- these are alternative realitie versions of the files, they are called feature branches

# to create a new branch:
- git branch <branch_name>

# change to a branch:
- git checkout <branch_name>

# to create and change to that branch in one command:
- git checkout -b <branch_name>

# to see all branches:
- git branch
- the branch youre on will be an asterisk
- branch main is default

# set up the default branch to be called main:
- git config --global init.defaultBranch main

# merges:
- once im done working on a feature branch and ready to bring commits together to main branch
- git merge <branch_name>
- when a line of code is changed by 2 branches and tried to merge, a merge conflict arises which needs to be solved

# to delete a branch:
- git branch -d <branch_name> (**if its been merged with main already**)
- git branch -D <branch_name> (**if it hasnt been merged with main already**)

