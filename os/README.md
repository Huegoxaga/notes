# Operating Systems

- It is the most important piece of software running on a computer
- It is a resource manager which decides which resources get used and when in an efficient manner
- It is a controller which manages the execution of applications/programs in order to prevent errors and improper use of the computer
- It acts as an interface between the user and the hardware/applications/programs
- They can be categorized into desktop operating systems, mobile operating systems, server operating systems and embedded operating systems
  - Embedded operating system is any OS designed for a specific piece of hardware rather than for general purpose use
- It belongs to one of the levels of a computer system:
  1.  Hardware - CPU, memory (primary/secondary), I/O devices (screens, keyboards, printers, network card)
  2.  Operating system - Controls and coordinates use of hardware among various applications and users
  3.  Application and system programs - Word processors, compilers, web browsers, database systems, video games
  4.  Users - People, machines, other computers

## CPU Scheduling

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
- Multiprocessors systems can increase throughput and reliability, help build economy of scale, it can be either:
  - Asymmetric Multiprocessing – each processor is assigned a specific task – Manager/Worker
  - Symmetric Multiprocessing – each processor performs all tasks equally
- Batch system (multiprogramming)
  - needed for efficiency
  - Single user cannot keep CPU and I/O devices busy at all times
  - Multiprogramming organizes jobs (code and data) so CPU always has one to execute
  - A subset of total jobs in system is kept in memory
  - One job selected and run via job scheduling
  - When it has to wait (for I/O for example), OS switches to another job
- Timesharing (multitasking)
  - needed for interactive computing
  - Response time should be < 1 second
  - Each user has at least one program executing in memory -> process
  - If several jobs ready to run at the same time -> CPU scheduling
  - If processes don't fit in memory, swapping moves them in and out to run
  - Virtual memory allows execution of processes not completely in memory

## Components of an Operating System

### Interrupts and Interrupt Handlers

- Operating systems work through an `Interrupt`
- An `Interrupt` is basically a device/program calling for attention in that it needs something done
- The `Interrupt` transfers control to the interrupt service routine generally, through the `Interrupt Vector`, which contains the addresses of all the service routines
- Interrupt architecture must save the address of the interrupted instruction
- A `Trap` or `Exception` is a software-generated interrupt caused either by an error or a user request
- Interrupt Handling
  - The operating system preserves the state of the CPU by storing registers and the program counter
  - Separate segments of code determine what action should be taken for each type of interrupt

### Input/Output (I/O) Structure and Operation

- Once I/O starts, control returns to user program only upon I/O completion
  - Something called a Wait instruction idles the CPU until the next interrupt
  - At most one I/O request is outstanding at a time, no simultaneous I/O processing
- After I/O starts, control returns to user program without waiting for I/O completion
  - System call – request to the OS to allow user to wait for I/O completion
  - Device-status table which for each I/O device indicating its type, address, and state
  - OS access the I/O device-status table to determine status and if necessary, to modify table entry with a new state

### Storage Structure

- Primary Storage
  - Main memory – only large storage media that the CPU can access directly
    - RAM - Random access → Typically volatile
  - Read Only memory
    - ROM – Read Only → Typically non-volatile
- Secondary storage – large non-volatile storage capacity
  - Hard disks – rigid metal or glass platters covered with magnetic recording material
    - Disk is logically divided into tracks, which are subdivided into sectors
    - Requires disk scheduling
  - Solid-state disks – faster than hard disks, nonvolatile
    - Semiconductor cells, which can contain between 1 and 4 bits of data (SLC,MLC,TLC,QLC)
    - Does not require disk scheduling

### Storage Management

- OS provides uniform, logical view of information storage
  - Abstracts physical properties to logical storage unit
- File-System management
  - Files usually organized into directories
  - Access control on most systems to determine who can access what
  - OS activities include
    - Creating and deleting files and directories
    - Primitives to manipulate files and directories
    - Mapping files onto secondary storage
    - Backup files onto stable (non-volatile) storage media

### Mass-Storage Management

- Secondary Storage used to store data that does not fit in Primary (RAM) memory
- Speed of computer operation hinges on disk subsystem and its algorithms
- OS activities
  - Free-space management
  - Storage allocation
  - Disk scheduling
- Some storage need not be fast
  - Tertiary storage includes optical storage, magnetic tape
  - Still must be managed – by OS or applications

### Caching

- copy information into faster storage system
- OS checks cache first to determine if information is there
  - If it is, information used directly from the cache (fast)
  - If not, data copied to cache and used there
- Migration of data "A" from Disk to Register
  - Multitasking environments must be careful to use most recent value, no matter where it is stored in the storage hierarchy
  - Multiprocessor environment must provide cache coherency in hardware such that all CPUs have the most recent value in their cache

### Memory Management

