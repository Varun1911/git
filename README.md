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


<!-- some basic linus commands -->