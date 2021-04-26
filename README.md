# Beginning Git

## Table of contents
* [General Info](#general-info)
* [Cloning a Repository](#cloning-a-repository)
* [Creating a Remote Repository](#creating-a-remote-repository)
* [Commiting Changes](#commiting-changes)
* [Staging Area](#staging-area)
* [Ignoring Files](#ignoring-files)
* [Viewing History](#viewing-history)
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

> 1. Create a directory :  `mkdir myDirectory`

> 2. Move inside that directory :  `cd myDirectory`

> 3. Create a new Git repository :  `git init`

> 4. Check the status of your repository :  `git status`

> 5. Start to track a newly added file in the directory and stage this change :  `git add [filename]`

> 6. Commit the changes to the local repository by adding a message :  `git commit -m "[yourMessage]"`

> 7. To see your commit :  `git log`

> 8. Create a repository in GitHub and get the https url to add the local changes to the remote repository :  `git remote add origin [yourHttpsUrl]`

> 9. Check if the remote repository is created :  `git remote -vv`

> 10. Move the repository content from your local computer to the remote repository, use ( -u | --set-upstream ) to ensure that the local branch will track the remote master branch  :  `git push -u origin main`


> You can see your local Git configurations using :  `git config --local --list`

> You can see your global Git configurations using :  `git config --global --list`

> You can change your user name and email used by Git to track commits using :  `git config user.name "[yourNewName]"`  `git config user.email "[yourNewEmail]"`


## Commiting Changes

> Commit representes the state of the directory at a particular point in time. Each commit has one or more parents and the transition from parent to child is represented by a Diff which are the differences/changes between the parent and the child.

> 1. Make a change in a file in your local repository.

> 2. To see the status of your files in your repository : `git status`

> 3. To see the changes that you have made : `git diff`

> 4. Track all the new added changes : `git add .`

> 4. Commit the changes in your local repository : `git commit -m "[yourMessage]"`

> 5. To see your commit history and the changes made in that commit : `git log -p`

> 6. Push your changes to the remote repository : `git push`


> Git tracks only the files not the directories that we may add in our repository so in order to track your directory you have to create it with a hidden file .keep.

> 1. Create the directory : `mkdir myDirectory`

> 2. Add an hidden file inside the directory so you can track it using git : `touch myDirectory/.keep`

> 3. Now you can add, commit and push the new directory to your remote repository.


## Staging Area

> Git has three conceptual areas :
> 1. Working Directory  -> the directory that you are working in.
> 2. Staging Area -> the directory for building your next commit, where you stage the changes using add.
> 3. Repository -> the directory for your local commits, where you create a reference for a point in history that you can then reference and access later on.

> The Staging area is very useful, it allows you to stage just 10 lines of a file that you might have change 80 lines. So it allows you to put the changes that you have made separate so you can create more than one commit with all the changes you have made.

> 1. Make a change in a file in your local repository.

> 2. See the changes that you have made that are not in the staging area :  `git diff`

> 3. Add all the changes in the staging area :  `git add .`

> 4. See the changes that you have made and that is in the staging area : `git diff --staged`

> 5. Move the changes back from the staging area to your working directory :  `git reset HEAD [yourFileName]`

> 6. Launch interactive adding :  `git add -i`

> 7. Type 'p' to select subsections of each of the files :  `What now> p`

> 8. Type the first letter of the file that you want to use :  `Patch update>> [firstLetter]`

> 9. This will display all changes and call it a 'hunk' and give you the option to stage it :  `Stage this hunk [y,n,q,a,d,s,e,?]? `

> 10. By typing '?' it will show you all the options you can apply to your hunk :  `Stage this hunk [y,n,q,a,d,s,e,?]? ?`

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

> 11. By typing 's' it will split your hunk :  `Stage this hunk [y,n,q,a,d,s,e,?]? s`

> 12. By typing 'y' it will stage the first newly created hunk :  `Stage this hunk [y,n,q,a,d,s,e,?]? y`

> 13. By typing 'n' it will not stage the second created hunk :  `Stage this hunk [y,n,q,a,d,s,e,?]? n`

> 14. Type 's' to see the staged files :  `What now> s`

> 15. Type 'q' to exit :  `What now> q`

> 16. Commit the staged hunk :  `git commit -m "[yourMessage]"`

> 17. See the commits that you have created :  `git log`


> You can move a file from a directory to another using git and it will automatically stage the moved file into the new directory :  `git mv [oldDirectory]/[file] [newDirectory]`

> You can delete a file from a directory using git and it will automatically stage the deleted file change :  `git rm [directory]/[file]`


## Ignoring Files

> It is useful to use it if you have passwords or API keys, you can use environment variables for what we don't want to track inside our repo.
> Locally these are stored in a file that is ignored by git so that when we commit it, it tracks everything apart of these files.
> So we create a .gitignore file, which is a simple text file where you list the patterns for the paths you want git to ignore, you can create it locally for a directory to ignore specific files in that directory or globally which will apply to all of the directories.

> You can create a git ignore file :  `touch .gitignore`

> You can edit it by adding constraints using the nano text editor :  `nano .gitignore`

> You can ignore all the .html files by adding the following line in the .gitignore file :  `*.html`

> You can ignore all the .html file that is not in the current directory but only the ones that are inside other directories contained inside the main directory :  `*/*.html`

> You can find the global gitignore file with the following command if it exists :  `git config --global core.excludefile`

> You can create it, if it does not exist : `git config --global core.excludefile ~/.gitignore_global`


## Viewing History

> Using the command  `git log` will give you the history of your repository and you can see each commit in more detail like the hash, author, date, and message.

> If you want to see a specific number of your latest commits :  `git log -5`

> If you want to see a specific summary of your commits :  `git log --oneline`

> To see an ASCII representation for the branches within the graph :  `git log --graph`

> You can combine them together :  `git log --oneline --graph --decorate --all`

> To see the differences for consecutive commits : `git log -p`

> To see changelogs where is the first line of each commit message grouped by author :  `git shortlog`

> To see a log of just the commits of a particular author :  `git log --author="[authorName]"`

> To search the commit messages you can write :  `git log --grep="[keyWord]"`

> To see a log for just one particular file :  `git log -- [fileName]`

> To search the content of the commit itself where the word is committed to :  `git log -S"[keyWord]" -p`

> Search the content of the commit for a specific keyWord :  `git log -p --all -S"[keyWord]"`


## Branching

> A commit represents a particular state of the tree directory, it also contains metadata like author, date, email, and the most important a reference to its parent.
> All this is wrapped inside the git repository and gives us a unique reference in a form of a hash using SHA1, this hash allows you to refer to a particular commit within your repository and every hash is unique so you can easily identify a specific commit using its hash.

> A Branch is just a label associated with a particular commit, it is implemented as a file containing a SHA1 hash then as you create more commits that label gets moved forward updating as you create new commits on the branch.
> By default when you create a git repository git creates a branch for you and calls it the 'main' branch.

> You can create a branch :  `git branch [branchName]`

> Creating a new branch creates a new file in .git/refs/heads/[branchName] that contains the SHA1 hash of the current commit : `cat .git/refs/heads/[branchName]`

> To see the list of all of the branches : `git branch`

> To move to the newly created branch :  `git checkout [branchName]`

> To create and move to the newly created branch :  `git checkout -b [branchName]`

> To delete the newly created branch :  `git branch -d [branchName]`

> To see all the branches created locally and on remote :  `git branch --all`

> To track a remote branch :  `git checkout --track origin/[branchName]`


> Git will not let you delete a branch that has a commit so you will not lose the changes that are committed.
> To delete a branch that has commits in it : `git branch -D [branchName]`


## Merging

> Merging consists of taking two branches and join them back together.
> The Main branch is what is deployed in production and it has only merged in it, this merges come from a branch called the Development branch and this is deployed to the staging system, if we want to create a new feature you can create a new Feature branch from Development branch and make some commits on the new Feature branch that has the new feature and then we merge that Feature branch back to the Development branch.

> Since the commit-graph is well defined in git it allows git to use a three-way merge which makes merging less error-prone, so it looks at the previous commits, it looks at the two commits at the end, and it looks at the common ancestors where one branch left the other one. It uses this information to create that merge commit.

> If two people edit the same line of code in the same file differently you will get a merge conflict because git will not know which one to keep.

> Move to the branch that you have made the commits :  `git checkout [branchName]`

> Check the commits that you have made :  `git log`

> Move back to the main branch :  `git checkout main`

> Merge the branch that you have created with the main branch :  `git merge [branchName]`

> Fast Forward Merge, it happens when you create a branch from the Main branch you make some commits in that new branch and then move back to the Main branch and merge it with the new branch. This way you did not create a merge commit you have only moved the Master branch to the end of the new commits made by the new branch that we created from the Main branch.

> If you want to create a merge commit you go to the Main branch and you can write :  `git merge --no-ff [branchName]`


## Syncing with a Remote

> There are two fundamental processes to work with remote directory labeled: PUSH and PULL

> You push your local changes to the remote repository :  `git push`

> You pull changes from the remote repository to your local repository :  `git pull` or `git fetch`

> You can list all your remotes that are associated with the current repository :  `git remote -v`

> Will list the branches and the remote branches they are tracking :  `git branch -vv`

> Will list all branches including remote branches :  `git branch -vv --all`

> You can create a new remote :  `git remote add [remoteName] [repositoryURL]`

> You can take the remote changes :  `git fetch [remoteName]`

> You can see more detail for a specific remote repository :  `git remote show [remoteName]`


## Pull Requests

> A pull request forms a kind of review process around a merge.
> If you work for an open-source project hosted on GitHub you need to fork the repository, making your changes, commit them to your own fork and then create a pull request from your fork back to the original repository.
> This pull request is just a merge of your code back into the origin, you can also use a pull request to merge from one branch to another within the same repository.
> A pull request forms a forum for discussing changes, adding continuous integration, testing, and code review.

> Create a new local branch :  `git checkout -b [branchName]`

> Make some changes and push the branch to the remote repository :  `git push --set-upstream origin [branchName]`

> You can check that the remote branch is created :  `git branch --all -vv`

> To create a new pull request you go to your GitHub account in the 'Pull requests' tab and click on the 'New pull request' button, after you can chose the 'base: branch' that will get the changes and the 'compare: branch' that has the changes and will be merged in the 'base: branch', it will then show you all the changes between those files and if you are ok with the changes you click the 'Create pull request' button, it will send you into another page where you can add more information and in the right side you can add Reviewers, Assignees, Labels, Projects, and Milestone. After you click the 'Create pull request' button and it will create the pull request, even if you created the pull request you can continue to add work to it and push the changes and at the bottom you can add extra comments related to that pull request.
> At the top we have Conversation tab where we can see the commits and the comments, Commits tab where we can se all the commits that have been made in this pull request, Filechanged tab will show you the chnages that have been made in each file, if you click the 'Review changes' button you can Comment changes without approval, Approve where you could give a feedback and approve merging these changes, Request changes give feedback and address changes to be made before merging.
> If you click the 'Merge pull request' button ti will display a comment and another button 'Confirm merge' to merge the changes and then it gives you a button 'Delete branch' to delete the brach witch changes have been merged.

> Go to the main branch : `git checkout main`

> Get all the latest information from the remote repo :  `git fetch`

> If we run `git status` command we can see that our main branch is behind origin/main branch so to update your local main branch you run `git pull` command

> To see if any branches have been deleted from the remote repository and apply those changes locally :  `git remote prune origin`


---

# Master Git

## Table of contents
* [Beginning Git](#beginning-git)
* [Git Info](#git-info)
* [Merge Conflicts](#merge-conflicts)
* [Stashes](#stashes)
* [Aliases](#aliases)
* [Rebase](#rebase)
* [Gitignore](#gitignore)
* [Cherry Picking](#cherry-picking)
* [Filter Branch](#filter-branch)
* [Undo](#undo)
* [GITK](#gitk)
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

> To reset the merge :  `git reset --hard HEAD`

> To change the conflict style :  `git config merge.conflictstyle diff3`


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


## Stashes

> Stashes allow you to record the current state of your working directory and then clean it, after it, you can perform many git operations like `git pull`, `git checkout [branchName]`.

> You can then reapply those changes that you recorded whenever you want to, this can be useful for pulling changes into a directory, it can also be helpful for coping with interruptions in the workflow, or if you have some personal changes that you don't want to commit to the repo so you can stash them and each time you commit they will not be committed and then you can easily reapply them again.

> To stash your changes : `git stash`

> To see a list of all the stashes that you have : `git stash list`

> To reapply the latest stash : `git stash apply`

> Even now that we have reapplied it again if we run the `git stash list` command it will still be in the list.

> To get a more detailed look at our current stash you run : `git stash show -p`

> To look at the second entry in the stash list : `git stash show stash@{1}`

> If you want to reapply the changes and remove the stash from the list : `git stash pop`

> You can provide your own message when you stash a change : `git stash push -m "[yourMessage]"`

> To see a more detailed content of a specific stash : `git stash show -p stash@{[stashNumber]}`

> To remove a specific item in the stash list : `git stash drop stash@{[stashNumber]}`

> You can go to another branch `git checkout [branchName]` and in there you can apply changes of a specific stash `git stash pop stash@{[stashNumber]}` and this will give us a merge conflict, we can then lunch the mergetool using `git mergetool` of Xcode and resolve the merge, that will apply the changes but will leave a file that has the merge conflict and we can remove that using `rm [fileName].[fileExtension].orig` and after that, we can commit the changes. 
> If we take a look at the stash list using `git stash list` the stash that we applied in the branch is not removed because we had merge conflicts so we can use `git stash drop stash@{[stashNumber]}`.


## Aliases

> It's a way of taking a really long git command and make it shorter by providing your way of writing it.
> You can create your own aliases for long commands.

> To create your own alias : `git config alias.[yourShortCommand] '[gitOriginalCommand]'`

> Example : `git config alias.st 'stash show -p'`

> To see the aliases that you have created in your local repository :  `cat .git/config`

> To create a global alias so we can use it with all of our repos : `git config --global alias.gl 'log --oneline --decorate --graph --all'` so now you can run it using `git gl` and it will run all that long command.

> To see your global git configuration : `cat ~/.gitconfig`


## Rebase

### A Merge Alternative :

> Rather than creating a merge commit it moves the feature branch and puts it at the end of the main branch that you wanted to merge the changes.

> If you want to rebase a feature branch on top of the main branch, git will go through each commit since the common ancestor works out the difference and replay it on top of the main branch, so it finds the first diff and replays it on the main branch creating a new commit and continues this way through each commit in your main branch when it is finished with all the commits it moves the HEAD (current location) from the feature branch on the end of the new commits on the main branch that is created.

> All the commits moved from feature branch to the main branch are entirely new commits, because of that fact you are rewriting the history so the feature branch commits no longer exist and they are no longer accessible.

> Example :

> You can go on the branch that you are working on `git checkout [ABranch]` then we can run `git rebase [BBranch]` so that means we want to add the code from [ABranch] on the end of the branch [BBranch], it can happen that we might get a merge conflict so we can take a look at a file generated to see the differences `cat .git/rebase-apply/patch` after that we can open the mergetool using `git mergetool` to fix the merge conflict, but there is a difference from the normal merge where you go into  [BBranch] and then merge the other [ABranch] into it, however, when you do a rebase these positions are switched where you go to the [ABranch] and put all its changes at the end of the [BBranch].

> After fixing the merge conflict we will apply the changes but that will leave a file that has the merge conflict and we can remove that using `rm [fileName].[fileExtension].orig` and after that, we run `git rebase --continue` but it will not let you because you have no changes you are on [ABranch] that is rebased in [BBranch] so instead we run `git rebase --skip` witch will discard that commit and put you onto the next commit if there are more commits.


### Rewriting History :

> Using the interactive rebase you can go to your git repository and reorder, delete, edit commits, or even squash multiple commits into a single commit.

> If you do rebase in a remote repository make sure that everyone is in agreement before so everybody gets the rebased branch, but as a general rule don't rebase something that is shared in a remote repository.

> Example :

> You go to the branch that has the changes `git checkout [branchName]` than using `git gl` we can see all our commits in a graphical way and there we find the parent commit and take its hash code so we can interactively rebase the commits, to do that we use `git rebase -i [parentBranchHash]` and that will put us into a file which will give us the opportunity to modify our commits in the VIM editor, to cut a line we type `dd`, and to paste it where the cursor is pres `p` after you finish editing the lines you type `:wq` to save and quit.

> To squash multiple commits into one we use the same command `git rebase -i [parentBranchHash]` and then we go to the row that we want to squash type `cw` and in there type `squash` into `pick` and then press the `esc` button and do the same for other rows you want to squash and after you finish editing the lines you type `:wq` to save and quit and that will put you into another editor were you need to create a commit message that will represent all the squashed commits, so we need to delete everything `dG` and then write your message after you finish adding your message you type `:wq` to save and quit, and then the rebase will complete.


## Gitignore

> There are three ways to ignore files :
> 1. Tell Git to pretend that there are no more changes to a specific file, and you will be unable to commit it because there will be no changes.
> 2. Remove the file from the Git index and stop tracking it.
> 3. Remove all traces of that file from the entire git repository history.

> You can add a file to be ignored by git using `echo "[fileName]*" > .gitignore` and then add it to the staging area `git add .gitignore` and commit the changes `git commit -m "[yourMessage]"` then add some content into that file using `echo "[text]" > [fileName]` and if we run `git status` we will see that git has traced that file so it will notify us that there is a change in that file, so we can tell Git that this file will never change using `git update-index --assume-unchanged [fileName]` command, this will tell Git that whatever happens to this file I want you to assume it did not change.

> To see all the files that Git assumes will never change you can run `git ls-files -v | grep '^[[:lower:]]'`

> If you decide that you want to start tracking it again you write the following command:  `git update-index --no-assume-unchanged [fileName]`

> Another way to stop tracking a file is to mark it as removed but in order to not lose that file we run  `git rm --cached [fileName]` to keep it in the working directory but update the staging area to see it as a deleted file, so if we run `git status` we will see that the [fileName] is marked as deleted then we can commit the changes `git commit -m "[yourMessage]"`then you can move to another branch using `git checkout [branchName]` command and if we see the content of the ignored file using `cat [fileName]` the file content stays the same. 


## Cherry Picking

> Allows you to select a commit from anywhere in the repo and add it to your current branch.

> You can run `git gl` to see the logs and locate the hash of the commit that you want to incorporate into your current branch, so to do that you run the `git cherry-pick [hash]` command which will add that commit to your branch.


## Filter Branch

> Allows you to update the repo making it look like any mistakes of the past never even happened.

> WARNING: Using Filter Branch alters the history of the repository, so you can not alter the history of a branch in a repository that has already been shared or at least not without the agreement of all the people that you have shared that branch with.

> You should use Filter Branch for branches that are local to you before you share them with other people.

> If you by mistake committed a secret file you can use Filter Branch to change that.

> Filter Branch allows you to alter the history programmatically, it takes each of the commits in the history and applies a filter to them.

> You can go and see the content of a 'secret file' using `cat [fileName]` and after that, you can see the commits that you have added to that file using `git gl -- [fileName]` command and if you want to see a more detailed content of what each commit consists of you type `git log -p -- [fileName]` command.

> Filters for Filter Branch :
> 1. Tree filter : this checks out each commit in turn run the script to make the changes that you want to make and rechecks them in. ( It is a slow approach )
> 2. Index filter : Instead of checking out into the working directory it just set up the staging area, and with that, we can use the cached option to be able to remove a file from an index using this command `git filter-branch --index-filter 'git rm --cached --ignore-unmatch -- [SecretFile]' --prune-empty -f HEAD`, it will go through and changes each of those staging areas and if a commit is empty it will discard it.
> 3. Environment filter : allows you to specify environment variables, git uses environment variables for all kinds of things including the committer name and email, so you can use this to completely rewrite the committer name for all of the commits.

> To see all the commits that are created by each user in a git remote repository : `git shortlog`

> To change the name of a committer you can type `git filter-branch -f --commit-filter '[bashScript]' HEAD`

```
if [ "$GIT_AUTHOR_NAME" = "[authorName]" ];
then 
 GIT_AUTHOR_NAME = "[newAuthorName]";
 GIT_AUTHOR_EMAIL = "[newAuthorEmail]";
 git commit-tree "$@";
else 
 git commit-tree "$@";
fi
```

## Undo

> There are a lot of different options of Undo

> The first option is Reset witch is very similar to checkout which when it is used it moves the HEAD on to the branch that we are checking out `git checkout [branchName]` or on a specific commit if we specify its hash by running `git checkout [hash]` command witch will move the HEAD to that commit.

> Reset it moves the HEAD and it also moves the reference that you are currently on and it comes in three ways :
> 1. Soft : will leave the working directory in the staging area as they were and moves the reference to the specified commit.
> 2. Mix : leaves the working directory as it is but resets the staging area and the index.
> 3. Hard : resets both the working directory and the staging area to match exactly the commit that you specified.

> If we add changes into a file and add it to the staging area using `git add [fileName]` we can unstage it using `git reset --mixed HEAD` and that will unstage the changes made in the current branch, but if we instead do `git reset --hard HEAD` that will clear the staging area and the working directory.

> In the previous example, we used HEAD as a reference but it can be anything like a Hash, Branch, Tag name, or you can use relative references like the last commit using `git reset --hard HEAD^` that will reset the HEAD by one commit.

> If you discard a commit that you wanted to keep you can use the 'reflog' which is the git built-in undo stack, it records every operation that mutates the state that you use in your git repo so it allows you to step back through the undo stack.

> We can run `git reflog` and you see the stack of all of the changes that you have been making inside your git repository, so to return the previous commit you can run `git checkout HEAD@{1}` which will put us in a detached head state, where HEAD is on its own away from 'main' and it has no branch referring to it, but we get the commit back, so to keep that commit you need to create a temporary branch `git checkout -b temp` and it will automatically contain the commit that we got back then we can go back to the main branch `git checkout main` and take a look using `git reflog` we will see that those changes will be persisted so if we want to go back before we deleted that commit you can type `git reset --hard HEAD@{[commitNumberBeforeDeletion]}` and then we can delete the temporary branch using `git branch -d temp`.

> You can not change history if you shared it with other people, discarding a commit does that where you discard the commit so you are changing history and you can't do that if you shared that with other people.

> You can use Revert to revert a commit that is shared in a repo so you can run `git revert [commitHash]` which will create a new commit at the end of the branch that is the exact opposite of the previous commit and then you can share that with the world.

> Use `git revert HEAD` to revert the most recent commit, which will generate a commit message for you and revert that commit, if you then want to revert that commit you can run again `git revert HEAD` witch will create a new commit message and revert the last revert.

> EXAMPLE :

> You can create a new branch using `git checkout -b myBranch` and in there create a text file using `touch myFile.txt`, then put that new file into the staging area using `git add myFile.txt` and commit it `git commit -m "[message]"`. Now if we switch back to main using `git checkout main` and delete the newly created branch with its commit using `git branch -D myBranch`, now if we see the reflog using `git reflog` we can se where that file was added so we can then run `git checkout HEAD@{[position]}` which will put us on a detached HEAD but at the point where we checked in that file, so now we need to create a new temporary branch using `git checkout -b temp` and then we can check out the log using `git gl` and we can see that we are back with the branch that we deleted.


## GITK

> It is a cross-platform UI library and you use GITK to visualize the repository and GIT-GUI to prepare your commits.

> They are both installed by default when you install GIT so we have them already, they are cross-platform and are for simple functionality like visualizing your repo and preparing your commits.

> To start GITK you type at the command line `gitk` if you are using macOS and it is not installed you can type `brew install git-gui`.

> You go to the main branch of your repo and you type `gitk` and it will open it.

> At the top left is the tree, then the committer and the commit time for the other two columns at the top.
> You can select each commit at it will load that commit in the lower window.
> You can suspend it using the `ctrl+Z` and then put it in the background using `bg`. 
> Or you can start it in the background directly using `gitk &`.

> To commit the changes that you have made you go to 'File>Start git gui' and this will show you the changes that you have made and will let you create a commit.
