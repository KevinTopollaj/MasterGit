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

> 1. Create a directory :

`mkdir myDirectory`

> 2. Move inside that directory :

`cd myDirectory`

> 3. Create a new Git repository :

`git init`

> 4. Check the status of your repository :

`git status`

> 5. Start to track a newly added file in the directory and stage this change :

`git add [filename]`

> 6. Commit the changes to the local repository by adding a message :

`git commit -m "[yourMessage]"`

> 7. To see your commit :

`git log`

> 8. Create a repository in GitHub and get the https url to add the local changes to the remote repository :

`git remote add origin [yourHttpsUrl]`

> 9. Check if the remote repository is created :

`git remote -vv`

> 10. Move the repository content from your local computer to the remote repository, use ( -u | --set-upstream ) to ensure that the local branch will track the remote master branch  :

`git push -u origin main`


> You can see your local Git configurations using :

`git config --local --list`

> You can see your global Git configurations using :

`git config --global --list`

> You can change your user name and email used by Git to track commits using :

`git config user.name "[yourNewName]"`
`git config user.email "[yourNewEmail]"`

### Commiting Changes

> Commit representes the state of the directory at a particular point in time. Each commit has one or more parents and the transition from parent to child is represented by a Diff which are the differences/changes between the parent and the child.

> 1. Make a change in a file in your local repository.

> 2. To see the status of your files in your repository :

`git status`

> 3. To see the changes that you have made :

`git diff`

> 4. Track all the new added changes :

`git add .`

> 4. Commit the changes in your local repository :

`git commit -m "[yourMessage]"`

> 5. To see your commit history and the changes made in that commit :

`git log -p`

> 6. Push your changes to the remote repository :

`git push`

> Git tracks only the files not the directories that we may add in our repository so in order to track your directory you have to create it with a hidden file .keep.

> 1. Create the directory :

`mkdir myDirectory`

> 2. Add an hidden file inside the directory so you can track it using git :

`touch myDirectory/.keep`

> 3. Now you can add, commit and push the new directory to your remote repository.

### Staging Area

> Git has three conceptual areas :
> 1. Working Directory  -> the directory that you are working in.
> 2. Staging Area -> the directory for building your next commit, where you stage the changes using add.
> 3. Repository -> the directory for your local commits, where you create a reference for a point in history that you can then reference and access later on.

> The Staging area is very useful, it allows you to stage just 10 lines of a file that you might have change 80 lines. So it allows you to put the changes that you have made separate so you can create more than one commit with all the changes you have made.

> 1. Make a change in a file in your local repository.

> 2. See the changes that you have made that are not in the staging area :

`git diff`

> 3. Add all the changes in the staging area :

`git add .`

> 4. See the changes that you have made and that is in the staging area :

`git diff --staged`

> 5. Move the changes back from the staging area to your working directory :

`git reset HEAD [yourFileName]`

> 6. Launch interactive adding :

`git add -i`

> 7. Type 'p' to select subsections of each of the files :

`What now> p`

> 8. Type the first letter of the file that you want to use :

`Patch update>> [firstLetter]`

> 9. This will display all changes and call it a 'hunk' and give you the option to stage it :

`Stage this hunk [y,n,q,a,d,s,e,?]? `

> 10. By typing '?' it will show you all the options you can apply to your hunk :

`Stage this hunk [y,n,q,a,d,s,e,?]? ?`

```
y - stage this hunk
n - do not stage this hunk
q - quit; do not stage this hunk or any of the remaining ones
a - stage this hunk and all later hunks in the file
d - do not stage this hunk or any of the later hunks in the file
s - split the current hunk into smaller hunks
e - manually edit the current hunk
? - print help
```

> 11. By typing 's' it will split your hunk :

`Stage this hunk [y,n,q,a,d,s,e,?]? s`

> 12. By typing 'y' it will stage the first newly created hunk :

`Stage this hunk [y,n,q,a,d,s,e,?]? y`

> 13. By typing 'n' it will not stage the second created hunk :

`Stage this hunk [y,n,q,a,d,s,e,?]? n`

> 14. Type 's' to see the staged files :

`What now> s`

> 15. Type 'q' to exit :

`What now> q`

> 16. Commit the staged hunk :

`git commit -m "[yourMessage]"`

> 17. See the commits that you have created :

`git log`

> You can move a file from a directory to another using git and it will automatically stage the moved file into the new directory :

`git mv [oldDirectory]/[file] [newDirectory]`

> You can delete a file from a directory using git and it will automatically stage the deleted file change :

`git rm [directory]/[file]`

### Ignoring Files



### Viewing History



### Branching



### Merging



### Syncing with a Remote



### Pull Requests

---


