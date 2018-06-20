# Linux 
# Package Management Systems

The core parts of a Linux distribution and most of its add-on software are installed via the Package Management System.
Each package contains the files and other instructions needed to make one software component work on the system.

#### **Package Management Systems**

|High Level Tool|Low Level Tool|Family|
|---------------|--------------|------|
|apt-get|dpkg|Debian|
|zypper|rpm|SUSE|
|yum|rpm|Red Hat|

Both package management systems provide two tool levels:
 + A __low-level__ tool (such as **dpkg** or **rpm**), takes care of the details of unpacking individual packages, running scripts, getting the software installed correctly.
 + A __high-level__ tool (such as **apt-get**, **yum**, or **zypper**) works with groups of packages, downloads packages from the vendor, and figures out dependencies. Most of the time users need work only with the high-level tool, which will take care of calling the low-level tool as needed.

 |Operation|RPM|Debian|
|---------|-----------|-----------|
|Install a package|rpm –i foo.rpm|dpkg --install foo.deb|
|Install a package with dependencies from repository|yum install foo|apt-get install foo|
|Remove a package|rpm –e foo.rpm|dpkg --remove foo.deb|
|Remove a package and dependencies using repository|yum remove foo|apt-get remove foo|
|Update package to a newer version|rpm –U foo.rpm|dpkg --install foo.deb|
|Update package using repository and resolving dependencies|yum update foo|apt-get upgrade foo|
|Update entire system|yum update|apt-get dist-upgrade|
|Show all installed packages|yum list installed|dpkg --list|
|Get information about an installed package including files|rpm –qil foo|dpkg --listfiles foo|
|Show available package with "foo" in name|yum list foo|apt-cache search foo|
|Show all available packages|yum list|apt-cache dumpavail|
|Show packages a file belong to|rpm –qf file|dpkg --search file|