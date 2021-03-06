# Git: Guide to your first pull request
## Table of contents
1. Getting started  
2. Git init, git add, git commit, git push  
3. Remotes, branches
4. How the graph is changing over commits
5. Fork, pull request

## 1. Getting started
First thing first, we need Git installed on our local machine. This can be simply 
done by  
[executing git install runfile on your local machine from the official website](https://git-scm.com/downloads),  
or you can just directly install the package using builtin package manager if you're running linux-based OS:
```bash
# Ubuntu distro
$ sudo apt-get install git 

# RPM distio(Fedora, CentOS ..)
$ sudo yum install git

# In MacOS, brew has to be installed first.
$ brew install git 
```
There are many different GUI-based client tools out there for committing and browsing git commits, but I strongly recommend beginners to start with 
the commnad-line interface that comes with git scm.  
Note that if you're using Windows OS, you'll already have **git bash** executable after the installation is done.  
(See [how-to-install-git-bash-on-windows](http://www.techoism.com/how-to-install-git-bash-on-windows/) for more details.)  
Lastly, ensure that the ```git``` command works fine on your local machine:
```bash
$ git --help
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]
            ...
            ...
$ git --version
git version 2.17.0
```
Nice, now we're all set! 

## 2. Git init, git add, git commit, git push
### Git init
1. First let's make an empty directory, `myfolder/`  
2. cd into `myfolder/`,  
3. then we'll initialize this empty directory as a git repository, by typing `git init` command.
Now we'll call this git initialized directory as **local repository**

```bash
$ git init
Initialized empty Git repository in /Users/{your_path_to_myfolder}/myfolder/.git/

$ ls -al
total 0
drwxr-xr-x   3 sangsulee  staff   96 Oct 16 10:22 .
drwxr-xr-x   3 sangsulee  staff   96 Oct 16 10:04 ..
drwxr-xr-x  10 sangsulee  staff  320 Oct 16 10:22 .git/
```
We can notice that `.git/` directory has been created once we type the command `git init`. Git tracks all version histories 
of the local repository such as file changes, all commits done, or get other important user configurations
from the files reside in this`.git/` folder. Hence, it's not a really good idea to remove/modify them manually :).

### Git status
Now let's make some dummy files in our **local repository**.  
As a side note, we distinguishes the terms **local repositoy** and **remote repository**. We'll cover them again in later section.

```bash
# Create empty files
$ touch haha.txt hoho.txt 
```

Then we have directory tree looks like this:
```bash
# Directory tree
─── myfolder
    ├── .git/
    ├── haha.txt
    └── hoho.txt
```

Once the directory is initialized by `git init` command, all the file changes in the repository 
will be tracked by git system. As the command suggests, `git status` 
shows those changes of which file has been newly added, or changed(deleted) within the repository. Command results are shown as follows:
```bash
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        haha.txt
        hoho.txt

nothing added to commit but untracked files present (use "git add" to track)
```
Git system recognized two **untracked** files that we added before.

### Git add
Using `git add` command, current changes in directory can be partially, or entirly **staged** for commit.   
Let's say we only want haha.txt file to be staged:
```bash
# Add haha.txt to be staged for next commit
$ git add haha.txt

# Check status
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   haha.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        hoho.txt
```
Of course we can stage all the changes we've made at once, by giving `-A` option to `git add` command.

### Git commit
- `git commit` command saves all staged changes. 
- Git commit is a fundamental, unit component of the git workflow
- Staged chages will not be revealed to outside of local repository until it is committed and finally pushed to public repository.  
- Each commit contains the changes of the content, along with user's log message.  
- Once committed, it is normally not easy to revert a commit.  
- Commit is usually be represented as a single node in graph representation that flows in time order. 
```bash
$ git add -A
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   haha.txt
        new file:   hoho.txt


$ git commit -m "Add haha, hoho"
[master (root-commit) 8167612] Add haha, hoho
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 haha.txt
 create mode 100644 hoho.txt
```
We can specify our commit message inline with `-m` option like above, otherwise the default text editor will popped up for the commit message.  

### Git log
To check the commit log graph visually in command line, try:
```bash
# https://stackoverflow.com/questions/1057564/pretty-git-branch-graphs
$ git log --all --decorate --oneline --graph
* 8167612 (HEAD -> master) Add haha, hoho
(END)
```  

### Git push
Now we have the commits ready to be synchronized with other repository.  
target repository URL could be your own git server, or public/private github repository, or could be other URL that serves git.  
For this example, If you haven't sign up for Github yet, please do, then create an emtpy repository **without** the README.md file.
I just have created mine and named it 'myrepo'. Any name would be fine, we'll push our local changes to this **remote repository**.


```bash
# First add the remote 'myrepo' and make it point to your github repository.
$ git remote add myrepo https://github.com/{username}/{your-repo-name}

# Now push local commit(s) to remote repository.
$ git push myrepo master
```
That's it for this section! check your github repository to see if your local changes are applied. 

## Remotes, Branches(WIP)
- `origin`, is the name of the default **remote** that pointing the repository url you've cloned from. 
- `master`, is the name of the **branch** in the git repository.
## How the graph is changing over commits(WIP)
## Fork, Pull Request(WIP)





