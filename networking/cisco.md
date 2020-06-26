GNS is a emulator. but it cannot mimic switch as a hardware.
Packet tracer is made by cisco for practise its is good for switch.
Switch(config-if)# switchport mode access
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport mode dynamic desirable
Switch(config-if)# switchport mode dynamic auto
Switch(config-if)# switchport nonegotiate

Switch has two mode:
Access mode
used to connect an end device
Trunk mode(.1qi is the current popular encapsulation)
used to connect another switch(extend the switch)
Dynamic Trunking Protocol(Cisco owns)
Desirable - starts to negotiate truck(it is not safe to have all desirable mode)
Auto - accept truck mode.
No Negotiate - turn DTP off

Switch functions:
Address Learning
learning devices info through communication between devices.
Forwarding Decision
Cut Through
It only check the destination info and transmit
Store & Forward
It check the entire info and check data and transmit
Loop avoidance
Broadcast between two switch has two links cause loop.(Layer -2 loop)
Spanning Tree Protocol disconnect one links if there are many backup links. enable it when that only links is broken.

VLAN
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

Router
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

# Router

- Out of band configration provide direct access to the router motherboard. It provides the following ways to connect.
  - Console is used to connect to computer.(ouf of band access)
  - AUX is connected to a modem, it acts as a backup method for
  - A mini USB port one is used for easy console connection.
- A larger USB port is for update,
- Connect with software like `putty`, `Tera Term`, `Secure CRT`, `Hyper Term`. Use the following settings.
- Connection type: `Serial`
- Speed `9600`
- Serial line mostly `COM1`

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
