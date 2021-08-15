# Cisco

## Practice Tools

* Emulator run hardware image, simulator mimic the hardware behavior using software
* `GNS` is an emulator. but it cannot mimic switch as a hardware.
* `Packet Tracer` is a simulator made by cisco for practise. it is good for switch.

## Device Connection

* Out of band configration provide direct access to the router motherboard. It provides the following ways to connect.
  * Console is used to connect to computer.\(out of band access\)
  * AUX is connected to a modem, it acts as a backup method for out of band access.
  * A mini USB port one is used for easy console connection.
* A larger USB port is used for update,
* Connect with software like `putty`, `Tera Term`, `Secure CRT`, `Hyper Term`. Use the following settings.
* Console port connection setup:
  * Connection type: `Serial`
  * Speed `9600`
  * Serial line mostly `COM1`, can be found out in the device manager.
* Telnet conncection setup
  * Configure interface management IP
  * In the host machine's terminal, run `telnet <CiscoDeviceIP>`
    * run `brew install telnet` to install `telnet` for Mac
  * The user can only establish one connection through one telnet port at a time.
* SSH conncection setup
  * It is more secure than telnet as the traffic is encrypted
  * Steps to setup SSH connection
    1. setup hostname
    2. create domain name
    3. generate secure key
    4. set ssh to version 2
    5. create local user
    6. allow ssh connection for the virtual lines.

## Command Line

* Cisco command has auto completion feature with `tab`.
* Commands work when the minimum required characters are entered that can be used to distinguish it with all other possible commands.

### Prompt

* The command line prompt starts with the hostname and followed by the mode indicator.
* Commands lines for Cisco devices can be in different modes, it is indicated by the symbols or brackets in the command prompt:
  * `>` - User EXEC Mode - Privilege Level 1
  * `#` - Privileged EXEC Mode - Privilege Level 15\(highest\)
    * `(config)#` - Global Configuration Mode
      * `(config-if)#` - Interface Configuration Mode
      * `(config-router)#` - Routing Configuration Mode
      * `(config-line)#` - Line Configuration Mode

### Commands

#### General Commands

* `?`, list all commands available in the current mode
  * `t?`, list commands start with letter `t`.
  * `<cr>` output means blank space, so a command can be executed by hitting enter directly
* `enable`, switch mode `>` to mode `#`.
* `disable`, `exit`, `end` or `Ctrl + Z` switch to the previous mode
* `show privilege` show the current privilege level
  * the privilege level ranges from 1 to 15, higher level will have more commands available.
* `show ip interface brief` show a breif summary of all ip interface status in current privilege Level.
  * When protocol is down, it means there is no traffic at this port.
* `ping 192.168.1.3` ping an IP address
  * `!` means packet received, `.` means packet not received.
* `telnet 192.168.1.3` open telnet connection
  * `Shift + Ctrl + 6` -&gt; `x`, go to the command for previous connection.
* `show users` get current user connection and connection ID
* `show version` show register info
* `show interface f 0/0` show port details
* `show clock` show the current time
* `show controller Serial 0` \(Router Only\) show serial connection info
* `show interface f 0/0 switchport` \(Switch Only\) show port access mode
* `show vtp status` \(Switch Only\) show vtp info including version number
* `show cdp neighbours detail` show others devices detail through `CDP`
* `show sessions` get all devices logged into
  * Hit enter to go to the last connection, Hit `Enter + 1` to go to connection with ID `1`.
* `no <command>` negect or disable the command.

#### Privileged EXEC Mode

* `configure terminal`, switch from mode `#` to `(config)#` mode.
* `show running-config` show the current configuration saved in RAM
* `show startup-config` show the saved configuration for next startup in NVRAM
* `show vlan` show the the ID, name, ports of all existing VLAN
* `show interfaces trunck` show all trunk ports
* `write` save the running config as startup configuration
* `copy <From> <To>`\(recommanded alternative for `write` command\)
  * `copy running-config startup-config` save running-config to startup-config
* `clear line 0` kick out other connection
* `disconnect 1` disconnect a connection
* `reload` or `reboot` restart the device

#### Global Configuration Commands

* `enable password <password>` setup a password when entering `#` mode.
  * This password is required by `vty` connection by default.
