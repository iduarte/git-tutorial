# Git and GitHub Workshop

## Ramiro Magno | 28 September 2020
---
Notes from **Isabel Duarte | 28 September 2020**

### A. Introduction
*NOTE: Please take notes (on paper -> then type them to file; or directly in a text file).*

#### 1. What is Git?
+ It is a distributed **version control system**.
+ It is a program, developed by Linus Torvalds (the "father" of Linux).
+ It allows keeping track of the changes in a project (i.e. a whole folder with several folders and/or files simultaneously -> it tracks changes in a collection of files simultaneously).
+ It allows the revision and restoring of files from previous versions.

#### 2. What is GitHub
+ It is a Git repository.
+ It is a distributed code-hosting platform for version control and collaboration.
+ Open source oriented.

#### 3. Files and Filesystems
+ **Drives** (permanent storage) -> physical system = Hardware
+ **Volume** is a partition of a drive that can contain a filesystem.
+ There are mainly two categories of file formats: **Binary** and **Text** files.
+ The **Encoding** of text files is a table that **maps binary code to characters/symbols** (letters, digits, punctuation, etc). E.g. ASCII, UTF8, UTF16, etc.  
+ In text files, 1 byte = 8 bits = 1 character.
+ This allows 2^8 different combinations (256 possible characters).  

#### 4. Preparation steps
+ Install Typora (or other markdown editor).
+ Install Git:   
  - Windows (not applicable to me)   
  - macOS (via XCode) -> already installed in my macOS Catalina (git version 2.24.3 Apple Git-128)
  - Linux (nothing to be done - it comes pre-installed) -> (Ubuntu 20.04 -> git version 2.25.1)

### B. Git Mechanics
![Git Data Transport Commands](./git-mechanics.png)

### Using Git
+ Workspace is the folder of our project -> create one and put a markdown file in it.

#### 1. Setting up the system (once per computer/project)

+ **After installing Git, open a Terminal window** and type the following commands:

```
git config --global user.name "I Duarte"
git config --global user.email "iduarte.scientist@gmail.com"

# Check that the global settings are correct
git config --global --list

# Note: We can have different settings for individual projects:
git config --list

```

#### 2. Create a Git repository

```
# 1. In the terminal, navigate to the folder of my project
cd /path/to/my/project/folder

# 2. Create a Git repository (it creates a ".git" hidden folder
  # that will allow the tracking of changes)
git init

# 3. Check the status of the newly created repository
git status

# 4. Add the markdown file to the list of files to be tracked for changes
  # (i.e. select the file or files that we will be included
  # in the following commit command)
git add file-name

# 4.1. Check again the status of the repository
  # (make sure that the previous command worked)
git status

# 5. Commit the changes from the file selected by "git add" to the repository
git commit

   # 5.1. This command opens the default Git text editor
        # (in my Linux system is Vim)
 - Add the title of the message explaining the changes (<80 chars)
 - Add 2 new lines (press enter twice)
 - Add a longer description of the the commit/changes

# Note: To change the default Git text editor, run:
git config --global core.editor neweditorname

```

#### 3. Interaction with your new Git Repository

```
# Show all the commits done so far
git log

# Check if there are changes in the local file
git status

# See the differences between the local version and the last commit
git diff

# A gitignore file specifies intentionally untracked files
  # that Git should ignore
  - For this create a file named: ".gitignore" in the parent
    folder of the repository.

```

#### 4. Shortcuts and other useful commands

```
# Add the title of the text description associated
  # with the change immediately with the commit command
git commit -m "Some text describing the change"

# Add and commit more than one file simultaneously
git add file1 file2 file3 *.pdf
git commit -m "Added all pdf files plus changes in 3 files."

# Graphical User Interface (GUI) for Git
gitk

```

### C. Using GitHub Repositories

+ The greatest advantage of using a **remote Git repository**, such as **GitHub**, is that it greatly facilitates the collaboration on the same project.

#### Steps to put the local Git repository on GitHub
```
# 1.Create a new repository on GitHub (online).
# It is advisable to give it the same name as the local one.
  # Very importantly, do NOT create any additional files online,
  # such as a README or a Licence file, because these will make
  # the local and remote repositories incompatible (not easily
  # synchronizable).

# 2. Add the local repository to GitHub:
git remote add origin https://github.com/username/repositoryname

# 3. Check the status of the remote add (previous command)
git remote -v

# 4. Push the local repository to the remote GitHub repository,
# along with necessary commits and objects.
# (It synchronizes the local with the remote repository).
git push origin master

# 5. Clone a remote repository
git clone github.com/repositoryname

```

### D. TL;DR | For the impatient | Short recap

Minimum set of commands required to setup a Git version control of a workspace/project.

#### 1. Create a local Git repository & Remote GitHub repository

**Required only once per project/folder**

```
# Open a Terminal and navigate to the project folder
cd /path/to/my/project/folder

# 1.1. Create a Local Git
git init

# 1.2. ONLINE | Create a GitHub repository (no README or any other files)

# 1.3. Link the local Git (myGitName) to the Remote GitHub
git remote add myGitName https://github.com/username/repositoryname

```

#### 2. Order of routine commands for fast Git version control

```
# 1. Navigate to the directory where the local repository is set
cd /path/to/my/project/folder

# 2. Check the status of the changes
  # (which files have been modified)
git status

# 3. Add the files that have been modified
git add filenames

# 4. Commit the changes to the local repository
git commit -m "Describe the changes made."

# 5. Check the status/names of the remote repositories already set
git remote -v

# 6. Push the local repository (origin) to the remote GitHub (master)
git push origin master  

#################################################################
# Other important commands:
 # Check the history of commits
git log

 # Check the differences between local files and last commit
git diff

 # Graphical User Interface to see the local Git
 gitk

# More about git remote commands
git remote -v                  # Lists all the remotes that are configured
git remote add [name] [url]    # Used to add a new remote
git remote remove [name]       # Removes a remote. Does not affect the remote repo; just removes the link to it from the local repo.
git remote set-url [name] [newurl]    # Changes the URL that is associated with the remote.
git remote rename [oldname] [newname] # Changes the local alias by which a remote is known - its local name.  
```

#### 3. Basic Collaborative Workflow

```
# 1. Update your local repo
git pull origin master

# 2. Make your changes and stage them
git add

# 3. Commit your changes
git commit -m

# 4. Upload the changes to GitHub
git push origin master

```

#### 4. Useful Git commands

```
# Reconcile histories between local and remote branches 
git config pull.rebase false  # merge
git config pull.rebase true   # rebase
git config pull.ff only       # fast-forward only
or
git pull --rebase origin master # one time only option

# About branches
git branch                    # list local branches (star indicates the current working branch)
git branch -a                 # list all local and remote branches
git branch <new_branch_name>  # Create a new branch

# Go to previous versions of the code (the commit_hash is given by the `git log` command)
git checkout <commit_hash>

# Go back to the latest commit (newest version of the project code)
git checkout master

# Merging branches
git merge <branch_name_to_merge_into_currrent_working_branch>

```

### Setting up Git to my computer & Adding keys to GitHub

Good links with instructions:

[Set up Git](https://docs.github.com/en/get-started/quickstart/set-up-git)
[SSH Keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

[SSH keys | Simple Instructions](https://kbroman.org/github_tutorial/pages/first_time.html)




_END_
