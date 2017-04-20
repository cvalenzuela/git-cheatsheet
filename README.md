# cheatsheet for git and github

### Create New Repo
```shell
git init
```

### Stage Files

```shell  
# Adds all files in cd
git add .
```

```shell  
# Adds all new or modified files
git add --all  
```

```shell  
# Add specific file
git add <FILE>
```

```shell  
# Adds all files witn .txt extension
git add "* .txt"
```

```shell  
# Unstage files. HEAD refers to the last commit on the branch we are.
git reset HEAD <FILENAME>
```

```shell  
# Blow away all changes since last commit
git checkout -- <FILENAME>
```
### Commit and Undo Commit
```shell
git commit -m 'comment here'
```

```shell
# Stage and commit at the same time if the file is already being tracked
git commit -a -m "comment here"
```

```shell
# Undo last commit and move everything from that commit back into staging. HEAD^ = move to commit before 'HEAD'  
git reset --soft HEAD^
```

```shell
# Add a new file to the last commit and maybe change the message
git commit --amend -m 'new message if we want to rewrite it'
```

```shell
# Undo last commit and all changes
git reset --hard HEAD^
```

```shell
# Undo last 2 commits and all changes
git reset --hard HEAD^^
```

### Check Status

```shell
git status
```

### Unstage and Remove
```shell
# Unstages all files that where commited.
git reset <FILENAME>
```

```shell
# Remove file from fs
git rm <FILENAME>
```

```shell
# Remove all .txt files
git rm '* .txt'
```

```shell
# Stop watching for this file
git rm --cached <FILENAME>
```

```shell
# Recursively remove all folders and files from the given directory.
git rm -r <FOLDERNAME>
```

```shell
# remove git (opposite of git init)
rm -rf .git
```

### Changes
```shell
# View unstaged differences since last commit
git diff
```

```shell
# View difference between two SHAs
git dif <SHA1> <SHA2>  
```

```shell
# diff between two branches
git diff <BRANCHNAME> <BRANCHNAME>
```

```shell
#  See what's different from pull repo and my most recent commit (HEAD)
git diff HEAD
```

```shell
# grandparent of latest commit
git diff HEAD^^
```

```shell
# Five commits ago
git diff HEAD~5
```

```shell
# Second most recent commit vs most recent commit
git diff HEAD^..HEAD
```

```shell
# See what files are commited (staged) or about to be pushed
git diff --staged
```

```shell
# see all the Commits
git log
git log --until=1.miute.ago
git log --since=1.day.ago
git log --since=1.hour.ago
git log --since=1.month.ago --until=2.weeks.ago
```

```shell
# Diffs with the logs
git log --patch
```

```shell
# How many deletions and insertions were made for each file included in each commit
git log --online --stat
```

```shell
# Visual Representation
git log --online --graph
```

```shell
# Change Files back to how they were at the last commit.
git checkout -- <target>
```

```shell
#See changes to the remote before you pull in
git fetch --dry-run
```

### Branches
```shell
# Create a new branch
git branch <BRANCHNAME>
```

```shell
# Move onto a branch
git checkout <BRANCHNAME>
```

```shell
# Create and switch(checkout) to a branch in one line
git checkout -b <BRANCHNAME>
```

```shell
# Creates a new branch that it's not tied to the history of the master branch. Usefull from gh-pages
git checkout --orphan <BRANCHNAME>  
```

```shell
#  List the branches
git branch
```

```shell
# List all remote branches
git branch -r
```

```shell
# Rename a branch you're currently on
git branch -m <NEWBRANCHNAME>
```

```shell
# Delete a Branch
git branch -d <BRANCHNAME>
```

```shell
# Show all of our remote branches and see if they are tracked
git remote show origin
```

```shell
# Delete remote branch
git push origin :<BRANCHNAME>
```

```shell
# to get rid of the local version of a deleted remote branch
git remote prune origin
```

```shell
# delete remote and local branch
git push origin --delete <branch_name>
git branch -d <branch_name>
```

### Merge

```shell
# From branch wanting to merge(master)
git merge <BRANCHTOMERGE>
```


### Ignore Files

```shell
nano .gitignore
```

