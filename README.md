# ProGit
Pro Git Apress Book

## About Version Control
 ##### What is version control system?
* System that records changes to a file or set of files over times so taht you can recall specific version later.
##### What variants they have?
  1. Local version controls
  2. Centrailzed Version Control Systems
    Centralized Version Control Systems as CVS, Subversion have a single server that contains all the versioned files.
  * Advantages:
   *Everyone knows what everyone is doing
   *Admin can restrict write/read privleges
  * Disadvantages:
  *Single point of failure (Server is down)
  3. Distributed Version Control - Git, Mercurial
  Client's files fully mirror the repository. Every checkout is really full backup of all the data.
  
  ## History of Git
  In 2002 the Linux kernel project began using a Distributed VCS - BitKeeper.
  2005 Linus Torvald writes own tool - Git. Main focus on Speed, Simple design, Support thousands of parallel branches, Distributed, Large projects
  
  ## Git Basics
  ###### What is the difference with the rest?
  * The major difference between Git and any other VCS is Git thinks of its data more like a set of snapshots of miniature filesystem. It takes a snapshot of all the files and stores a reference to it. If a file has not changed Git doesn`t store the file again, just a link to the previous identical file it has stored. Stream of snapshots.
  * Basically it does not store only the changed file. It stores the whole *file system* at every change. However this is optimized - if a file is not changed Git stores only link to where it has previously saved that file
  > Git stores snapshots(the whole filesytem) of the project over time.
 * Every change is local. Git works as local file system.
 * Every change has checksum SHA-1 hash - integrity and security. Git stores these checksums in DB - hash of info in the file.
 > Git only adds data. It is almost impossible to delete something.
 ###### Which are the tree states of a file under git?
* Commited - Saved in your local db (.git directory)
* Modified - Changed but not saved
* Staged - Marked to go to db at the next commit (they are put in a file in .git (staging area or index)
###### What does *clone* command do?
* It copies object db to your filesyste (this is .git directory)
##### First-time setup of Git

``` git config ``` - a tool that helps with configuration

Files where configurations are stored:
* etc/giconfig file - every user, all thir repos ```--system```
* ~/gitconfig - your user ```--global```
* .git/config - this git repo specific to this repo
   ```git config --global user.name "Jhon"```
  ```git config --global user.email "Email"```
  ```git config --list```
###### How to get a repo?
* ```git init``` - creates .git folder, git repository skeleton
* ```git clone``` - copy all the repo, all the history, every version of every file. *ALL*.This also checkout latest version of the working files
     `git clone some_repo myDir` - this will clone the repo and name its folder myDir
###### How to track files?
* `git add file` - Now file is listed as ```changes to be commited``` after that command if you modify the file you must run git add again.
> git add saves the file as it is. It does not track further changes
###### Is there short command for status?
* ```git status -s``` - this shows files as M - modified, A - staged, ?? - not added
###### How to ignore files?
* Add file .gitignore
 `cat .gitignore`
> Uses glob patterns
````
* - matches 0 or more chars
 ? - matches one char
[a,b,c] -matches any of that chars
[a-z] - matches range
** - nested directory. Example: dirA/**/dirB - matches dirA/a/b/dirB or dirA/b/dirB
*.[a,o] - ignore any files ending in .a, .o
*~ - ignore files ending with tilda
# - comment (ignore that line)
dirA/  - ignore all at directory dirA
! - do not ignore that file. Example: You have *.a but then you add !b.a (File b.a will be tracked)
/dirA - ignore root dirA folder, but do not ignore a/b/dirA folders
doc/*.txt - ignore files doc/a.txt, but do not ignore doc/test/file.txt
doc/ - ignore all files in the doc directory
````

###### How to view your changes?
* What is changed and not staged `git diff` (no output if everything is staged). If something is staged and then changed - show difference between local and staged file
* What are the changes that are staged `git diff --staged`
###### How to commit your changes?
> `git commit` commits only staged files
* configure editor of comments (git config --global core.editor)
* `git commit -v` shows diff result while commiting
* `-a` option adds everything to staging area and commits (you skip git add part)
`git commit -a -m "Message"`
###### How to remove change?
* remove file from staging area and local dir
`git rm` - removes the file from local dir and staging area
`git rm -f` - by force
* remove file from staging area but not from local dir
`git rm --cashed <file>`
* Use file-glob pattern
`git rm log/\*.log` - remove all from log dir that has .log extension
`git rm \*.log` - all files that end with .log
 ###### View comit history
`git log` - most recent commits are first
- author, date, commit message
* see only differences between commits
`git log -p -2` - see diffs only in last 2 commits. Very helpful for code review.
`git log --stat` - only what files are changed
* See log in different format
`git log --pretty=oneline` 
`git log --pretty=format:"%h - %an, %ar : %s"` - %h - hash, %an author name, %ar author date - relative (6 years ago), %s subject. Author - who originally wrote the work, commiter - who apply changes
* See graph of merge history
`git log --pretty=format: "%h %s" --graph`
* Other options
`-p --stat --shortstat --name-only --name-status -abbrev-commit --relative-date --graph --pretty`
* Limit log output
 `git log--since=2.weeks` Another options --until 
* Filter by author 
`git log --author`
* Search specific words
`--grep`
* To use two filters at the same time
 `--all` - otherwise filters result will not merge
* Show only changes to specific code
`--S` - only show commits that introduced a change to code that added/removed that string
`git log --Sfunction_name`
* Show only changes in specified files
`git log --filename`
###### Undoing Things
* Change commit
`git commit -amend` - change your commit message if there is not staged changes. This commit replaces results of the first
* Unstage a staged file
`git reset HEAD <file>`
* Remove changes to a file
`git checkout --file` 
> git checkout rewrites the file permanently. No way back
##### Working with remotes
 Repos hosted oh the Internet or network somewhere.
* See names of your remotes
`git remote` \ origin (lists shortnames)
`git remote -v` \ origin https://github.com/repo url (lists url)
`git remote show [shortname]` - more information for branches and tracking branches
* Add remote repo
`git remote add [shortname] [url]`
* Fetch using shortname. Fetch someone else branch
`git fetch [shortname]` - Now you will have master branch of shortname *new branch shortname/branchname. You can merge it in your branch
* Git fetch and clone differences
>fetch pulls the that and you have references to all branches in a repo. It does not merge changes to it!
>clone adds the repo as orign
> pull a branch = fetch & merge it
* Push data
`git push remotename branchname`
* Remove and rename
`git remote rename [old] [new]`
`git remote rm [name]`
##### Working with tags






















  
  
