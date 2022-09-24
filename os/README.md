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

## Processes and Threads

### Processes

- A Process is a computer program that is in execution
- Difference between progran and process
  - Program is passive, it is the entity stored on disk, i.e. the executable file
  - Process is active, it’s load into memory and the code is being gone through line by line
- Multiprocess applies the concept of parallelism
  - Data Parallelism - Distributes subsets of data across multiple cores and performing the same operation on each
  - Task Parallelism - Distributes disparate tasks across several different cores or threads from different cores
- Process consists of multiple parts
  - STACK - this contains any temporary data (i.e. pointer addresses to objects, function parameters, primitive variables)
  - HEAP - this contains data stored in memory which is dynamically allocated during run time (i.e. objects)
  - BSS - this contains uninitialized global or static data (i.e static int I;)
  - DATA - this contains initialized global or static data (i.e. int val = 3;)
  - TEXT - This is the program code
- To help manage a process it contain a Process Control Block, contained within is;
  - Process ID - this is a unique ID for each process, these are contained within a Process Table
  - Program Counter - contains the memory address of the instruction that is to be executed next. Gets incremented at successful completion of instruction
  - Process State - current state of the process
  - Priority - Gives a ranking of importance to the process
  - General Purpose Registers - holds the data of the process that is generated during its execution
  - List of Open Files - These are the names and locations of any files that are being used by the process
  - List of Open Devices - These are the ID of any devices that are being used by the process (i.e. harddrives, printers, etc)
  - Protection - items necessary to protect the PCB from inadvertent destruction
- Process State
  - New - a program has been loaded from secondary memory in primary memory and is awaiting to be scheduled
  - Ready - a process that has been scheduled and is
    waiting for its turn to execute
  - Run - a process that is currently executing
  - Terminate - a process that has finished executing and is going to be flushed out of primary memory
  - Wait / Block - a process that has initiated some type of I/O request and is waiting for that I/O to be completed
  - Suspend wait - a process that has initiated some type of I/O request but cannot perform that I/O since another process is currently monopolizing the I/O unit
  - Suspend Ready - a process that has completed its I/O but cannot return to the Ready queue because it is full
- Process Transitions
  - New
    - Entry → Program moves to Ready, becomes Process
  - Ready
    - Schedule/Dispatch → Scheduler loads Process to Run
    - Suspend → Memory/Queue full move Process to Suspend Ready
  - Run
    - I/O Request → Process has requested some type of I/O
    - Completion → Process has completed running
    - Priority/Time quantum → Process finished its turn, moves back to Ready
  - Terminate
    - N/A
  - Wait / Block
    - Suspend → I/O busy with another Process, moves Process to Suspend Wait
    - I/O Completion → Done with I/O, Process moves to Ready (resume running)
  - Suspend wait
    - Resume → I/O freed, Process moves back to Wait / Block
    - I/O Completion but still in Suspend → Memory/Queue full move Process to Suspend Ready
  - Suspend Ready
    - Resume → Memory/Queue freed, move Process to Ready
- Steps for a process to change from ready (P0) to run (P1)
  - Currently we have P0 running when Priority/Time quantum (interrupt) occurs
  - Save state into PCB0, this allows another process to now be loaded in the CPU registers
  - We will take PCB1 which is held in the Process Control Block Table, this gets loaded in CPU registers, this pull P1 from the Ready Queue to the Run State (CPU)
  - During this time P0 will have moved back to the Ready Queue
  - Now we have P1 running when Priority/Time quantum (interrupt) occurs
  - Save state into PCB1, this allows another process to now be loaded in the CPU registers
  - We will take PCB0 which is held in the Process Control Block Table, this gets loaded in CPU registers, this pull P0 from the Ready Queue to the Run State (CPU)
  - This time P1 will have moved back to the Ready Queue
- When CPU switches to another process, the system must save the state of the old process and load the saved state for the new process via a context switch
- Context of a process represented in the PCB
- Context-switch time is overhead; the system does no useful work while switching
  - The more complex the OS and the PCB, the longer the context switch
- Time dependent on hardware support
  - Some hardware provides multiple sets of registers per CPU, so multiple contexts can be loaded at once
- Processes can be described as either:
  - I/O-bound process – spends more time doing I/O than computations, many short CPU bursts
  - CPU-bound process – spends more time doing computations; few very long CPU bursts
- A Parent process create children processes, which, in turn can create other processes, forming a tree of processes
  - Generally, process identified and managed via a process identifier (pid)
  - Resource sharing options
    - Parent and children share all resources
    - Children share subset of parent’s resources
    - Parent and child share no resources
  - Address space
    - Child duplicate of parent (same program and data as parent) (recursion)
    - Child has a program loaded into it
  - Execution options
    - Parent and children execute concurrently
    - Parent waits until children terminate
