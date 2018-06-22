# Linux
# User envinronment  
 ---
 ## Users and Group 

 Linux is a __multiuser__ operating system where more than one user can log on at the same time.
 The `who` command lists the currently logged-on users.
 ```
 aa32007@xuanngoc:~$ who -a
           system boot  2018-06-20 16:41
           run-level 5  2018-06-20 16:42
LOGIN      tty1         2018-06-20 16:42              1147 id=tty1
aa32007  + tty7         2018-06-20 16:42  old         1200 (:0)

 ```
 To identify the current user, use the `whoami` command.
 ```
aa32007@xuanngoc:~$ whoami
aa32007
 ```
Linux uses groups for organizing users. Groups are collections of accounts with certain _shared permission_. Permissions on various files and directories can be _modified_ at the group level.

Only the root user can add and remove users and groups.
Adding a new user is done with the ``useradd`` command: 
```
aa32007@xuanngoc:~$ useradd pencil
```
Removing an existing user is done with the ``userdel`` command.
```
aa32007@xuanngoc:~$ sudo deluser pencil
sudo: unable to resolve host xuanngoc
Removing user `pencil' ...
Warning: group `pencil' has no more members.
Done.

```
The command ``id`` with no argument gives information about the current user. If given the name of another user as an _argument_, ``id`` will report information about that other user.
```
aa32007@xuanngoc:~$ id
uid=1000(aa32007) gid=1000(aa32007) groups=1000(aa32007),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare)
```
Use the ``passwd`` command to change the password for the user.
```
Changing password for aa32007.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password:
passwd: password updated successfully

```
Adding a new group is done with the ``groupadd`` command and removed with the ``groupdel`` command.

```
aa32007@xuanngoc:~$ sudo groupadd  newpen
aa32007@xuanngoc:~$ sudo groupdel newpen
```

## The root user

The __root__ account is very _powerful_ and has _full access_ to the system. Other operating systems often call this the __administrator__ account; in Linux it is often called the __superuser__ account.

You can use the ``sudo`` feature to assign more limited privileges to standard user accounts:
  1. on only a temporary basis.
  2. only for a specific subset of commands.

## Startup Files
In Linux, the command shell program, generally _bash_ uses one or more startup files to configure the environment.

 The startup files can do anything the user would like to do in every command shell, such as:
 + Customizing the user's prompt
 + Defining command-line shortcuts and aliases
 + Setting the default text editor
 + Setting the path for where to find executable programs

 ## Environment variables 
The environment variables are simply named quantities that have specific values and are understood by the command shell, such as _bash_.
Some of these are pre-set by _the system_, and others are set by _the user_ either at the command line or within startup and other scripts.
There are a number of ways to view the values of currently __set__ environment variables. All the ``set``, ``env``, or ``export`` commands display the environment variables.
By default, variables created within a script are __only__ available to the current shell.All the child processes (sub-shells) will __not__ have access to values that have been set or modified.

 Allowing child processes to see the values, requires use of the export command.
|Task|Command|
|----|-------|
|Show the value of a specific variable|echo $SHELL|
|Export a new variable value|export VAR=value|
|Add a variable permanently|Add the line export VAR=value to ~/.bashrc|

The __HOME__ is an environment variable that _represents_ the home or login directory of the user. The ``cd`` command without arguments will change the current working directory to the value of ``HOME``. Note the tilde character (``~``) is often used as an _abbreviation_ for $HOME.
The __PATH__ environment variable is an _ordered_ list of directories which is scanned when a command is given to find the appropriate program or script to run.

The __PS__ environment variable (``Prompt Statement``) is used to _customize_ your prompt string in your terminal windows to _display_ the information you want.

## Command history 
The __bash__ keeps track of previously entered commands and statements in a history buffer.
To view the list of previously executed commands, you can use the ``history`` at the command line. ``` aa32007@a32007:~$ history
```
This information is stored in ``~/.bash_history`` file.
 ```
aa32007@a32007:~$ cat ~/.bash_history
```
Several associated environment variables can be used to get information about the history file.
|Variable|Usage|
|--------|-----|
|HISTFILE|stores the location of the history file|
|HISTFILESIZE|stores the maximum number of lines in the history file|
|HISTSIZE|stores the maximum number of lines in the history file for the current session |

The table below shows the syntax used to execute previously used commands

|Syntax|Usage|
|------|-----|
|!!|Execute the previous command|
|!|Start a history substitution|
|!$|Refer to the last argument in a line|
|!n|Refer to the n-th command line|
|!string|Refer to the most recent command starting with string|

## Creating Aliases
Customized commands can be created to modify the behavior of already existing ones by creating aliases.
The ``alias`` command with no arguments will list currently defined aliases.
```
aa32007@a32007:~$ alias
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
```













