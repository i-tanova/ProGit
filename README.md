# ProGit
Pro Git Apress Book

## About Version Control
 ##### What is version control system?
* System that records changes to a file or set of files over times so taht you can recall specific version later.
##### What variants they have?
 Old VCS store each version of the file as patch sets:
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
 * Git only adds data. It is almost impossible to delete something.
 ###### Which are the tree states of a file under git?
* Commited - Saved in your local db (.git directory)
* Modified - Changed but not saved
* Staged - Marked to go to db at the next commit (they are put in a file in .git (staging area or index)
###### What does *clone* command do?
* It copies object db to your filesyste (this is .git directory)
##### First-time setup of Git

``` git config ``` - a tool that helps with configuration
* etc/giconfig file - every user, all thir repos ```--system```
* ~/gitconfig - your user ```--global```
* .git/config - this git repo specific to this repo
   ```git config --global user.name "Jhon"```
  ```git config --global user.email "Email"```
  ```git config --list```


  
  
