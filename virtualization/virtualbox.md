# Oracle VirtualBox

## Introduction

- Open Source Desktop Virtualization solution Oracle.
- [Click](https://www.virtualbox.org/wiki/Documentation) to see full docs.
- For x86 and AMD64/Intel64 platforms
- Cross-platform, runs on Windows, Linux, Macintosh and Solaris OS’s
- Support for large number of Guest operating systems
  - Windows (NT 4.0, 2000, XP – Windows 10)
  - Windows Server 2003, 2008, 2012
  - Linux distributions, Solaris, OpenSolaris, OpenBSD, Debian, RedHat….
  - OS X Server
- Supports both software and hardware based virtualization
- Intel and AMD implement deferent technologies for hardware virtualization
  - On Intel CPU’s look for VT-x
  - On AMD’s look for AMD-V.
- Virtual machines can easily be imported and exported using the industry-standard Open Virtualization Format (OVF) with `.ova` extension
  - `OVF` file can be extracted into a virtual disk image file and an `ovf` file contains the machine settings using various extracting tools
- Alternative Front Ends, it has both GUI and Command line control.

## Files

- Once VMs created, its configuration will be stored in the default VM folder, it can be found in preference panel with an extension of `.vbox`.
- Hard disk files will have an extension of `.vdi`. It will be stored in the location user specified during VM creation.

## Usage

- Host Key stop the VM intercept key press and mouse click inside the VM window, by default it is the right control key.
- Snapshot makes the original disk image read-only, changes will be recorded on the differencing disk file.
- Full clone copies the entire disk image. Linked clone create the current image a snapshot.
- All disk files and snapshot can be viewed in the `File/Virtual Media Manager`.
  - A hard disk image can be set to immutable, then virtual machine gets reset after every shutdown
- Each VM icon has a change view button on the right, click it to see snapshots or logs.
- Use Device/USB menu to mount USB device to the guest OS.

## Add-ons

### Guest Additions

- Guest Additions that can be installed within the supported guest systems, it provides additional functionality, such as:
  - Shared Folders
  - 3D graphics accelerators
  - Automatic video resolution (window resizing)
  - It enables auto capture of mouse pointer when its inside virtual machine window.
- Installation
  1. Select the Devices menu option and 'Install Guest Additions...'
  2. This will result in the VBoxAdditions image (iso) being mounted in the CD-ROM drive.
  3. Run the drive.
- enables shared folders.
  1. select Devices/Shared Folders/Shared folder settings.. from the VirtualBox menu. This should open the Shared Folders window.
  2. select add a folder as the share folder from the host machine in the setting.
  3. Select the ‘Make Permanent’ and Auto-mount options. This will ensure this folder is always available as a shared folder for this Virtual Machine.
  4. In guest OS, open a terminal window.
  5. Create a directory that will become the mount point
  6. run `mount –t vboxsf foldername <folderpath>`

## Configuration file

- One virtual machine is associated with one hard disk UUID.

## GUI

- [Download Link](https://www.virtualbox.org/wiki/Downloads)
- After installing the downloaded software, install the extension pack for additional features

## Command Line Interface

- For mac, once virtualbox is installed in the OS command line, `vboxmanage` command will be available.
- For Windows, add the virtualBox installation path to the Environment's Path.
- It is a command-line interface to VirtualBox
- It exposes all the features of the virtualization engine, even those that may not yet be accessible from the GUI.
- Typical syntax vboxmanage <subcommand> <VMname>
- [Click](https://www.virtualbox.org/manual/UserManual.html#vboxmanage-intro) to see a full list of commands.

### Useful Commands

- `vboxmanage list vms` This display all VMs files that VirtualBox has.
- `vboxmanage modifyvm "old name" --name "new name"` This changes VM name.
- `vboxmanage modifyhd <hard disk file path> --type immutable` Make the virtual hard disk reset its data when the VM is shutdown.
- `vboxmanage clonehd <hard disk file path OR UUID> <cloned disk file path>` This is used to clone the hard disk with a new UUID.

## Network

### Virtual Network Adapters

Bridged

- Configured with an IPv4/IPv6 address, just like a real physical network
  adapter
- Can communicate on the network, just like any other physical network
  device
- Can communicate out to the Internet
  NAT
  (Network Address Translation)
- Configured with a special reserved IPv4/IPv6 address
- Can communicate with other devices beyond the Host OS, including the
  Internet
- By default, cannot be communicated with by other Guest OSes running
  on the same physical host
- By default, cannot be communicated with by other hosts anywhere on the
  network

### Internal Network

- Used to create small isolated network environments
- Requires an arbitrary logical network name (e.g. intnet), common to all
  Guest OSes communicating in the same small network
- Cannot communicate with the Host OS
- Cannot communicate with (or be communicated by) other hosts anywhere
  on the network
- Cannot communicate with other Guest OSes which are not configured to
  use the same logical network name (e.g. intnet)
- Cannot communicate out to the Internet
  Host-only
- Can communicate with the Host OS
- Can communicate with other Guest OSes configure with the same
  network adapter type (Host-only)
  Cannot communicate beyond the Host OS, including the Internet
