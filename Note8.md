# Linux
# Swap memory 
---
## Linux swap memory 

Linux divides RAM into memory areas called pages.
The swapping is the process by which a memory page is copied into a preconfigured hard disk space, called space swap , to release from memory. 

Swapping is  necessary for two important reasons:
   1. First, when the system requires more memory than the one physically available, the kernel moves the less used pages into the swap space and grants the use of ram memory to the current application (process) that at that time requires memory.
    2. Secondly, a significant number of pages used by an application during its startup phase can only be used for system initialization and then never used again. 

The system can then use swaps on those pages and free up memory for other applications or even disk caches.
The access to the disk is tens of thousands of times **slower** than the memory ram. 

Linux has two forms of swap space: the **swap partition** and the **swap file**.
- The swap partition is an independent section of the hard disk, used exclusively for the swap, no one else can reside there.
- The swap file is a special file that resides in the filesystem between the system and data files.
To see how it is done and where the swap space you have is located, you use the command ``swapon`` :
```
aa32007@xuanngoc:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda9                              	partition	4094972	300736	-1
```

## Swap dimensioning 
| Amount of RAM in the system | Recommended swap space | Recommended swap space if allowing for hibernation |
|:------------------------------|------------------------|----------------------------|
|< 2GB| 2 times the amount of RAM | 3 times the mount of RAM|
|>2 GB && < 8GB> | Equal to the amount of RAM | 2 times the amount of RAM |
| > 8GB && <64GB | 0.5 times the amount of RAM | 1.5 times the amount of RAM |
| > 64 GB | 4GB of swap space | No extra space needed |

## Add a swap area as a file 

