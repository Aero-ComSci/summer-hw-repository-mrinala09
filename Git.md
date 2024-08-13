# Learning Git and GitHub
## Step 1. Installing Git
You can simply download the git installer from here: https://git-scm.com/
Or if you have a Macbook:
* Head over to terminal and type the following `brew install git`
    * (other computers follow instructions on the given website)

## Step 2. Git Setup
In order to setup your Git, you have to configure it globally with your name and email address it will be used to verify your commits and stored with your repositories.

```
git config --global user.name "Mrinal A"
git config --global user.email "random_email@example.com"
```
## Step 3. Basic Git functions
### Creating a repository
```
git init
```
### Staging Your Files
```
git add.
```
### Commiting Any Changes
```
git commit -m "commit (whatever message you want to put here)"
```
* `-m` is used to be able to input any commit message you would like

### Checking Version History
This allows you to check the history of previous commits in a given repository
```
git log
```
## Step 4. Creating A New Branch
Suppose you want to try out a new function or feature for your code but you're scared about making changes to the main project itself in case something goes wrong in the process of developing the feature and dont want to add something incomplete. Well thats where git branches come in!
* It allows you to toggle between different versions/states of the project
* At that point once you are satisfied you can merge the branch to the main project but we'll get to that later

Here's how you would do it:
```
git checkout -b <branch name>
```
This automatically creates a new branch and move you immediately there 

## Step 4. Creating A New Repository on GitHub
Log in to GitHub and then from there you'll see the button `new repository` under the `+` sign. 
* Name the repository
* Give it a general description
* `Public` or `Private`
* Most often it is initialized with a ReadMe file like this repository!

YAY! You've created your repository!

GitHub will ask if you want to create a new repo from scratch or if you want to add a repo you have created locally. In this case, since we've already created a new repo locally, we want to push that onto GitHub so follow the '....or push an existing repository from the command line' section: 

## Step 5. Adding/Pushing a local Repository
First add the GitHub respository as a remote 
```
git remote add origin https://github.com/username/repository_name.git
```
Then you have to push it to GitHub directly
```
git push -u origin master
```
`-u` is used so that you can create a mainstream branch so any further push requests can be done without using `-u`

## Step 5. Branches 

### Pushing a Branch to GitHub
Now we'll push the commit in your branch to your new GitHub repo. This allows other people to see the changes you've made. If they're approved by the repository's owner, the changes can then be merged into the primary branch.
```
git push origin new-branch
```
Origin is shorthand for the URL for remote repository

### Merging a Branch 

Merge the new branch into the master branch:
```
git merge new-branch-name
```
### Deleting a Branch 
Once your done testing out this new function (scaredy cat 🥲) you can delete it:

```
git branch -d new-branch-name
```

YAYYYY YOU LEARNED GIT AND GITHUB (I did too, thank you!)

For more advanced topics, you can explore other commands for Git: stash, cherry-pic, rebase, bisect, stash. Alright, now I'm done, have fun!!! 












