# Basic commands
## Locating Applications
- ``which`` to find out exactly where the __file__ program resides on the filesystem
- ``whereis`` 

## Accessing Directories
|Command|Result|
|-------|-----------|
|cd 	|Change to your home directory|
|cd ..|Change to parent directory|
|cd - |Change to previous directory|
|cd /	|Changes your current directory to the root (/) directory|

## Exploring the Filesystem
|Command|Result|
|-------|-----------|
|ls 	  |List the contents of the present working directory|
|ls –a  |List all files including hidden files and directories|
|tree   |Displays a tree view of the filesystem|
|tree -d|Just list the directories and suppress listing file names|

## Hard and Symbolic
    - Hard link: ln file.txt file1.txt 
        + When you delete file.txt, file1 still working.
        + file.txt and file1.txt h referenced
    - Soft link: ln -s file.txt file1.txt
        + When you delete file1.txt, file1.txt is empty.
        +  file.txt and file1.txt haven't referenced.

---
