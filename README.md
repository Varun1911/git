# Git and Github

*git* -> version control software  
*github* -> online service to host git  

[**Notes By Hitesh**]("https://docs.chaicode.com/youtube/chai-aur-git/welcome/")

## Git Terminologies + Basic Commands

To check version
```
git --version
```  
<br />

**Repository** - A collection of files and directories stored together. It can contain other files, folders, and even other repositories. You can think of a repository as a container that holds all your code.   
   
<br>

We can track a any repository and check we can run this command to check the current status of the repo.  
*NOTE* - We don't need to track the entire repo. We can track specific files and folders as well. 

```
git status
```
<br />

**Config**  
Whenever you checkpoint your changes, git will add some information about your such as your username and email to the commit. There is a git config file that stores all the settings that you have changed.  
There are some global settings and some repository specific settings.

Setting global user name and email

```
git config --global user.email "your-email@example.com"
git config --global user.name "Your Name"
```  
  
Setting local user name and email

```
git config user.email "your-email@example.com"
git config user.name "Your Name"
```

check your config settings:
```
git config --list
```
<br>

**Creating a Repository**  
Creating a repository is a process of creating a new folder on your system and initializing it as a git repository. It’s just regular folder to code your project, you are just asking git to track it.

```
git init
```
This adds a hidden `.git` folder to your project.


**Stage**  
Stage is a way to tell git to track a particular file or folder. You can use the following command to stage a file:

```
git add <file> <file2>
```

To stage all files
```
git add .
```

**Commit**  
We can see that the changes are now committed to the repository. The -m flag is used to add a message to the commit. Missing the -m flag will result in an action that opens your default settings editor
```
git commit -m "commit message"
```

We can add description to our commits like so : 

```
git commit -m "Title" -m "description"
```

We can also use the editor :
```
git commit
```
This will open up the editor and we we can add the title then leave a line and add the desctiption.

<br>

**Logs**  
This command will show you the history of your repository. It will show you all the commits that were made to the repository and info about the commit. You can use the `--oneline` flag to show only the commit message.
```
git log
git log --oneline
```
<br>

**Change Default Code Editor**

set to vscode
```
git config --global core.editor "code --wait"
```
<br>

**Git Ignore**  
Gitignore is a file that tells git which files and folders to ignore. It is a way to prevent git from tracking certain files or folders. You can create a gitignore file and add list of files and folders to ignore.


*NOTE* - since git does not track empty folders, we can add a `.gitkeep` file in them for git to allow tracking  
<br>

## Git Branches  
Branches are a way to work on different versions of a project at the same time. They allow you to create a separate line of development that can be worked on independently of the main branch. 

### HEAD in git  
The HEAD is a pointer to the current branch that you are working on. It points to the latest commit in the current branch. When you create a new branch, it is automatically set as the HEAD of that branch.

```
git branch
git branch bug-fix
git switch bug-fix
git log
git switch main
git switch -c dark-mode
git checkout orange-mode
git checkout -b new-branch
```

`git branch` - This command lists all the branches in the current repository.  
`git branch bug-fix` - This command creates a new branch called bug-fix.  
`git switch bug-fix` - This command switches to the bug-fix branch.  
`git log` - This command shows the commit history for the current branch.  
`git switch main` - This command switches to the main branch.  
`git switch -c dark-mode` - This command creates a new branch called dark-mode. the -c flag is used to create a new branch.  
`git checkout orange-mode` - This command switches to the orange-mode branch.  
`git checkout -b new-branch` - This command creates a new branch called new-brnach and switches to the new-branch branch.  


### Merging Branches
Merging is about bringing changes from one branch to another.
In Git we have two types of merges :  
   * Fast-Forward Merges (If branches have not diverged)
   * 3-Way Merges (if branches have diverged) 
<br><br>

#### Fast-forward merge
This one is easy as branch that you are trying to merge is usually ahead and there are no conflicts.

When you are done working on a branch, you can merge it back into the main branch. This is done using the following command:

```
git checkout main
git merge bug-fix
```

#### 3 Way merge  
In this type of merge, the main branch has additional commits that are not present in the `bug-fix` branch. Here git looks at 3 different commits [common ancestor of branches + tips of each branch] and combines the changes into one merge commit.

When you are done working on a branch, you can merge it back into the main branch. This is done using the following command:
```
git checkout main
git merge bug-fix
```
The difference is resolving the conflicts.  
You have to manually resolve the conflicts. Decide, what to keep and what to discard.


#### Rename a branch
```
git branch -m <old-branch-name> <new-branch-name>

git branch -m <new-branch-name>  
<!-- renames the current branch -->
```


#### Delete a branch
```
git branch -d <branch-name>
```

#### Abort Merge

Abort the merge when faced with conflicts to get back to the same state.
```
git merge --abort
```

## Diff, Stash and Tags

### Git diff
It is used to compare the changes made in one commit with the changes made in another commit. Git consider the changed versions of same file as two different files.  

Comparing Working Directory and Staging Area

```
git diff
```
<br>
Comparing Staging Area with Repository

```
git diff --staged
```
<br>
Comparing Two Branches

```
git diff <branch-name-one> <branch-name-two>
<!-- or -->
git diff branch-name-one..branch-name-two
```
<br>
Comparing Specific Commits

```
git diff <commit-hash-one> <commit-hash-two>
```

