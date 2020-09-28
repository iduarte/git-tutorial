# Git and GitHub Workshop

## 28 September 2020

### A. Introduction
*NOTE: Please take notes (on paper -> then type them to file; or directly into a text file).*

#### 1. What is Git?
+ It is a distributed **version control system**.
+ It is a program, invented by Linus Torvalds (the "father" of Linux).
+ It allows keeping track of the changes in a project (i.e. a whole folder with several folders and/or files simultaneously -> it tacks changes in a collection of files simultaneously).
+ It allows the revision and restoring of files from previous versions.

#### 2. What is GitHub
+ It is a Git repository.
+ It is a distributed code-hosting platform for version control and collaboration.
+ Open source oriented.

#### 3. Files and Filesystems
+ **Drives** (permanent storage) -> physical system = Hardware
+ **Volume** is a partition of a drive that can contain a filesystem.
+ There are mainly two categories of file formats: **Binary** and **Text files**.
+ The Encoding of text files is a table that maps binary code to characters/symbols (letters, digits, punctuation, etc). E.g. ASCII, UTF8, UTF16, etc.  
+ In text files, 1 byte = 8 bits = 1 character.
+ This allows 2^8 different combinations (256 possible character combinations).  

#### 4. Preparation steps
+ Install Typora (or other markdown editor).
+ Install Git:
  ++ Windows
  ++ macOS (via XCode) -> already installed in mine (git version 2.24.3 Apple Git-128)
  ++ Linux (nothing to be done - it comes pre-installed) -> (git version 2.25.1)

### B. Git Mechanics
![Git Data Transport Commands](./git-mechanics.png)

+ Workspace is the folder of our project -> create one and put a markdown file in it.
+ After installing Git:

**1. Setting up the system (once per computer/project)**
```
git config --global user.name "I Duarte"
git config --global user.email "iduarte.scientist@gmail.com"

# Check that the global settings are correct
git config --global --list

# Note: We can have different settings for individual project:
git config --list

```

**2. Create a Git repository**

```
# 1. Navigate to the folder of my project
cd /path/to/my/project/folder

# 2. Create a Git repository (it creates a ".git" hidden folder that will allow the tracking of changes)
git init

# 3. Check the status of the newly created repository
git status

# 4. Add the markdown file to the list of files to be tracked for changes
git add file-name

# 4.1. Check again the status of the repository (make sure that the previous command worked)
git status

# 5. Commit the changes to the file selected by "git add" to the repository
git commit

# 5.1. This command opens the default Git text editor (in my Linux system is Vim)
 - Add the title of the message explaining the changes (<80 chars)
 - Add 2 new lines (press enter twice)
 - Add a longer description of the the commit/changes

  # To change the default Git text editor, run:
  git config --global core.editor neweditorname

```

**3. Interaction with your new Git Repository**

```
# Show all the commits done so far
git log

# Check if there are changes in the local file
git status

```

#### 1. Setting up the system

#### 2. Check that the global settings are correct

#### 3. Create a Git repository
