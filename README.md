# Linux
----
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
    - Soft link: ln -s file.txt file1.txt

---
---
# Working with files
## The file streams
    1. standard input or **stdin**
    2. standard output or **stdout**
    3. standard error or **stderr**
## Search for files
Wildcards can be used in search for a filename containing specific characters.

|Wildcards|Result|
|---------|-----------|
|?     |Matches any single character|
|*     |Matches any string of characters|
|[set] |Matches any character not in the set of characters|
|[!set]|Matches any character not in the set of characters|

The ``locate``.

The ``find``:
```
    - Finding based on time:
        ```
        $ find / -ctime 3
        ```
    - Finding based on sizes:
        ```
        $ find / -size +10M
        ```    
```

## Manage files
Use the following utilities to view files:

|Command|Usage|
|:-------|-----------|
|cat  |Used for viewing files that are not very long|
|tac  |Used to look at a file backwards, starting with the last line|
|less |Used to view larger files because it is a paging program; it pauses at each screenful of text, provides scroll-back capabilities, and lets you search and navigate within the file.|
|tail |Used to print the last 10 lines of a file by default. You can change the number of lines by doing -n 15 or just -15 if you wanted to look at the last 15 lines instead of the default|
|head |The opposite of tail; by default it prints the first 10 lines of a file|

The ``touch`` command is often used to set or update the access, change, and modify times of files. By default it resets a file's time stamp to match the current time.
However, you can also __create__ an empty file.

The ``mkdir`` command is used to create a directory. Removing a directory is simply done with ``rmdir`` command. The directory must be __empty__ or it will fail.

## Compare files 
The ``diff`` command is used to compare files and directories.
For instance:
```
$  cat file2.txt
amor, ch'a nullo amato amar perdona,
mi prese del costui piacer si forte,
che, come vedi, ancor non m'abbandona.
$ 
$ diff  file1.txt file2.txt
< Amor, ch'a nullo amato amar perdona,
< Mi prese del costui piacer si forte,
< Che, come vedi, ancor non m'abbandona.
---
> amor, ch'a nullo amato amar perdona,
> mi prese del costui piacer si forte,
> che, come vedi, ancor non m'abbandona.
$ 
$ diff -c file1.txt file2.txt
*** file1.txt   2015-02-17 16:10:03.781804799 +0100
--- file2.txt   2015-02-17 16:13:41.059088459 +0100
***************
! Amor, ch'a nullo amato amar perdona,
! Mi prese del costui piacer si forte,
! Che, come vedi, ancor non m'abbandona.
--- 1,3 ----
! amor, ch'a nullo amato amar perdona,
! mi prese del costui piacer si forte,
! che, come vedi, ancor non m'abbandona.
$ 
$  diff -i file1.txt file2.txt
$ 
```
## The file utility 
The ``file`` to check  the contents and certain characteristics to determine whether the files are plain text, shared libraries, executable programs, scripts, or something else. 

