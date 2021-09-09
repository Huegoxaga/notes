# Operating Systems

- It is the most important piece of software running on a computer
- It is responsible for managing and communicating with the computer’s hardware
- It dictates which applications are allowed access to the hardware, when they are allowed, for how long, and so forth. This is referred to as scheduling
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
- Linux is the name of the OS kernel, means Linux "based" OS.
- Active Linux OS:
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
