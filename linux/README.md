# Linux

## Background
### Unix
* UNIX is an operating system since the 1960’s
* Unix is a [trademarked](www.unix.org) name.
* UNIX operating system is one that
  * conforms to a set of standards
  * is registered with the governing body of the trademark.
  * If any those two requirement is not met, it can only be called Unix 'like' OS.
* Active Unix OS:
  * Hewlett Packard(HP-UX)
  * IBM AIX
  * IBM z/OS
  * Oracle Solaris
  * Apple macOS

### Linux
* Linux is Unix "like" OS.
* Linux was created around 1990's
* Linux is a [trademarked](www.linuxmark.org) name.
* Linux is the name of the OS kernel, means Linux "based" OS.
* Active Linux OS:
  * Google Android
  * Oracle Linux
    * Red Hat Enterprise Linux
    * CentOS - It is based on Red Hat Enterprise Linux
    * Fedora
  * Ubuntu Linux
  * Debian Linux


## Basic Concepts

1. Kernel
* The kernel is the core of Unix or Unix "like" OS, used to communicate to the hardware.
* It has the following functions.
  - Multi-tasking
  - File reads and writes
  - Connectivity to networks and devices
  - Resource allocation

2. Shell
* Provides a command-line interface where the user can execute commands.
* It has the following functions.
  - Interprets the user commands
  - Passes the interpreted commands to the kernel
* famous shells
  - Bourne Shell(sh)
  - Bourne-Again Shell(bash), most used shell.
  - C Shell(csh)
  - Korn Shell(ksh)

3. Filesystem
* For Unix/Linux OS every thing is a file
* Types of file systems:
  - xfs : Default filesystem for many newer Linux distributions
  - ext4 : 4th extended filesystem (still used with many Linux distributions)
  - exFAT : Provides support for Microsoft’s exFAT (read + write)
  - NTFS : Provides support for Microsoft’s NTFS (read-only)