- For a program to execute, it must be in Primary Memory (or at least a part of it is)
- For a program to use data, it must be in Primary Memory (or at least a part of it is)
- Memory management determines what is in memory and when
- Memory management activities
  - Allocating and deallocating memory space as needed
  - Decides what processes and data to move into and out of memory
  - Keeps track of which parts of memory are currently being used and by which user

### Process Management Activities

- The operating system provides an environment in which applications can begin and run
- The operating system is responsible for trying to make the computer and all applications work as efficiently as possible
- The OS is responsible for the following activities in connection with process management:
  - Creating and deleting both user and system processes
  - Suspending and resuming processes
  - Providing mechanisms for process synchronization
  - Providing mechanisms for process communication
  - Providing mechanisms for deadlock handling

### Kernel

- Along with device drivers, the kernel manages the computer’s hardware
- It is the interface that applications use to interact with the hardware (for example, saving a file to the hard drive)
- OS now uses Dual-mode operation to protect itself and other system components
  - User mode (a user program) and kernel mode (a system operation)
  - OS employs a `Mode bit` which provided by hardware, determines if user code or kernel code
    - Some instructions designated as privileged, only executable in kernel mode
    - System call changes mode to kernel, return the user mode upon completion
  - Transition from User to Kernel Mode
    - Timer to prevent infinite loop / process in kernel mode
      - Timer is set to interrupt the computer after some time period, decremented by computer clock
      - Keep a counter that is decremented by the physical clock

## Operating System Services

- User interface - Almost all operating systems have a user interface (UI).
- Program execution - Loads program into memory, run that program, end execution, either normally or abnormally (indicating error)
- I/O operations - program may require I/O, which may involve a file or an I/O device
- File-system manipulation
- Communications, exchange info between processes via shared memory or through message passing
- Error detection in CPU, memory, I/O devices, user program
- Resource allocation
- Accounting - keeps track of which users use how much and what kinds of computer resources
- Protection and security

### User Interface

- CLI
  - Sometimes implemented in kernel, sometimes by systems program
  - Sometimes multiple flavors implemented – shells
  - Primarily fetches a command from user and executes it
- GUI
- Voice Interface
  - Siri/Alexa/Google
  - Vocal commands
    - Hands free
    - Must keep listening
    - Uses Keywords
- Touchscreen Interfaces
  - Actions and selection based on gestures
  - Virtual keyboard for text entry

### System Boot

- When power initialized on system, execution starts at a fixed memory location
  - Firmware ROM used to hold initial boot code
- Operating system must be made available to hardware so hardware can start it
  - Small piece of code – bootstrap loader, stored in ROM or EEPROM locates the kernel, loads it into memory, and starts it
  - Sometimes two-step process where boot block at fixed location loaded by ROM code, which loads bootstrap loader from disk
- Kernel loads and system is then running

### System Calls

- Interface to services provided by OS
- done by High-level language (C or C++)
- Accessed by programs via a high-level Application Programming Interface (API)
- e.g. System Calls are performed to copy the contents of one file to another file
- Number associated each system call
  - System-call interface maintains table indexed according to these numbers
- System call invoked in OS kernel
  - Returns status to calling program
  - Calling program does not need to know how system call implemented – Just use the API
- Three general methods used to pass parameters with the system calls to the OS
  - Simplest pass the parameters in registers, however, there may be more parameters than registers available
  - Parameters stored in a block, or table, in memory, and address of block passed as a parameter in a register
  - Parameters placed, or pushed, onto the stack by the program and popped off the stack by the operating system
    - Block and stack methods do not limit the number or length of parameters being passed
- Types of System Calls
  - Process control
    - create process, terminate process
    - end, abort
    - load, execute
    - Debugger for determining bugs, single step execution
    - Locks for managing access to shared data
  - File management
  - Device management
  - Information maintenance
    - get system data, set system data
    - get and set process, file, or device attributes
  - Communications
    - create, delete communication connection
    - send, receive messages if message passing model to host name or process name
    - Shared-memory model create and gain access to memory regions
    - transfer status information
    - attach and detach remote devices
  - Protection
    - Control access to resources
    - Get and set permissions
    - Allow and deny user access

### System Programs

- Provide convenient environment for program development and execution
  - Can be written in any language and use emulation to run on non-native hardware
- File management - Create, delete, copy, rename, print, dump, list, and generally manipulate files and directories
- Status information
  - Some ask the system for info - date, time, amount of available memory, disk space, number of users
  - Others provide detailed performance, logging, and debugging information
  - Some systems implement a registry - used to store and retrieve configuration information
- File modification - text editor or modification commands
- Programming-language support - Compilers, assemblers, debuggers and interpreters sometimes provided
- Program loading and execution - Absolute loaders, relocatable loaders, linkage editors, and overlay-loaders, debugging systems for higher-level and machine language
- Communications - Provide the mechanism for creating virtual connections among processes, users, and computer system
- Background Services
  - Launch at boot time
  - Provide facilities like disk checking, process scheduling, error logging, printing
  - Run in user context not kernel context
  - Known as services, subsystems, daemons

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
