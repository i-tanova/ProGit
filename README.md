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
* remove file from staging area
`git rm` - removes the file from local dir and staging area








  
  