* `enable secret <password>` setup a secret password when entering `#` mode.
  * The password will be encrypted in the config files.
* `do <command>` run `#` command in `(config)#` mode.
* `ip domain-lookup`, enable domain-lookup for unrecognized commands by default it is on.
* `ip default-gateway <IP>` setup the default gateway IP address
  * Router needs a default gateway to work with router.
* `ip domain-name example.com` set a domain name
* `crypto key generate rsa` then enter the bits size for the key size to generate a key
* `ip ssh version 2` set the ssh version to 2
* `username <name> password <password>` create a new local user
* `hostname <NewName>`, change hostname of the device
* `banner motd <delimittingCharacter>`, entering the command will allow you change the login banner message, enter the same delimitting character at the end of the banner message, then hit enter to save the change.
  * It will be displayed before password prompt during login
* `banner login <delimittingCharacter>` \(Router Only\), set the login message
* `cdp run` enable `CDP`
  * enabled by default
* `lldp run` enable `lldp`
  * disabled by default
* `interface gigabitEthernet 0/0`, enter the Interface Configuration Mode for gigabitEthernet Port `0/0`.
  * All router ports start at `0/0`
  * All switch ports start at `0/1`
* `interface range f0/2-5` configure port `2-5` at once
* `line console 0`, enter the Line Configuration Mode
* `line console vty 0 15` enter the Line Configuration Mode for all 16 virtual lines.
  * `vty 0 15` configuration will be broken down to `0 4` and `5 15` to support older devices with only `vty 0 4`
* `interface vlan 1`\(Switch Only\), enter the Interface Configuration Mode for the `vlan 1`
  * This is where the access IP address or the management IP located
* `router rip`\(Router Only\), enter the Routing Configuration Mode for `RIP` protocal.
* `vlan 1`\(Switch Only\), create VLAN\(if not exist\) and enter the VLAN Configuration Mode for `vlan 1`.
* `interface Loopback 0`\(Router Only\) enable a lookback interface and change its state to up, then enter loopback config mode
* `interface serial 0` \(Router Only\) enter the serial config mode

**Interface Configuration Commands**

* `ip address 10.1.1.1 255.255.255.0` set management IP for the interface.
* `shutdown` administratively shutdown a port.
  * open a port using negating command `no`
* `cdp enable` enable cdp for a certain port
* `lldp receive` allows the port to receive lldp info from other devices.
* `lldp transmit` allows the port to receive and send lldp info with other devices.
* Switch Only Commands
  * `switchport mode access` set port to access mode to connect the port to end device
  * `switchport mode trunk` set port to trunk mode to connection the port to another switch
  * DTP config
    * `switchport mode dynamic desirable`
    * `switchport mode dynamic auto`
    * `switchport nonegotiate`
  * Assign a port to VLAN
    * `switchport mode access` only ports in access mode can be in a VLAN
    * `switchport access vlan <NO>` assign the port to a VLAN
      * will create new VLAN if the VLAN number does not exist

**VLAN Configuration Commands**

* `name <name>` naming the VLAN
  * The name is only used as a description.

**Line Configuration Commands**

* `password <password>` set login password
* `login`, set to require login password for the current line console port
* `login local`, enable login and use the local user password to login
* `transport input <option>` setup input transmittion type, there are 4 options:
  * `all`
  * `none`
  * `telnet`
  * `ssh`
* `logging synchronous` sync command line input after interrupt by other output while typing.
* `exec-timeout` set timeout duration.
  * `0` means never timeout. `3 10` means `3 minutes 2 seconds`.

**Serial Configuration Commands**

* `clockrate 64000` config clock rate for `DCE` connection with DTE terminal.

