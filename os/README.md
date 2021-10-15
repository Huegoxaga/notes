# Operating Systems

- It is the most important piece of software running on a computer
- It is responsible for managing and communicating with the computer’s hardware
- It dictates which applications are allowed access to the hardware, when they are allowed, for how long, and so forth. This is referred to as scheduling
  - Scheduling algorithms includes first come first serve, shortest job next, priority, shortest remaining time, round robin, etc
  - Operating systems opened up the opportunity to have multiple processes running at once (Parallelism)
  - Communication between processes can be achieved via sockets, signal handlers, shared memory, semaphores and files
  - OS also controls the execution of multiple threads in each process (Concurrency)
  - For programs utilize multithread, there are three common thread liveness problems:
    - Deadlock: Each thread operating is waiting for another thread to finish executing
      - There is no CPU usage, because all threads are waiting
      - Can be the affect of lock ordering (when multiple locks are required)
        - May have to modify the order the locks are obtained
        - May have to include a lock timeout after a certain amount of time all locks are released and each thread has to try again
      - Can also happen when a thread unexpectedly exits without unlocking resources
        - Lock and unlock should always be executed in programs exception handling step
    - Starvation: For some reason, a thread is unable to obtain the resources it needs
      - Having priority on threads may cause this, low priority threads never get scheduled to run
      - Having a large number of incoming threads running may also cause starvation
    - Livelock: Threads are still not making progress, but are actively trying to solve the problem
      - It is like four cars are waiting other to go first in a four ways intersection in front of all-way stop signs
      - CPU has consistent usage under livelock, lots of context switching going on
- All of the hardware resources are managed by this singular operating system, and applications can then run in the environment set up by that operating system
  - For most virtualization tool, they are running on top of this singular operating system called the host OS
  - Type 1 hypervisor is an exception, it runs directly on the hardwares
- They can be categorized into desktop operating systems, mobile operating systems, server operating systems and embedded operating systems
  - Embedded operating system is any OS designed for a specific piece of hardware rather than for general purpose use
- Components of an Operating System
  - Kernel
    - Along with device drivers, the kernel manages the computer’s hardware
    - It is the interface that applications use to interact with the hardware (for example, saving a file to the hard drive)
  - Process Management
    - The operating system provides an environment in which applications can begin and run
    - The operating system is responsible for trying to make the computer and all applications work as efficiently as possible
  - Shell
    - The shell is the interface that users interact with. For most users, it is a graphical user interface (GUI). Operating systems can also accept user input via a command line interface (CLI).

## Unix

- UNIX is an operating system since the 1960’s
- Unix is a [trademarked](www.unix.org) name.
- UNIX operating system is one that
  - conforms to a set of standards
  - is registered with the governing body of the trademark.
  - If any those two requirement is not met, it can only be called Unix 'like' OS.
- Active Unix OS:
  - Hewlett Packard(HP-UX)
  - IBM AIX
  - IBM z/OS
  - Oracle Solaris
  - Apple MacOS

## Linux

- Linux is Unix "like" OS.
- Linux was created around 1990's
- Linux is a [trademarked](www.linuxmark.org) name.
- Linux is the name of the OS kernel, means Linux "based" OS
  - The Linux kernel, written by Linus Torvalds, first released in 1991
- Linux distribution refers to an OS, which package the kernel along with shells, utilities, and so on, in order to create full-fledged operating systems
- Active Linux Distributions:
  - Google Android
  - Oracle Linux
    - Red Hat Enterprise Linux
    - CentOS - It is based on Red Hat Enterprise Linux
    - Fedora
  - Ubuntu Linux
    - The LTS version number has format `YY.MM` determined bt the realse year and month.
    - It release LTS(Long-term support) versions every 2 years in April, each one will be supported for 5 years.
    - Every six months between LTS versions, Canonical publishes an interim release of Ubuntu. These are production-quality releases and are supported for 9 months, with sufficient time provided for users to update.
      - Interim releases will introduce new capabilities from Canonical and upstream open source projects, they serve as a proving ground for these new capabilities.
    - It uses `apt` for package management.
  - Debian Linux
  - [Kali Linux](https://www.kali.org/downloads/)
    - A Linux distribution Focused on cyber security
    - It has been pre-configured with all of the most well-known cyber security tools
