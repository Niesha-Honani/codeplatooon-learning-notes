# Embedded Repo Fix
Scenario: Accidentally creating a repo inside another repo using git init or by other means.
I've done this before and abandoned a whole useful repo and nearly quit everything but in our breakout
room - we figured it out. 

Symptom: 
You try to push your repo you created after creating a branch then doing git init inside a nother local repo or something else
And you get errors when you try to track your changes git add . or you get errors when trying to push to your GitHub repo
It will say something about a submodule and advice remove the submodule, etc. 

StackOverflow Says Remove Submodule:
Reference: https://stackoverflow.com/questions/25092958/nested-git-repository-mistake-method-to-remove-it


git rm path/to/embedded_repo

After reading the post and it works - Awesome! 
In my scenario and the one in our breakout room it didn't - so we had to go deeper 

In hindsight I found this gem 
Check if embedded repo is the problem - just to confirm. 

git rev-parse --show-toplevel

if you are not where you thought you were then 

cd ..
git rev-parse --show-toplevel

this shows the repo root you are in - do this until you are the top level of the repo you want to be in
and shows all the nested repos

you can also find nested .git dirs under the outer repo

find . -type d -name .git -not -path './.git'

changed directory to the repo you want to remove 

cd /accidental_repo

rm -rf .git 

if that works change directory to your parent repo add and commit --> push

However if you continue to get the errors and responses about submodules and repo things
possibly you may have created a local repo using git init 
So you made a branch called second_branch
typed in git init --> turned into a repo 

## Deinit
if you type submodule help in the terminal there is a piece about deinitializing the embedded repo

git submodule [--quiet] deinit [-f|--force] (--all| [--] <path>...)

- change directory to the root level of the repo you want to be in and out of the embedded repo
example:

cd main_repo 

then: 

git submodule deinit -f embedded_repo

git rm -cached embedded_repo

or 
git rm -f embedded_repo

if it was pushed at some point and exists in your GitHub repo then 
git add . 
git commit -m "removed.."
git push 

otherwise check to see if it worked 
find . -type d -name .git -not -path './.git'


I wanted to capture this process for future reference because I will do it again. 