#### How to Read the Diff Output
* a/ –> the original file (before changes)
* b/ –> the updated file (after changes)
* --- –> marks the beginning of the original file
* +++ –> marks the beginning of the updated file
* @@ –> shows the line numbers and position of changes  


### Git Stash
Stash is a way to save your changes in a temporary location. It’s useful when switching branches without losing work. You can then come back to the file later and apply the changes.  
Conflicting changes will not allow you to switch branches without committing the changes.  
Stash is like a stack.
```
git stash
```

#### Naming the stash
```
git stash save "work in progress on X feature"
```
#### View the stash list
```
git stash list
```

#### Apply the Most Recent Stash
```
git stash apply
```

#### Apply Specific Stash
```
git stash apply stash@{0}
```

#### Applying and Drop a Stash
This will apply the stash and also remove it from the stash
```
git stash pop
```

#### Drop the stash
```
git stash drop
```

#### Applying stash to a specific branch
```
git stash apply stash@{0} <branch-name>
```


#### Clearing the stash
```
git stash clear
```

### Git Tags
Tags are a way to mark a specific point in your repository. They are useful when you want to remember a specific version of your code or when you want to refer to a specific commit. Tags are like sticky notes that you can attach to your commits.  

#### Creating a tag  
```
git tag <tag-name>  
```  

#### Create an annotated tag  
```
git tag -a <tag-name> -m "Release 1.0"  
```  

#### List all tags
```
git tag
```

#### Tagging a specific commit
```
git tag <tag-name> <commit-hash>
```


#### Push tags to remote repository
```
git push origin <tag-name>
```

<br><br>

## Useful Linus Commands
<!-- some basic linus commands -->
<table data-start="258" data-end="771" class="w-fit min-w-(--thread-content-width)"><thead data-start="258" data-end="304"><tr data-start="258" data-end="304"><th data-start="258" data-end="268" data-col-size="sm">Command</th><th data-start="268" data-end="282" data-col-size="md">Description</th><th data-start="282" data-end="304" data-col-size="sm">Windows Equivalent</th></tr></thead><tbody data-start="351" data-end="771"><tr data-start="351" data-end="393"><td data-start="351" data-end="358" data-col-size="sm"><code data-start="353" data-end="357">ls</code></td><td data-col-size="md" data-start="358" data-end="384">List directory contents</td><td data-col-size="sm" data-start="384" data-end="393"><code data-start="386" data-end="391">dir</code></td></tr><tr data-start="394" data-end="428"><td data-start="394" data-end="401" data-col-size="sm"><code data-start="396" data-end="400">cd</code></td><td data-start="401" data-end="420" data-col-size="md">Change directory</td><td data-col-size="sm" data-start="420" data-end="428"><code data-start="422" data-end="426">cd</code></td></tr><tr data-start="429" data-end="494"><td data-start="429" data-end="437" data-col-size="sm"><code data-start="431" data-end="436">pwd</code></td><td data-col-size="md" data-start="437" data-end="463">Print current directory</td><td data-col-size="sm" data-start="463" data-end="494"><code data-start="465" data-end="469">cd</code> (shows path in prompt)</td></tr><tr data-start="495" data-end="539"><td data-start="495" data-end="505" data-col-size="sm"><code data-start="497" data-end="504">mkdir</code></td><td data-col-size="md" data-start="505" data-end="528">Create new directory</td><td data-col-size="sm" data-start="528" data-end="539"><code data-start="530" data-end="537">mkdir</code></td></tr><tr data-start="540" data-end="618"><td data-start="540" data-end="547" data-col-size="sm"><code data-start="542" data-end="546">rm</code></td><td data-col-size="md" data-start="547" data-end="598">Delete files or directories (<code data-start="578" data-end="582">-r</code> for recursive)</td><td data-col-size="sm" data-start="598" data-end="618"><code data-start="600" data-end="605">del</code> or <code data-start="609" data-end="616">rmdir</code></td></tr><tr data-start="619" data-end="671"><td data-start="619" data-end="626" data-col-size="sm"><code data-start="621" data-end="625">cp</code></td><td data-col-size="md" data-start="626" data-end="651">Copy files/directories</td><td data-col-size="sm" data-start="651" data-end="671"><code data-start="653" data-end="659">copy</code> / <code data-start="662" data-end="669">xcopy</code></td></tr><tr data-start="672" data-end="712"><td data-start="672" data-end="679" data-col-size="sm"><code data-start="674" data-end="678">mv</code></td><td data-start="679" data-end="702" data-col-size="md">Move or rename files</td><td data-col-size="sm" data-start="702" data-end="712"><code data-start="704" data-end="710">move</code></td></tr><tr data-start="713" data-end="771"><td data-start="713" data-end="723" data-col-size="sm"><code data-start="715" data-end="722">touch</code></td><td data-col-size="md" data-start="723" data-end="746">Create an empty file</td><td data-col-size="sm" data-start="746" data-end="771"><code data-start="748" data-end="769">type nul &gt; file.txt</code></td></tr><tr data-start="904" data-end="964"><td data-start="904" data-end="921" data-col-size="sm"><code data-start="906" data-end="920">cat file.txt</code></td><td data-col-size="sm" data-start="921" data-end="945">Display file contents</td><td data-col-size="sm" data-start="945" data-end="964"><code data-start="947" data-end="962">type file.txt</code></td></tr></tbody></table>