```text
## Switch

### Trunking

- Trunking is a way to combine multiple switch into a bigger switch througn trunck port connection
- Switch has two mode:
  - Access mode - used to connect an end device
  - Trunk mode(.1q is the current popular encapsulation) - used to connect another switch(extend the switch)
- Dynamic Trunking Protocol(Cisco owns) - Controls how to establish trunk connection
  - Desirable - starts to negotiate truck(it is not safe to have all ports in desirable mode)
  - Auto - accept truck mode.
  - No Negotiate - turn DTP off
- Switch functions:
  - Address Learning - learning devices info through communication between devices.
  - Forwarding Decision
  - Cut Through - It only check the destination info and transmit
  - Store & Forward - It check the entire info and check data and transmit
  - Loop avoidance
    - Broadcast between two switch has two links cause loop.(Layer -2 loop)
    - Spanning Tree Protocol disconnect one links if there are many backup links. enable it when that only links is broken.

### VLAN

Divided one switch to two virtual to separate network among ports.
it can logically group, Segment broadcast, subnet correlation.
info from port in a VLAN has VLAN Tags, its a layer 2 feature
port without VLAN setting belongs to native VLAN.
when change native VLAN all switch should be changed

VLAN trunking protocol (VTP)
make vlan setting among all connected switch
uses switch setting with the highest reversion number.

Server - can make a changes about VLAN

Client - cannot make changes about VLAN

Transparent - turn VTP off.

VTP version 1/2 (2 default)
VTP domain - safety setting
VTP password

VTP Pruning
look at VLAN and prevent not useful information travel to other switch.
switchport trunk allowed vlan x

check
show vlan
each vlan has its own management IP

Switch security
Allow certain Mac address or sticky it stick to the next mac address who connect it
set max number of mac address for this port
set violation what to do if there is a violation:
can choose three consequence
protect - protect from wrong Mac device
restrict - protect plus log the incidence using SNMP
shutdown
To enable port security: Switch(config-if)# switchport port-security.

check
show port-security

## Router

Router rely on software, Cisco IOS
Has the help of hardware CEF(Cisco Express forwarding)

Static
set path
Dynamic
auto path, using protocol and router auto communicate and route.
IGP
for LAN
RIP Old, distance vector, shortest path.
OSPF Link state, fastest path.
EIGRP(Cisco own) both distance and speed
EGP
for WAN
BGP
EGP

RIP
open source
RIPv1
classful Version(no VLSM)
No Authentication - anyone can provide routing info
Uses Broadcast: send broadcast routing info everywhere

RIPv2
Classless Version(supoorts VLSM)
Adds Authentication
Uses Multicast

Update Timer default every 30 second
Invalid Timer default 180 seconds - when no info received from certain network
Holddown Timer default 180 after invalid timer finish
Flush Tmer:240s starts when invalid timer starts

Rip problems
It has auto-summarzation for routing table. it cause problem.

adjacent router send misleading info about info network on opposite side network, loop for large hop count.
Solved by:
Split Horizon - don’t send info to router which u learn this info earlier.
Route poison - generate large hop count(16(not accessible)) right away

Inter switch routing
router in between two switches

inter VLAN routing (router on a stick)
Use one cable from router with 2 - sub interface setting to connect one switch’s 2 VLAN seperately using truck mode.

ACL
it has permit/deny
it can be a compares from top to down
only a match found execute right away, no more comparison
has a implicit deny at the end(if one user define condition is created.)

Standard ACL
name 1-99 & 1300-1999
or name
Based on source IP

Extended ACL
100-199& 2000-2699
Based on Source IP, Destination IP, protocol or port No.

Wildcard mask:
It is the inverse of subnet mask. change subnet mask’s 1 to 0, 0 to 1

Rules:
Standard ACL applied close to Destination
Extended ACL applied close to Source //no more two S in one statement to remember.

NAT

Inside Local - before transit source
Inside Global - after transit source
Outside Local - Destination address before transition
Outside Global - Destination address after transition
Outside address are usually the same.

Static NAT
one to one transition. one public address for each device.
Dynamic NAT
many to many transition. inside local auto assign public IP when there is one available.
NAT Overloading(PAT)
many to one, one public IP address but with different random source port number. for both inside local and inside global IP address.

Cisco three layer architecture
access layer - connect to device
distribution layer - building layer (connect access layer)
core layer - connect to the outside. connected by ether Channel

Ether Channel
Combine two link to one link with double speed

CDP
Cisco Discovery Protocol
Cisco own

LLDP
Link Layer Discovery Protocol
open source

Switch(config-if)# speed 100 (switch will restart)
Duplex
full and half should coordinate.
auto setting for fast ethane is half
auto setting for giga ethernet is full
full
both send and receive
half
either send or receive
Switch(config-if)# duplex full
```

