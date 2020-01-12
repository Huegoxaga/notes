Linux

Background

Unix is a trademarked name
Unix is Unix”like” after they conforms some standards.
Unix:
Hewlett Packard(HP-UX)
IBM AIX
IBM z/OS
Oracle Solaris
macOS
Linux is a trademarked name.  Ex, Google Android
Red Hat
Oracle
CenOS CentOS is based on RedHat Enterprise Linux
Ubuntu
Debian
Fedora


Basic Concepts

1Kernel
Used for
- Multi-tasking
- File reads and writes
- Connectivity to networks and devices
- Resource allocation


2Shell

Provides a command-line interface where the
user can execute
commands
-
Interprets
 the user commands
-
Passes
 the interpreted commands to the kernel
- Bourne Shell
(sh)
-
Bourne-Again Shell
(
bash
)
- C Shell
(csh)
- Korn Shell
(ksh)


3Filesystem
Unix/Linux every thing is a file
- xfs : Default filesystem for many newer Linux distributions
- ext4 : 4
th
 extended filesystem (still used with many Linux distributions)
- exFAT : Provides support for Microsoft’s exFAT (read + write)
NTFS : Provides support for Microsoft’s NTFS (read-only)
The filesystem start at root
does not has volume letter
the directories are files
home directory ~ are for users

system implicit treat dir and files as in the current folder
or ./abc is used for explicit method.
for file contain space use “” surround the whole path.


its important to remember that all Linux Operating systems are case sensitive

linux system use forward slash ``/``
or use the following sign.
  ``.`` is the current directory
  ``..`` is the previous directory
  ``~`` is the home directory
  ``*`` means all
In Linux, files that start with a dot ( . ) are considered hidden files
  / - the root of the file system
/var – variable files or files that vary frequently
/root/Downloads – downloads directory for the root user
/etc – contains system wide configuration files
/etc/sysconfig/iptables – the path to the iptables configuration file
/home – contains all other user home directories
/home/hagerd – the hagerd user home directory
/usr – the ‘user file system’  contains non-system critical files and binary (executable) files
/bin and /sbin – contain system binary files



Command

# startx
# shutdown –h now

appname —version   check the current version
Both the more and the less command provide paging functionality in a command line environment.

man <command name> the man pages for Linux commands.  
help <command name> To get help with built-in shell commands use the help command



clear   clear screen
who am i
ls   -l(detail) -a(include didden)
``cd`` Change directory to the directory followed,
* ``ls`` If no directory name is followed, it will list all of the files in the current working directory.
``pwd`` display the absolute path to the current working directory.
touch create new file
mkdir <directory path(s)> make new dir create multiple new folder separate by space.
cp <source> <destination> -R(include directories The cp command is used to make copies of files and folders

mv <source> <destination> The mv command is used to move or rename files


rm <PathToFile> or rm <PathToFolder> -r  remove file or folder.

rmdir remove empty directories
find / -type f -iname “abcd” 2> /dev/null(no error messages)                   /(find under root) f(files) or d(dir)
route -n for jumps
su change to root user.
su username change to certain user.
su - change user and refirect to default home directory for that user.

ifconfig eth0  will display networking information 			about the device named eth0
ifconfig   will display networking information about 		all devices
ip addr 	will display the IP address (inet) for all active network interfaces

ip route 	will display the system default gateway information
eth0 the number is the order in which the card has been detected, starting with a zero

cat
uname -a
ifconfig    or    ip addr

startx


yum package manager
/etc/yum.conf allows you to configure which software repositories to use globally (i.e., RedHat, Fedora, CentOS, etc…)
/etc/yum.repos.d/ is the configuration file for the current repositories, that will override /etc/yum.conf configuration.
cdrom.repo configuring this file allows installation from cd-rom
To see a list of available software:
yum list available
To install a specific package or package groups, you type:
yum install package_name
yum groupinstall ‘groupname’ ‘groupname2’


sudo add this before command to get execute as admin

whoami
who
cd ~
passwd xxxx
useradd xxx
echo "xxxxxx"|passwd --stdin oldboy
su - Huegoxaga
su - (to root password required)

chmod 400 fildPath    //make it private

drag file into the terminal to get its directory.
Command + +  to have bigger font
