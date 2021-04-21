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

> It is useful to use it if you have passwords or API keys, you can use environment variables for what we don't want to track inside our repo.
> Locally these are stored in a file that is ignored by git so that when we commit it, it tracks everything apart of these files.
> So we create a .gitignore file, which is a simple text file where you list the patterns for the paths you want git to ignore, you can create it locally for a directory to ignore specific files in that directory or globally which will apply to all of the directories.

> You can create a git ignore file :

`touch .gitignore`

> You can edit it by adding constraints using the nano text editor :

`nano .gitignore`

> You can ignore all the .html files by adding the following line in the .gitignore file :

`*.html`

> You can ignore all the .html file that is not in the current directory but only the ones that are inside other directories contained inside the main directory :

`*/*.html`

> You can find the global gitignore file with the following command if it exists :

`git config --global core.excludefile`

> You can create it, if it does not exist :

`git config --global core.excludefile ~/.gitignore_global`

### Viewing History

> Using the command  `git log` will give you the history of your repository and you can see each commit in more detail like the hash, author, date, and message.

> If you want to see a specific number of your latest commits :

`git log -5`

> If you want to see a specific summary of your commits :

`git log --oneline`

> To see an ASCII representation for the branches within the graph :

`git log --graph`

> You can combine them together :

`git log --oneline --graph --decorate --all`

> To see the differences for consecutive commits :

`git log -p`

> To see changelogs where is the first line of each commit message grouped by author :

`git shortlog`

> To see a log of just the commits of a particular author :

`git log --author="[authorName]"`

> To search the commit messages you can write :

`git log --grep="[keyWord]"`

> To see a log for just one particular file :

`git log -- [fileName]`

> To search the content of the commit itself where the word is committed to :

`git log -S"[keyWord]" -p`

> Search the content of the commit for a specific keyWord :

`git log -p --all -S"[keyWord]"`

### Branching

> A commit represents a particular state of the tree directory, it also contains metadata like author, date, email, and the most important a reference to it's parent.
> All this is wraped inside the git repository and gives us an unique reference in a form of an hash using SHA1, this hash allows you to refer to a particular commit within your repository and every hash is unique so you can easily identify a specific commit using it's hash.

> A Branch is just a label associated with a particular commit, it is implemented as a file containing a SHA1 hash then as you create more commits that label gets moved forward updating as you create new commits on the branch.
> By default when you create a git repository git creates a branch for you and calls it the 'main' branch.

> You can create  a brach :

`git branch [branchName]`

> Creating a new branch creates a new file in .git/refs/heads/[branchName] that contains the SHA1 hash of the current commit :

`cat .git/refs/heads/[branchName]`

> To see the list of all of the branches :

`git branch`

> To move to the new created branch :

`git checkout [branchName]`

> To create and move to the new created branch :

`git checkout -b [branchName]`

> To delete the new created branch :

`git branch -d [branchName]`

> To see all the branches created localy and on remote :

`git branch --all`

> To track a remote branch :

`git checkout --track origin/[branchName]`

> Git will not let you delete a branch that has a commit so you will not lose the changes that are commited.
> To delete a branch that has commits in it :

`git branch -D [branchName]`

### Merging



### Syncing with a Remote



### Pull Requests

---


