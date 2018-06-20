# File permissions 
---
In Linux and other UNIX operating systems, every file is associated with a user who is the owner. Every file is also associated with a group which has an interest in the file and certain rights, or permissions: read, write, and execute.

|Command|Result|
|-------|-----------|
|chown|Used to change user ownership of a file or directory|
|chgrp|Used to change group ownership|
|chmod|Used to change the permissions on the file|

Files have three kinds of permissions: read (r), write (w), execute (x). These are generally represented as in the following order **rwx**.
These permissions affect three groups of owners: user (u), group (g), and others (o).


There are a number of different ways to use the ``chmod`` command. For instance, to give the owner execute permission:
```
$ ls -l test1
-rw-rw-r-- 1 joy caldera 1601 Mar 9 15:04 test1
$ chmod u+x test1
$ ls -l test1
-rwxrw-r-- 1 joy caldera 1601 Mar 9 15:04 test1
```