### Config

```shell
git config --global user.name "Alexis Sanchez"
git config --global user.email "alexis@sanchez.com"
git config --global color.ui true # Add color to CLI
git config --global core.editor emacs # Use emcas for interactive coomands
git config --global merge.tool opendiff # Use a opendiff for merging conflicts
git config --global alias.st status # git st = git status -
git config --global alias.co checkout # git co = git checkout
git config --global alias.ci commit # git ci = git commit
git log -pretty=online # See all the SHAs in one line
```

### Set Remote Github

```shell
#Add a remote origin/upstream
git remote add origin <url>
```

```shell
#Set the upstream url as the master local branch
git branch --set-upstream-to=upstream/master master
```

```shell
# check is origin is good
git remote -v
```

```shell
# Change a remote URL
git remote set-url <REMOTENAME> <URL>
```

```shell
# View remote connections
git remote -v
```

```shell
# Remove remote
git remote rm <Name>
```

### Clone
```shell
# clone a repo, adds the origin remote pointing to url, checkout initial branch
git clone <URL>
# clone a repo and change its cd name
git clone <URL> <name> <!-- -->
```

### Pull and Fetch
```shell
# Pull changes and merge from a remote master branch
git pull
```

```shell
# Pull changes from a remote branch
git pull origin master
```

```shell
# Pull changes and don't merge from a remote master branch
git fetch
```

```shell
# Create a new branch and pull it from a new remote one.
git checkout --track origin/<BRANCHNAME>
```

```shell
# force a pull
git fetch --all
git reset --hard origin/master
```

### Push
```shell
# push everything to the github repo
git push origin master
```

```shell
# The -u tells Git to remember the parameters, so that next time we can simply run git push and Git will know what to do.
git push -u origin master
#  Same as above
git push --set-upstream origin <BRANCHNAME>
```

```shell
# Links local branch to the remote branch
git push origin <BRANCHNAME>
```

```shell
# force a push that's not been pulled
git push origin +master
```

### Rebase
```shell
#Move local commits after a fetch has been done
git rebase <!--  -->
```

```shell
# Move all changes to master which are not in origin/master to a temporary area, run all origin/master commits, run all commits in the temporary area one at a time.
git rebase <ORIGINOROTHERBRANCHNAME>
```

```shell
# Continue after fixing a problem
git rebase --continue
```

```shell
# Abort Rebase
git rebase --abort
```

### Tags
```shell
# Create new tag
git tag -a <NAME> -m <DESCRIPTION>
```

```shell
# Push remotely
git push --tags
```

```shell
# List all the tags
git tags
```

```shell
# Checkout to that Tag.
git checkout <TAGNAME>
```

### Blame
```shell
See how made the changes and when
git blame <FILE> --date short
```

### Help
```shell
git help
git help <COMMAND>
```

------------
### GitHub Standard Fork & Pull Request Workflow
###### Source: https://gist.github.com/Chaser324/ce0505fbed06b947d962
0) Create Fork

```shell
# Clone your fork to your local machine
git clone git@github.com:USERNAME/FORKED-PROJECT.git

# Add 'upstream' repo to list of remotes
git remote add upstream https://github.com/UPSTREAM-USER/ORIGINAL-PROJECT.git
```

1) Keeping Your Fork Up to Date

```shell
# Fetch upstream master and merge with your repo's master branch
git fetch upstream
git checkout master
git merge upstream/master
# or
git reset --hard origin/upstream # just to force! and delete local changes to upstream branch
```

2) Branch
```shell
# Checkout the master branch - you want your new branch to come from master
git checkout master

# Create a new branch named newfeature (give your branch its own simple informative name)
git branch newfeature

# Switch to your new branch
git checkout newfeature

# Commit changes
git add .
git commit -m 'cool feature'
```

3) Submitting a Pull Request

```shell
# Fetch upstream master and merge with your repo's master branch
git fetch upstream
git checkout master
git merge upstream/master

# If there were any new commits, rebase your development branch
git checkout newfeature
git rebase master
```

4) Rebase commits
```shell
# Rebase all commits on your development branch
git checkout
git rebase -i master
```
