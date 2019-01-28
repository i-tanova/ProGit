# ProGit
Pro Git Apress Book

## About Version Control
<p>
System that records changes to a file or set of files over times so taht you can recall specific version later.
<p/>

<p>
  Old VCS store each version of the file as patch sets.
 <p>
  
 <p>
  1. Local version controls
  2. Centrailzed Version Control Systems
  Centralized Version Control Systems as CVS, Subversion have a single server that contains all the versioned files 
  Advantages:
  ..*Everyone knows what everyone is doing
  ..*Admin can restrict write/read privleges
  
  Disadvantages:
  ..*Single point of failure (Server is down)
  3. Distributed Version Control - Git, Mercurial
  Client's files fully mirror the repository. Every checkout is really full backup of all the data.
  
  ## History of Git
  In 2002 the Linux kernel project began using a Distributed VCS - BitKeeper.
  2005 Linus Torvald writes own tool - Git ( Speed, Simple design, Support thousands of parallel branches, Distributed, large projects)
  
  ## Git Basics
  <p>
  The major difference between Git and any other VCS is Git thinksof its data more like a set of snapshots of miniature filesystem. It takes a snapshot of all the files and stores a reference to it. If a file has not changed Git doesnt store the file again, just a link to the previous identical file it has stored. Stream of snapshots.
</p>
  
  
