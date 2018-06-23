# Linux
# Processes 
---
## Linux processes

A __process__ is simply an instance of one or more related tasks (threads) executing on the same machine. It is __not__ the same as a program or a command.
Processes use many system resources, such as memory, CPU cycles, and peripheral devices such as printers and displays.

A terminal window, is a process that runs as long as needed. It allows users to execute programs and access resources in an interactive environment. 
Processes can be of different types according to the task being performed.

|Type|Description|
|--------|---------|
|Interactive |Need to be started by a user, either at a command line or through a graphical interface such as an icon or a menu selection.|
|Batch |Automatic processes which are scheduled from and then disconnected from the terminal. These tasks are queued and work on a FIFO (First In, First Out) basis.|
|Daemons|Server processes that run continuously. Many are launched during system startup and then wait for a user or system request indicating that their service is required.|
|Threads|Lightweight processes. These are tasks that run under the umbrella of a main process, sharing memory and other resources, but are scheduled and run by the system on an individual basis.|
|Kernel Threads|Kernel tasks that users neither start nor terminate and have _little_ control over. These may perform actions like moving a thread from one CPU to another, or making sure input/output operations to disk are completed.|

At any given time, many processes are running on the system. However, a CPU can actually accommodate __only one__ task at a time.

## Running processes 

The ``ps`` command provides information about currently running processes, keyed by PID.
 If you want a _repetitive_ update of this status, you can use the ``top`` command or commonly installed variants such as ``htop`` or ``atop`` from the command line. 

You can use the ``ps -u`` to display information of processes for a specified username.  The command ``ps -ef`` displays all the processes in the system in full detail.

```
aa32007@a32007:~$ ps -u
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
aa32007   4087  0.0  0.1  24320  4552 pts/0    Ss   09:25   0:00 bash
aa32007   4211  0.0  0.1  25328  5600 pts/2    Ss+  09:27   0:00 /bin/bash
aa32007  10224  0.0  0.0  38892  3492 pts/0    R+   16:17   0:00 ps -u

```
The ``pstree`` command displays the processes running on the system in the form of a _tree diagram_ showing the relationship between a process and its parent process and any other processes that it created.

To __terminate__ a process you can type ``kill -SIGKILL <pid>`` or ``kill -9 <pid>``. Note however, you can _only_ kill your own processes: those belonging to another user are off limits unless you are _root_.

A best alternative is to use ``top`` to get constant real-time updates (every two seconds by default). The ``top`` command clearly highlights which processes are consuming the most CPU cycles and memory.

```
top - 16:26:22 up  7:09,  1 user,  load average: 0,28, 0,46, 0,80
Tasks: 213 total,   2 running, 211 sleeping,   0 stopped,   0 zombie
%Cpu(s):  6,9 us,  2,1 sy,  0,0 ni, 90,2 id,  0,3 wa,  0,0 hi,  0,6 si,  0,0 st
KiB Mem :  3943020 total,   252180 free,  2600048 used,  1090792 buff/cache
KiB Swap:  4094972 total,  3898608 free,   196364 used.   752456 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                         
 8525 aa32007   20   0 2659340 522676 104480 S  18,9 13,3  16:25.86 chromium-browse                                                                 
  993 root      20   0  421928  83552  54856 R   5,6  2,1   5:54.46 Xorg                                                                            
 2029 aa32007   20   0 1248556  75636  32132 S   4,3  1,9   7:13.64 compiz                                                                          
 1988 aa32007    9 -11  576224   9124   6504 S   3,6  0,2   2:51.01 pulseaudio                                                                      
 2340 aa32007   20   0 3303644 564096  95508 S   3,3 14,3  11:39.66 chromium-browse
```

 + The first line of the ``top`` output displays a quick summary of what is happening in the system including:
 1. How long the system has been up
 2. How many users are logged on
 3. What is the load average

+ The second line of the ``top`` output displays the total number of processes, the number of running, sleeping, stopped and zombie processes.
 
 + The third line of the ``top`` output indicates how the CPU time is being divided between the users (__us__) and the kernel (__sy__) by displaying the percentage of CPU time used for each.

 + The fourth and fifth lines of the ``top`` output indicate memory usage, which is divided in two categories:
   1. Physical memory (RAM) – displayed on line 4.
   2. Swap space – displayed on line 5.
   3. Both categories display total memory, used memory, and free space.

+ Each line in the process list of the ``top`` output displays information about a process. By default, processes are ordered by highest CPU usage.

## Background and foreground processes

Linux supports background and foreground job processing. Foreground jobs run directly from the shell, and when one foreground job is running, other jobs need to wait for shell access until it is completed. This is fine when jobs complete quickly. But this can have an adverse effect if the current job is going to take a long time to complete. In such cases, you can run the job in the background and free the shell for other tasks. The background job will be executed at lower priority, which, in turn, will allow smooth execution of the interactive tasks, and you can type other commands in the terminal window while the background job is running. By default all jobs are executed in the foreground. 

## Scheduling processes 
The ``at`` utility program is used to execute any non-interactive command ``at`` a specified time. The ``at`` jobs is picked by the ``atd`` service.

The ``cron`` utility is a __time-based__ scheduling utility program. It can launch routine background jobs at specific times and or days on an on-going basis.

## Delaying processes 
Sometimes a command or job __must__ be delayed or suspended.

The ``sleep`` command suspends execution for at least the specified period of time, which can be given as the number of seconds (the default), minutes, hours or days. After that time has passed, the execution will resume.