- Example system call
  - `fork()` system call creates new process (UNIX)
  - `CreateProcess()` in (Windows)
  - `exec()` system call used after a fork() to replace the process' memory space with a new program
  - `wait()` parent process call `wait()` to wait for termination of a child process, the call returns status information and the process identifier (pid) of the running process upon its termination
  - `exit()` process executes last statement and then asks the operating system to delete it
    - Returns status data from child to parent (via `wait()`)
    - Process' resources are deallocated by operating system
  - `abort()` terminate execution of child/children processes, possible reasons for doing so:
    - Child exceeded allocated resources
    - Task assigned to child is no longer required
    - Parent is exiting and the OS does not allow child to continue if parent terminates
      - cascading termination. All children, grandchildren, etc. are terminated
      - The termination is initiated by the OS
- Zombie processes
  - A child process has completed execution but has not yet terminated (i.e. it still has an entry in the process & resource table)
  - Parent by issuing wait() will “reap” the child exit status
  - Child (Zombie) can terminate and be removed from the process & resource table
  - A Child will always become a Zombie before being removed from the process & resource table
- Orphan Processes
  - A child process that exists without a parent process
    - Parent process terminated (either intentionally (normal exit()) or unintentionally (crashes)) and leaves a child process continuing to execute
- Background Processes
  - A Background process is a process that runs behind the scenes (i.e. logging, system monitors, various device drivers and managers)
  - A Background process is typically a child process created by some control (parent) process to manage a specific task for the control (parent) process
  - A special Background process called daemon exists, these are created by a parent process that immediately disassociates itself from the background process thus creating the daemon. A daemon basically is created to handle a specific event and will sits idle until that event occurs
- Challenges with multiple processing
  - Identifying tasks - examine application to determine how it can be broken apart to run tasks in parallel on different cores
  - Balance - Need to ensure that work done between different task is balanced across different threads
  - Data Splitting - Just as application are split to run on different cores, the same applies to data
  - Data Dependency - There’s a need to examine the data to ensure that there is no dependency between two different tasks
  - Testing and Debugging - When applications are run on multiple cores, may different execution paths are possible, thus making testing and debugging more difficult

#### Inter-process Communication (IPC)

- Processes within a system may be independent or cooperating
  - Independent process cannot affect or be affected by the execution of another process
  - Cooperating process can affect or be affected by the execution of another process, cooperating processes need interprocess communication (IPC)
- IPC Models:
  - Shared memory - An area of memory shared among the processes that wish to communicate
    - The communication is under the control of the users processes not the operating system
    - Major issues is to provide mechanism that will allow the user processes to synchronize their actions when they access shared memory
  - Message passing - Mechanism for processes to communicate and to synchronize their actions
    - Message system – processes communicate with each other without resorting to shared variables
    - It has two operations, send and receive
    - The message size is either fixed or variable
    - Must establish a communication link between them
    - Slower than shared memory
    - Direct Communication
      - Links established directly between processes
    - Indirect Communication
      - Message passes through a message queue
      - Processes Push or Pull messages from the mailbox
    - Message passing may be either blocking or non-blocking
      - Blocking is considered synchronous
        - If both send and receive are blocking, we have a rendezvous this means both sender and receiver blocked while a message is being passed
      - Non-blocking is considered asynchronous
    - Message Buffering - No matter if we use direct or indirect communication message reside in a temporary space. It can be implemented in one of three ways
      - Zero capacity – no messages are queued on a link.
        - Sender must wait for receiver (rendezvous)
      - Bounded capacity – finite length of n messages
        - Sender must wait if link full
      - Unbounded capacity – infinite length
        - Sender never waits
  - Additional communication strategies in a client server application
    - Sockets - structure within a network node of a computer network that serves as an endpoint for sending and receiving messages across the network
    - Remote Procedure Calls - one process can use an RPC to request a service from a process located in another computer
    - Pipes - Communication is achieved by one process writing into the pipe and other reading from the pipe. To achieve the pipe system call, create two files, one to write into the file (F1) and another to read from the file (F2)
- Message Buffering

### Threads

- Multiple thread can exist for a single process
- Multithreads applies the concept of concurrency
- Fiber - a sub-thread
- Thread Control Block has:
  - Program counter (pc) - contains the memory address of the instruction that is to be executed next. Gets incremented at successful completion of instruction
  - Scheduling Properties - this can be policy (i.e. FIFO, etc) or priority
  - States
    - Ready: ready to run
    - Running: currently running
    - Blocked: waiting for resources
  - Registers → holds the data of the process that is generated during its execution
- Using multithread applications will bring four benefits:
  - Responsiveness
    - Will allow interactive applications to continue to run even if some part is processing something else
  - Resource Sharing
    - Processes can only share resources via shared memory or message passing (discussed last lecture)
    - As seen in previous slide share data and code and are used within the same address space therefore increasing efficiency
  - Economy
    - Allocating memory and resources for processes is costly
    - Creating threads uses less resources (see resources sharing)
  - Scalability
    - Multiple threads in a multiprocessor environment means more activities can be occurring concurrently
    - Single threaded processes can only run on one processor, regardless of how many are available