* The filesystem start at root does not has volume letter
* the directories/foldrs are files
* home directory ``~`` are for users
* the current folder shown before shell symbol, all its contain can be accessed without specify path. In short, ``./`` is ignored for file path.
* For file contain space use """ surround the whole path.
* Its important to remember that all Linux Operating systems are case sensitive
* linux system use forward slash ``/`` and the following sign for relative path.
  * ``.`` is the current directory
  * ``..`` is the previous directory
  * ``~`` is the home directory
  * ``*`` means all
* absolute path starts with ``/`` from root folder.
* In Linux, files that start with a dot ( . ) are considered hidden files
* Linux System has the following files structure.
  * / - the root of the file system
  * /var – variable files or files that vary frequently
  * /root/Downloads – downloads directory for the root user
  * /etc – contains system wide configuration files
  * /etc/sysconfig/iptables – the path to the iptables configuration file
  * /home – contains all other user home directories
  * /home/username – the username user home directory
  * /usr – the ‘user file system’  contains non-system critical files and binary (executable) files
  * /bin and /sbin – contain system binary files
* drag file into the terminal to get its directory.
* files permission can be represented by ``-`` or ``d`` followed by three groups of three letter.s
  * ``-`` means file, ``d`` means directories.
  * First group is permission for users, second is for Groups, third is for others.
  * In each group ``r`` is read permission, ``w`` is write permission, ``x`` is execute permission, ``-`` is no permission.
  * A permission code can be calculated, using ``r``=4, ``w``=2, ``x``=1, ``-``=0, and and them together.
  * For example, ``400`` means only user has read permission, so the file is private.

## Commands
* Command options full name are after ``--``. can use the first letter, can combine the letter after one common ``-``.
* Large command output press ``Q`` to quit. enter ``/searchContent`` to search.
* Both the ``| more`` and the ``| less`` command provide paging functionality in a command line environment. For example ``help | less``. shows output that can be control using up and down arrow.
* ``| grep <filterString>`` Grep will return only those lines in the file that contain the supplied string. For Example ``cat /etc/man.config | grep MANPATH``
* ``startx`` start X Windows System GUI.
* ``shutdown –h now``  shutdown immediately.
* ``shutdown –r now`` restart immediately.
* ``appname —version``   check the current version for any app.
* ``man <command name>`` the man pages for Linux commands.  
* ``help <command name>`` To get help with built-in shell commands use the help command
* ``help`` get list of built in command.
* ``clear``   clear screen
* ``who am i`` check current user name
* ``ls   -al`` ``-l`` for detail ``-a`` for include hidden files.
  * ``ls`` If no directory name is followed, it will list all of the files in the current working directory.
  * add ``\`` before ls to see not colored outputs.
* ``cd`` Change directory to the directory followed, if nothing followed cd to home dir.
* ``pwd`` display the absolute path to the current working directory.
* ``touch`` create new file
* ``mkdir <directory path(s)>`` make new dir
  * create multiple new folderName separate by space.
* ``cp <source> <destination> -R``, copy files for folders,  ``-R`` include directories.
  * ``cp ~/a* ~/Documents/a`` copy anything begins with a to ``a`` folder.
* ``mv <source> <destination>`` The mv command is used to move or rename files
* ``rm <PathToFile> -r`` remove files for folders, ``-r`` includes folders.
  * a folder must be empty in order to execute ``rm`` command.
* ``rmdir`` remove empty directories
* ``find <fromFolderPath> -type f -iname "*.txt" 2> /dev/null``
  * ``-type  f`` is used to locates only files
  * ``-type  d`` is used to locates only directories
  * ``-iname`` for any case of the file or directory name (case insensitive)
  * ``2>  /dev/null`` Do not display any access error message   
* ``route -n`` for checking jumps info.
* ``su`` change to root user.
* ``su username`` change to certain user.
* ``su -`` change user and redirect to default home directory after changed.
* ``ifconfig eth0`` will display networking information about the device named ``eth0``.
  * ``eth0`` the number is the order in which the card has been detected, starting with a zero
* ``ifconfig`` will display networking information about all device.
* ``ifup eth0`` set ``eth0`` interface up.
* ``ip addr`` will display the IP address for all active network interfaces.
* ``route`` 	will display the system default gateway information
* ``uname -a`` Print operating system info
* ``cat <file.txt>`` create or read a txt file.
* ``sudo`` add this before command to get execute as admin
* ``who`` see current who logged in
* ``chmod <modeCode> fildPath`` change the file mode.
* ``passwd xxxx``modify a user's password
* ``useradd xxx`` add new user
* ``echo``
* ``diff <file1> <file2>`` The diff command can be used to compare the contents of two files.


## Tools
### YUM
* It is a package manager
* ``/etc/yum.conf`` allows you to configure which software repositories to use globally (i.e., RedHat, Fedora, CentOS, etc…)
* ``/etc/yum.repos.d/`` is the configuration file for the current repositories, that will override ``/etc/yum.conf`` configuration.
* ``cdrom.repo`` configuring this file allows installation from cd-rom
* ``yum list available``, see a list of available software
* ``yum install package_name``, install a specific package.
* ``yum groupinstall 'groupname' 'groupname2'`` install package groups.
* ``yum groupinstall -y 'X Window System' 'Desktop' 'Fonts'`` install X window GUI
* ``yum install gcc –y`` Install the C compiler.
* ``yum install kernel -y`` and ``yum install kernel-devel –y`` install kernel development source.

##Vim
* ``vi``, open vim.
* ``vi filename.txt``, open a file with vi.
* Vi has insert mode, press i to enter insert mode, press Esc to exit.
* When out of insert mode, the following command works.
  * ``:w filename.txt`` save as ``filename.txt`` in the current folder.
  * ``:wq`` or ``ZZ``, save and quit.
  * ``:q!`` quit without save.
  * ``:r <file>`` insert file after current line.


### SCP
* It is used to transfer files between local machine and remote server.
* scp ``username@serverAddress:<remote file path> <local file path> -r``, ``-r``means including folders
* Ex, ``scp -r 000123456@exampleserver.com:/foldername/public_html/ /users/username/Downloads``

### SSH
* It is used to log in remote servers.
* Ex, ``ssh -i ~/.ssh/"WordPress Key.pem" ubuntu@ec2-13-229-104-228.ap-southeast-1.compute.amazonaws.com``

### NPM
* ``npm install -g package-name`` -g means install globally.

### SQL Server
* ``mssql -u userName -p password`` connect to SQL Server.
