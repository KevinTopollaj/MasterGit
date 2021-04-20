# Master Git

> Source control has the ability to remember the history of your project and to jump back in time with whatever kind of files you are working on, and it can integrate changes from different branches and then merge them into one.

> 1. Commit : It is a snapshot in time of your work.
> 2. Diff : It represents the changes for each commit.
> 3. Branch : It is represented by a split and then you have two different histories from a specific moment that move along.
> 4. Merge : It is created when you put together two branches.
> 5. Repository : It is called the entire scheme that has Commits, Diffs, Branches, and Merges.

> The key thing that makes Git different from Subversions is the fact that Git stores each Commit as what your project looks like at this point in time, Subversion stores the Diff so if you want to see how a Repository looked like at a specific time you have to go back to the beginning and replay all the Diffs.

### Cloning a Repository 

> Cloning consists of copying the entire Repository from the cloud into your local computer.

> 1. Remote is called the cloud where you clone the version of the Repository from (GitHub, GitLab, BitBucket).
> 2. Local Repository (CLONE) is called the version of the Repository you store on your disk.  

`git clone [yourHttpsUrl]`

### Creating a Remote Repository

> You can turn any directory on your computer into a Git Repository, and by doing that Git will create a hidden .git directory within that directory. It uses that directory for all of its metadata and its object storage to maintain the history as you move forward.

> 1. Create a Directory :

`mkdir myDirectory`

> 2. Move inside that directory :

`cd myDirectory`

> 3. Create a new Git Repository :

`git init`

> 4. Check the status of your Repository :

`git status`

> 5. Start to track a newly added file in the directory and stage this change :

`git add [filename]`

> 6. Commit the changes to the Remote Repository by adding a message :

`git commit -m "[yourMessage]"`

> 7. To see your commit :

`git log`


> You can see your local Git configurations using :

`git config --local --list`

> You can see your global Git configurations using :

`git config --global --list`

> You can change your user name and email used by Git to track commits using :

`git config user.name "[yourNewName]"`
`git config user.email "[yourNewEmail]"`

### Commiting Changes



### Staging Area



### Ignoring Files



### Viewing History



### Branching



### Merging



### Syncing with a Remote



### Pull Requests

---


