# Beginning Git

## Table of contents
* [General Info](#general-info)
* [Cloning a Repository](#cloning-a-repository)
* [Creating a Remote Repository](#creating-a-remote-repository)
* [Commiting Changes](#commiting-changes)
* [Staging Area](#staging-area)
* [Ignoring Files](#ignoring-files)
* [Branching](#branching)
* [Merging](#merging)
* [Syncing with a Remote](#syncing-with-a-remote)
* [Pull Requests](#pull-requests)
* [Master Git](#master-git)

## General Info

> Source control has the ability to remember the history of your project and to jump back in time with whatever kind of files you are working on, and it can integrate changes from different branches and then merge them into one.

> 1. Commit : It is a snapshot in time of your work.
> 2. Diff : It represents the changes for each commit.
> 3. Branch : It is represented by a split and then you have two different histories from a specific moment that move along.
> 4. Merge : It is created when you put together two branches.
> 5. Repository : It is called the entire scheme that has Commits, Diffs, Branches, and Merges.

> The key thing that makes Git different from Subversions is the fact that Git stores each Commit as what your project looks like at this point in time, Subversion stores the Diff so if you want to see how a Repository looked like at a specific time you have to go back to the beginning and replay all the Diffs.

## Cloning a Repository

> Cloning consists of copying the entire Repository from the cloud into your local computer.

> 1. Remote is called the cloud where you clone the version of the Repository from (GitHub, GitLab, BitBucket).
> 2. Local Repository (CLONE) is called the version of the Repository you store on your disk.  

`git clone [yourHttpsUrl]`


## Creating a Remote Repository

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

## Commiting Changes

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


## Staging Area

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


## Ignoring Files

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


## Branching

> A commit represents a particular state of the tree directory, it also contains metadata like author, date, email, and the most important a reference to its parent.
> All this is wrapped inside the git repository and gives us a unique reference in a form of a hash using SHA1, this hash allows you to refer to a particular commit within your repository and every hash is unique so you can easily identify a specific commit using its hash.

> A Branch is just a label associated with a particular commit, it is implemented as a file containing a SHA1 hash then as you create more commits that label gets moved forward updating as you create new commits on the branch.
> By default when you create a git repository git creates a branch for you and calls it the 'main' branch.

> You can create a branch :

`git branch [branchName]`

> Creating a new branch creates a new file in .git/refs/heads/[branchName] that contains the SHA1 hash of the current commit :

`cat .git/refs/heads/[branchName]`

> To see the list of all of the branches :

`git branch`

> To move to the newly created branch :

`git checkout [branchName]`

> To create and move to the newly created branch :

`git checkout -b [branchName]`

> To delete the newly created branch :

`git branch -d [branchName]`

> To see all the branches created locally and on remote :

`git branch --all`

> To track a remote branch :

`git checkout --track origin/[branchName]`

> Git will not let you delete a branch that has a commit so you will not lose the changes that are committed.
> To delete a branch that has commits in it :

`git branch -D [branchName]`


## Merging

> Merging consists of taking two branches and join them back together.
> The Main branch is what is deployed in production and it has only merged in it, this merges come from a branch called the Development branch and this is deployed to the staging system, if we want to create a new feature you can create a new Feature branch from Development branch and make some commits on the new Feature branch that has the new feature and then we merge that Feature branch back to the Development branch.

> Since the commit-graph is well defined in git it allows git to use a three-way merge which makes merging less error-prone, so it looks at the previous commits, it looks at the two commits at the end, and it looks at the common ancestors where one branch left the other one. It uses this information to create that merge commit.

> If two people edit the same line of code in the same file differently you will get a merge conflict because git will not know which one to keep.

> Move to the branch that you have made the commits :

`git checkout [branchName]`

> Check the commits that you have made :

`git log`

> Move back to the main branch :

`git checkout main`

> Merge the branch that you have created with the main branch :

`git merge [branchName]`

> Fast Forward Merge, it happens when you create a branch from the Main branch you make some commits in that new branch and then move back to the Main branch and merge it with the new branch. This way you did not create a merge commit you have only moved the Master branch to the end of the new commits made by the new branch that we created from the Main branch.

> If you want to create a merge commit you go to the Main branch and you can write :

`git merge --no-ff [branchName]`


## Syncing with a Remote

> There are two fundamental processes to work with remote directory labeled: PUSH and PULL

> You push your local changes to the remote repository :

`git push`

> You pull changes from the remote repository to your local repository :

`git pull` or `git fetch`

> You can list all your remotes that are associated with the current repository :

`git remote -v`

> Will list the branches and the remote branches they are tracking :

`git branch -vv`

> Will list all branches including remote branches :

`git branch -vv --all`

> You can create a new remote :

`git remote add [remoteName] [repositoryURL]`

> You can take the remote changes :

`git fetch [remoteName]`

> You can see more detail for a specific remote repository :

`git remote show [remoteName]`


## Pull Requests

> A pull request forms a kind of review process around a merge.
> If you work for an open-source project hosted on GitHub you need to fork the repository, making your changes, commit them to your own fork and then create a pull request from your fork back to the original repository.
> This pull request is just a merge of your code back into the origin, you can also use a pull request to merge from one branch to another within the same repository.
> A pull request forms a forum for discussing changes, adding continuous integration, testing, and code review.

> Create a new local branch :

`git checkout -b [branchName]`

> Make some changes and push the branch to the remote repository :

`git push --set-upstream origin [branchName]`

> You can check that the remote branch is created :

`git branch --all -vv`

> To create a new pull request you go to your GitHub account in the 'Pull requests' tab and click on the 'New pull request' button, after you can chose the 'base: branch' that will get the changes and the 'compare: branch' that has the changes and will be merged in the 'base: branch', it will then show you all the changes between those files and if you are ok with the changes you click the 'Create pull request' button, it will send you into another page where you can add more information and in the right side you can add Reviewers, Assignees, Labels, Projects, and Milestone. After you click the 'Create pull request' button and it will create the pull request, even if you created the pull request you can continue to add work to it and push the changes and at the bottom you can add extra comments related to that pull request.
> At the top we have Conversation tab where we can see the commits and the comments, Commits tab where we can se all the commits that have been made in this pull request, Filechanged tab will show you the chnages that have been made in each file, if you click the 'Review changes' button you can Comment changes without approval, Approve where you could give a feedback and approve merging these changes, Request changes give feedback and address changes to be made before merging.
> If you click the 'Merge pull request' button ti will display a comment and another button 'Confirm merge' to merge the changes and then it gives you a button 'Delete branch' to delete the brach witch changes have been merged.

> Go to the main branch :

`git checkout main`

> Get all the latest information from the remote repo :

`git fetch`

> If we run `git status` command we can see that our main branch is behind origin/main branch so to update your local main branch you run `git pull` command

> To see if any branches have been deleted from the remote repository and apply those changes locally :

`git remote prune origin`


---

# Master Git

## Table of contents
* [Beginning Git](#beginning-git)
* [Git Info](#git-info)
* [Merge Conflicts](#merge-conflicts)
* [a](#a)
* [a](#a)
* [a](#a)
* [a](#a)
* [a](#a)
* [a](#a)
* [a](#a)
* [a](#a)
* [a](#a)

## Git Info

> All of the data that git uses to be able to provide the entire history of your repository is stored in a form of key-value, where a key points to data.
> At a high level, a commit is just a tree that represents all of the files in your working directory.
> All files that have changes when you commit them, it takes each of them and calculates the SHA1 hash of its content and it uses that as a key and the value is a compressed content of the file.
> At the commit time, git creates all of the items within the tree in the Blob Store, it then needs to represent how the tree looks like for that commit, and to do that it creates a simple text file that has the keys of the items in the tree and puts it in the Blob Store, where it compresses the contents and finds the hash of it, the hash is the key and the compressed content of that tree file goes in the Blob Store as the value.
> A commit also has a reference to the parent, then git creates a new simple Commit text file that represents the commit itself and it has a reference to the tree which is a key and a reference to its parent commit and it wraps that up in a file finds a hash and uses that as a key compresses the content as a value and stores it in the Blob Store.
> So every aspect of the commit (Files, Tree, Commit text files) is stored in the Blob Store, and the hashes you see when you are using git are just the keys used in the Blob Store.
> That is why braches are very cheap in git because everything is referenced by this key in the Blob Store as a SHA1 hash, so to chose a different point in the git repo you just use a different hash, so the branch is just a file with a reference to that SHA1 hash when you check it out git goes and finds the commit and from there it can find what tree it needs and it recreates that tree in your working directory.

## Merge Conflicts

> If two users edited the same line in a file from two different branches and try to merge one branch to the other it will cause a merge conflict.

> To reset the merge :

`git reset --hard HEAD`

> To change the conflict style :

`git config merge.conflictstyle diff3`

> When we rerun the merge `git merge [branchThatHasChanges]` you will see that you have three sections :
> 1. HEAD : that is the current branch code.
> 2. merge common ancestors : is the code of the branch that the two other branches have been created from.
> 3. [branchThatHasChanges] : is the code of the branch you are trying to take the changes from.

> To solve the merge conflict you have to manually make the changes in the file that has conflicts and leave the code that you need to be on that file.
> After solving the merge conflict you need to run the `git add .` command to add the changes in the staging area and then run `git commit -m "[yourMessage]"` to commit the changes.
> You can now delete the branch that you have merged into your branch by running `git branch -d [branchThatHasChanges]`

> On macOS when you install Xcode it provides for you a tool called 'opendiff', you can use this to graphically see diffs and resolve merge conflicts.
> First, you need to set the config `git config merge.tool opendiff` then you can run a merge `git merge [branchThatHasChanges]` and it will inform you about the conflict.
> You can run `git mergetool` to invoke the merge tool that we set up in the configuration 'opendiff', on the left-hand side are the local changes made on the branch that you are currently in, and on the right-hand side are the changes that you are trying to merge in from the other branch. 
> At the bottom right we can choose the Action that we want to perform on the merge conflict.
> By running the `git status` we will see that doing it in this way will create a file '[fileName].[fileExtension].orig' which is where the merge conflict is stored, so we don't need that and we can remove it using `rm [fileName].[fileExtension].orig` and then we can add and commit the changes and delete the branch that you have merged into your branch by running `git branch -d [branchThatHasChanges]`.
