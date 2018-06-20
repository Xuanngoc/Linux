# Linux
# System info
---
## Linux release and system info 
Some useful commands.

  - Linux release and distribution

```
aa32007@a32007:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"
NAME="Ubuntu"
VERSION="16.04.3 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.3 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial
```

  - Kernel version 
``` 
aa32007@a32007:~$ uname -r
4.13.0-45-generic

```

  - Memory Info
```
aa32007@a32007:~$ head /proc/meminfo
MemTotal:        3943020 kB
MemFree:          199220 kB
MemAvailable:     921232 kB
Buffers:           78492 kB
Cached:          1214064 kB
SwapCached:          740 kB
Active:          2547188 kB
Inactive:         931332 kB
Active(anon):    2077528 kB
Inactive(anon):   526976 kB

```  

  - File system 
 ```
 aa32007@a32007:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1,9G     0  1,9G   0% /dev
tmpfs           386M   12M  374M   3% /run
/dev/sda8       197G   29G  158G  16% /
tmpfs           1,9G   25M  1,9G   2% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
/dev/sda2        96M   29M   68M  30% /boot/efi
tmpfs           386M   76K  385M   1% /run/user/1000
 ``` 

  - Count the number of CPU
```
aa32007@a32007:~$ cat /proc/cpuinfo | grep model | uniq -c
      1 model		: 69
      1 model name	: Intel(R) Core(TM) i5-4310U CPU @ 2.00GHz
      1 model		: 69
      1 model name	: Intel(R) Core(TM) i5-4310U CPU @ 2.00GHz
      1 model		: 69
      1 model name	: Intel(R) Core(TM) i5-4310U CPU @ 2.00GHz
      1 model		: 69
      1 model name	: Intel(R) Core(TM) i5-4310U CPU @ 2.00GHz

```

## The proc Filesystem 
The ``/proc`` filesystem contains virtual files that exist only in memory.
Some important files in ``/proc`` are:
```
/proc/cpuinfo
/proc/interrupts
/proc/meminfo
/proc/mounts
/proc/partitions
/proc/version
/proc/<process-id-#>
/proc/sys
```

## Hostname
The hostname identifies the machine within the domain.
```
aa32007@a32007:~$ cat /etc/hostname 
a32007
```

Set a new host name.
```
hostname NEW_NAME
```

Use the ``hostnamectl`` utility to get and set the hostname.
```
aa32007@a32007:~$ hostnamectl 
   Static hostname: a32007
Transient hostname: ouanngoc
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: 89f73e2f3956433594e7adcf70b0317a
           Boot ID: 28db86597e4b43919e3c9dbd2003a537
  Operating System: Ubuntu 16.04.3 LTS
            Kernel: Linux 4.13.0-45-generic
      Architecture: x86-64
```






