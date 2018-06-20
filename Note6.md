# Linux 
---
# Data Backup

### Backup the data
The ``rsync`` command is used to synchronize entire directory trees.
Basically, it copies file as the ``cp`` command does. In addition, ``rsync`` checks if the file being copied already exists. If the file exists and there is no change in size or modification time, rsync will avoid an unnecessary copy and save time.
 ## Compress the data
File data is often compressed to save disk space and reduce the time it takes to transmit files over networks. Linux uses a number of methods to perform this compression.

|Command|Usage|
|-------|-----------|
|gzip 	|The most frequently used Linux compression utility|
|bzip2  |Produces files significantly smaller than those produced by gzip|
|xz     |The most space efficient compression utility used in Linux. It is now used by kernel.org to store archives of the Linux kernel.|
|zip    |Is often required to examine and decompress archives from other operating systems|

These techniques vary in the efficiency of the compression and time.

## Archiving data


The ``tar`` command allows you to __create__ or __extract__ files from an archive file, often called a tarball. At the same time you can optionally compress while creating the archive, and decompress while extracting its contents.

Some examples of the use of ``tar``:

|Command|Usage|
|-------|-----------|
|tar xvf mydir.tar|Extract all the files in mydir.tar into the mydir directory|
|tar zcvf mydir.tar.gz mydir|Create the archive and compress with gzip|
|tar jcvf mydir.tar.bz2 mydir|Create the archive and compress with bz2|
|tar xvf mydir.tar.gz|Extract all the files in mydir.tar.gz into the mydir directory.|
|tar cvf  mydir.tar|show the content into the mydir directory|

## Copying disks 
The ``dd`` command is very useful for making copies of raw disk space.

To use ``dd`` to make a copy of one disk onto another, __deleting everything__ that previously existed on the second disk, use:
```
dd if=/dev/sda of=/dev/sdb
````