- User threads - Supported by the application, work outside the kernel
- Kernel threads - Managed directly by the operating system
- For User Level Threads (ULTs)
  - Kernel not aware of the existence of threads
    - Thread management done by application
    - Thread switching does not require kernel mode privileges (no mode switch)
  - Kernel activity for ULTs:
    - Kernel not aware of thread activity but it is still managing process activity
    - When a thread makes a system call
      - whole process will be blocked but;
        - For the thread library that thread is still in the running state
        - Therefore, thread states are independent of process states
- For Kernel Level Threads (KLTs)
  - All thread management is done by kernel
  - No thread library but an API (system calls) to the kernel thread facility exists.
  - The kernel maintains context information for the process and the threads, switching between threads requires the kernel
  - Scheduling is performed on a thread basis
- Models allowing a relationship between user and kernel threads, thus to work together
  - Many-to-One - There are many User Level Threads (ULTs) vying to use a single Kernel Level Thread (KLT)
    - Many user-level threads mapped to single kernel thread
    - One thread blocking causes all to block
    - Multiple threads may not run in parallel on muticore system because only one may be in kernel at a time
    - Few systems currently use this model
  - One-to-One - There is one User Level Thread (ULT) coupled to one Kernel Level Thread (KLT)
    - Each user-level thread maps to kernel thread
    - Creating a user-level thread creates a kernel thread
    - More concurrency than many-to-one
    - Number of threads per process sometimes restricted due to overhead
    - Model used by Linux and Windows
  - Many-to-Many - There are many User Level Threads (ULTs) capable of using many Kernel Level Threads (KLTs)
    - Allows many user level threads to be mapped to many kernel threads
    - Allows the operating system to create enough kernel threads
    - Adopted by Windows with the Thread Fiber package
- Thread Libraries - Threads can be implemented through the use of a library
  - Provides an API for creating/managing threads
  - Thread libraries are primarily responsible for
    - creating and destroying threads
    - passing messages and data between threads
    - scheduling thread execution
    - saving and restoring thread contexts
  - Two primary ways of implementing thread libraries
    - First approach is to provide a library entirely in the user space
      - Code and data structures reside in user space, this means threads get created in user space
    - Second approach is to provide a library at the kernel level
      - Code and data structures reside in the kernel space, invoking a function in API will result in a system call
- Currently there are a number of different implementations for threads including;
  - Pthreads (Linux, Mac OS X, and Solarius)
  - Windows
  - Java
- Several methods used for Implicit Threading
  - Thread Pools
  - OpenMP - an implementation of multithreading
    - it will create a thread for each processing core. i.e. if a system has dual core it will create two threads, quad core then four
    - a primary thread has a series of instructions executed consecutively. It forks a specified number of sub-threads and the system divides tasks among them
  - Grand Central Dispatch
    - Used in Apple systems
    - Threads are abstracted away from the programmer
    - GCD schedules blocks and places them in a FIFO queue
    - GCD then takes these blocks and assigns them to a thread once they become available from the thread pool
    - Each process has its own queue
  - Microsoft Threading Building Blocks (TBB)
  - java.util.concurrent package
- Thread Pool can create several threads at process start up. This solves the following:
  - Reduces time taken to create threads
  - Also places a boundary on the number of threads created, this will then of course limit the number of concurrent threads that are processing
  - Threads get used and then they return to the thread pool
  - Therefore, when an application requests work to be done it can ask for a thread from the thread pool
  - If none is available, it just waits until one does become available
  - Sophisticated architectures can dynamically adjust the number of threads up and down depending on load

## Scheduling

### Process Scheduling

- Process scheduler selects among available processes for next execution on CPU, dependent on scheduling algorithm
  - It maintains scheduling queues of processes
    - Job queue – set of all processes in the system
    - Ready queue – set of all processes residing in main memory, ready and waiting to execute
    - Device queues – set of processes waiting for an I/O device
    - Processes migrate among the various queues
- Scheduler Types
  - Long-term scheduler (or job scheduler) determines the processes (jobs) that can be brought into the ready queue
    - This scheduler is used in large batch systems, (mainframe)
    - Determines priority of which jobs need to be run next
      - Multiple factors used to determine this
        - Resources required for job to execute (Time, # of files read/written, databases)
        - Priority of Job (if manually set)
        - Online Job or batch job
    - Jobs usually on Disk until ready to be swapped into memory
    - Long-term scheduler is invoked infrequently (seconds, minutes) or slower
    - The long-term scheduler controls the degree of multiprogramming
  - Short-term scheduler (or CPU scheduler) – selects which process should be executed next and allocates CPU
    - Typically the only scheduler in a system (PC’s)
    - Makes sure to keep the CPU(‘s) busy
    - It selects which job is to next to be processed by the/a CPU when current process swaps out of CPU (time quantum expired or I/O request)
    - Short-term scheduler is invoked frequently (milliseconds)
    - Uses some type of algorithm to determine which process from Ready queue is next to be processed and pulls job accordingly
  - Medium-term scheduler can be added if degree of multiple programming needs to decrease
    - Remove process from memory, store on disk, bring back in from disk to continue execution: swapping
    - Medium-term scheduler strives for good process mix

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
