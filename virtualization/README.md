# Virtualization

## Virtual Machines
* Allows you to run an operating system within its own window directly on top of your existing operating system.
* The OS’s contained in these windows are referred to as virtual machines(VMs).
* The physical computer is then typically referred to as the host, while the virtual machine is typically referred to as a guest OS.
* The guest OS thinks it's running on real hardware as the only OS with exclusive use of all hardware resources.
* Virtualization software configures and creates the virtual environment, redirect hardware access to simulated hardware files.

### VMs Platforms
* Microsoft Hyper-V
  * only available for Microsoft Windows Server as a Server Role, network infrastructure virtualization, not for personal use.
* Microsoft Client Hyper-V
  * only available for windows operation system as a feature for personal use.
* VMware ESXi
  * bare-metal installation
  * infrastructure installation
  * costy, most popular
* VMware Workstation
  * installed as an application
  * personal use
  * available for Windows and Linux variants only.
  * costy
* Oracle VM
  * bare-metal installation
  * network infrastructure
  * most popular for Oracle Database
  * free to use and charged for maintenance agreement annually
* [Oracle VM VirtualBox](./virtualbox.md)
  * as an application
  * personal use
  * available for all major platforms.
  * free


## Containers Platforms
* Containers are similar to VMs, but they have relaxed isolation properties to share the Operating System (OS) among the applications.
* Container focuses on running certain softwares inside, with its own filesystem, CPU, memory, process space, and more.
* Each container needs to be deployed on Container Runtime services, without installing and running the entire OS for every container.
* Containers are lightweight and flexible.

### Container Providers

* Kubernetes (K8s)
* Docker
