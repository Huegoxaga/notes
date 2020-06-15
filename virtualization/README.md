# Virtualization

## Virtual Machines

- Allows you to run an operating system within its window directly on top of your existing operating system.
- The OS’s contained in these windows are referred to as virtual machines(VMs).
- The physical computer is then typically referred to as the host, while the virtual machine is typically referred to as a guest OS.
- The guest OS thinks it's running on real hardware as the only OS with exclusive use of all hardware resources.
- Virtualization software configures and creates the virtual environment, redirect hardware access to simulated hardware files.
- It utilizes hypervisor to host multiple VMs runnung different operating systems.
  - Type 2 hypervisor - a software running on a host operationg system.
  - Type 1 hypervisor - a bare-metal installation.

### VMs Platforms

- Microsoft Hyper-V
  - only available for Microsoft Windows Server as a Server Role, network infrastructure virtualization, not for personal use.
- Microsoft Client Hyper-V
  - only available for windows operating system as a feature for personal use.
- VMware ESXi
  - bare-metal installation
  - infrastructure installation
  - costy, most popular
- VMware Workstation
  - installed as an application
  - personal use
  - available for Windows and Linux variants only.
  - costy
- Oracle VM
  - bare-metal installation
  - network infrastructure
  - most popular for Oracle Database
  - free to use and charged for maintenance agreement annually
- [Oracle VM VirtualBox](https://huegoxaga.github.io/notes/virtualization/virtualbox.html)
  - as an application
  - personal use
  - available for all major platforms.
  - free

## Containers Platforms

- Containers on Linux are similar to VMs, but they do not use hypervisor and add libraries on top of host OS with guest OS.
- Each isolated container using namespace. The isolation is not as strong as using hypervisor.
  - A namespace is a Linux Kernel feature that isolate processes in the same system environment.
  - There are 7 types namespaces in Linux System.
    - Ex, namespaces for User, IPC, PID...
  - one namespace can have one or more containers.
- Container on Windows machines use `Hyper-V` or can running on `Windows 10 64bit Home Insider Preview build 19018+`.
- Each container needs to be deployed on Container Runtime services. It lies between host OS and containers.
- Container focuses on running a certain software inside, with its filesystem, CPU, memory, process space, and more.
- Containers are lightweight and flexible.
- Container Providers
  - [Docker](https://huegoxaga.github.io/notes/virtualization/kubernetes.html)

## Container Orchestration

- Container orchestration is the automatic process of managing or scheduling the work of individual containers for applications based on microservices within multiple clusters.
- Container Orchestration Tools
  - Docker Compose
  - [Kubernetes](https://huegoxaga.github.io/notes/virtualization/kubernetes.html)
