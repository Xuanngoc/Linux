# Linux
----


# Filesystem

## Filesystem Structure 
On many systems, including Linux, the filesystem is structured like a tree. The tree is usually portrayed as inverted, and starts at what is most often called the root directory, which marks the beginning of the hierarchical filesystem and is also denoted by /.
Some examples of filesystem types that Linux supports are:
1. **ext3**, **ext4**, **btrfs**, **xfs** (native Linux filesystems)
2. **vfat**, **ntfs**, **hfs** (filesystems from other operating systems) 

**Each filesystem resides on a hard disk partition**. Partitions help to organize the contents of disks according to the kind of data contained and how it is used. For example, important programs required to run the system are often kept on a separate partition than the one that contains files owned by regular users. In addition, temporary files created and destroyed during the normal operation of Linux are often located on a separate partition; in this way, using all available space on a particular partition may not fatally affect the normal operation of the system. 

Before you can start using a filesystem, you need to ``mount`` it to the filesystem tree at a **mountpoint**. Mount points are __usually__ empty directories. 

The ``mount`` command is used to attach a filesystem somewhere within the filesystem tree. Arguments include the ``device node`` and ``mount point``.

``` $ mount /dev/sda5 /mnt ```

The command ``df -Th`` (it stands for disk-free) will display information about mounted filesystems including type and usage statistics about currently used and available space.

## The home directories 
In any UNIX system, each user has his own home directory, usually placed under ``/home``. 
The ``/home`` directory is often mounted as a **separate filesystem** on its own partition, or even exported remotely on a network through NFS.

## The binary directories 
The ``/bin`` directory contains executable binaries.
The ``/sbin`` directory is used for essential binaries related to system administration, such as ifconfig and shutdown.

## The device directory
 The ``/dev`` directory contains device nodes, a type of pseudo-file used by most hardware and software devices, __except__ for network devices. 
 The ``udev``, which creates and manages device nodes on Linux.
 The ``/dev`` is empty on the disk partition when it isn't mounted but it contains entries which are created by ``/udev``.

 ## The variable directory
 
The ``/var`` directory contains files that are expected to change in size and content as the system is running.
Such as the entries in the following directories:
   + System log files: ``/var/log``
   + Packages files: ``/var/lib``
   + Print queues: ``/var/spool``
   + Temp files: ``/var/tmp``
   + FTP home directory: ``/var/ftp``
   +  Web Server directory: ``/var/www``
## The system configuration directory 
The ``/etc`` directory is the home for system configuration files.

## The boot directory 
The ``/boot`` directory contains the few essential files needed to boot the system. 

## The libraries directory 
The ``/lib`` contains libraries (common code shared by applications and needed for them to run) for the essential programs in ``/bin`` and ``/sbin`` folders. 

## Additional directories 
|Directory|Usage|
|:---------:|-----|
| /opt | Optional application software packages |
| /sys | Virtual pseudo-filesystem giving information about the system and the hardware. Can be used to alter system parameters and for debugging purposes. |
| /srv | Site-specific data served up by the system. Seldom used. |
| /tmp | Temporary files; on some distributions these files are erased across a reboot |
| /media | It is typically located where removable media, such as CDs, DVDs and USB drives are mounted. Unless configuration prohibits it, Linux automatically mounts the removable media in this directory when they are detected. |
| /usr | Multi-user applications, utilities and data |
| /usr/include | Header files used to compile applications |
| /usr/lib | Libraries for binary programs |
| /usr/lib64 | 64bit Libraries for binary programs |
| /usr/share | Shared data used by applications, generally architecture-independent |
| /usr/src | Source code, usually for the Linux kernel |
| /usr/local | Data and programs specific to the local machine. |





