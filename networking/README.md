Networking Basics
network connects nodes

LAN-Local area network
WAN- Wide area network

Internet - a nets of WANs.
Ethernet-

8 bits = 1 byte

Speed:
network speeds - it is represented by the slowest connection in between.
delay - It depends on the distance between devices.
availability - it depends on the links available

Topology:
Star = share one core switch.
Ring = connected one by one.
Bus = share one cable.

Cable type
UTP cables
CAT5    100MHz
5E     125MHz     100MB/s
6     250MHz     1000MB/s
6A  500MHz  10Gbit/s
CAT5 has less twist than CAT6
RJ45 connector is the head
crimping tool to make



T568A
T568B

Same head is Straight Through Between different devices

different head is Crossover Diagram between same devices.

Auto MDIX doesn’t care.


OSI model

developed by ISO, because IBM vs DEC cannot communicate.

each layer work independently

Please Do Not Throw Sausage Pizza Away
7. Application - the point of contact for network aware application
	FTP. TFTP,SNMP,DNS,HTTP protocol work on this layer
6. Presentation - the layer generify data, encryption convserion,  TLS,SSL
5. Session - create and maintain session, has
————above equals 4 in TCP/IP———————————-above layers will not be discussed by network engineer.
socket = ip address + port number
4. Transport  ———————————————- segement with header and encapsulation create TCP(Reliable) or UDP(Faster) and add Port Numbers.  equivalent to 3 in TCP/IP
3. Network —————————-equivalent to 2 in TCP/IP——packet with IP
2. Data Link, Frame with MAC address
1. Physical ———————-1 and 2 are equivalent to 1 inTCP/IP, it is bit(data unit) hardware
*they all has header added one by one
TCP/IP model
4. Application
3. Transport
2. Internet
1. Network Interface
TCP/IP comes in A TIN


Media Access Control is a unique physical address for each devices, it is hard-coded.
MAC is a 12 digit hexadecimal value, there are two digit in one pair, consisted of 6 pairs.

All frame transmit data using above model to add headers for each one of them and strip the header according layer types.


Nodes are connected by switches, wireless access points, and routers.

Internet Protocol (IP) is logical address

Address Resolution Protocol (ARP) is used to find MAC from IP

Port numbers are used to identify the type of application or services during data transmission.
random port number

ICMP protocol

IPv4
A group of 4 octets (8-bit) data.
4.3 billions unique addresses available.

It has network ID in the left portion and node ID in the right portion combined.
network ID is represented by subnet mask 1 value digit place.
gateway is the representation of the network ID

class A
1.0.0.0 - 126.255.255.255/8
class B
128.0.0.0 - 191.255.255.255/16
class C
192.0.0.0 - 223.255.255.255/24
D multicast
224-239
E experiment
240-255

the first IP of each Host IP is the Network ID
the last is the broadcast ID



Subnetting is classless IP address (CIDR)
it is achieved by have 1 more bit in subnet mask

Supernetting is lend 1 bit to represent all its subnets. it is a summarization of ip addresses.




ideal network size is < 500

public ip used in WAN
private ip used in LAN

private range
10.0.0.0 - 10.255.255.255
172.16.0.0 - 172.31.255.255
192.168.0.0 - 192.168.255.255
private addresses are not routable. In order to reach the internet NAT is used.
Automatic Private IP Addressing (APIPA)
When there is no DHCP, APIPA is configured to assign random IP starts with 169.254 for local communication.i
169.254.0.0 - 169.254.255.255
starts with 127 (127.0.0.1)is a loopback address.
Unused/Reserved 0.0.0.0 - 0.255.255.255
		      224.0.0.0 - 255.255.255.255



IPv6
8 group of 4 hexadecimal values, delimited by colon
0s can be group and simplified.
::1 is loopback

MAC address is a 12 X (Hexdecimal) 4 bit = 48 bit Number divided by : into 3 parts.

Devices
hub
it copy info from 1 port to all port.
not intelligent
1 collision domain
1 broadcast domain

Bridge
between hub and switch

Switch
Intelligent - it learn Mac address of devices on CAM table
Many Collision Domains - 1 port a collision domains
One or more broadcast domains(VLAN)

manegement IP is  the switch IP used for telnet connection

Router
Intelligent - only exchange info between different networks,
Many Collision Domains
Many broadcast  Domains

AUX is connected to a modem


USB port is for update

Console is used to connect to computer.(ouf of band access)
connect With putty/Tera Term/ Secure CRT/Hyper Term.

Use ARP to broadcast request to get destination MAC address
only device with the request Mac address will reply

GNS is a emulator. but it cannot mimic switch as a hardware.
Packet tracer is made by cisco for practise its is good for switch.


DHCP
Is a protocol that automatically configure IP to a host

6 message

4 mandatory
DHCP Discocvery
broadcast to find DHCP,
DHCP offer
all DHCP server in the network reserver one IP address and sent a offer
DHCP Request
Client confirm
DHCP Ack
accepted server confirm. others server take the offer back and free its IP pool.


4 non-critical messages
DHCP Information
If the client need more information from the DHCP offer
DHCP Release
The client tell the server to release its IP address when done.

TCP Transmission
TCP is a connection oriented transmission. UDP is a connectionless transmission.

3 Way Hand Shake.
SYN package
SYN/ACK package
ACK package

CRC is the hash value attached to the beginning of the frame for error checking process before data is out and in the LAN. It is the job for routers.

Windowing
It is the trail process for testing the max packages can be sent at the same time using TCP connection.





Port Number
It is used to marking destination and source devices
Source port number random number in upper part of 65535
Destination port number uses well-known port number.

0-65535 port numbers





Some standard port number.
80
- Unsecured web browsing (http)
443
- Secured web browsing (https)
25
- Unsecured/secured sending of e-mail messages (smtp/smtp-s)
110
- Unsecured/secured receiving of e-mail messages (pop/pop-s)
143
- Unsecured/secured receiving of e-mail messages (
imap/
imap-s
)
Where:
http(s)
- Hypertext Transport Protocol (Secured)
smtp(-s)
- Simple Mail Transport Protocol (Secured)
pop(-s)
- Post Office Protocol (Secured)
imap(-s)
Internet Message Access Protocol (Secured)

There are (3) sub-ranges for stanrdrand port numbers
Well-known Ports: registered with a governing body
 (a.k.a. System Ports)
Range:
0 - 1,023
Registered Ports: registered by developer, can be used when no conflict.
Range:
1,024 - 49,151
Dynamic, Private, or Ephemeral Ports: not registered, for temp use.like web browser applications.
Range:
49,152 - 65,535

subnet mask is used to indicate the network ID

router is the only way for traffic goes in and out. it is the gateway and has a routing table.
Fully Qualified Domain Names:
   hardest.acme.com
hostname domain FQDN

Domain Name Service(DNS)
is a distributed database
forward lookups is FQDN -> IP
reverse lookups is IP ->FQDN

There is a Local Resolution Files
Windows    C:\Windows\System32\drivers\etc\hosts
Linux      /etc/hosts

Command for Windows
ipconfig -?
ipconfig
ipconfig /all
netsh interface ipv4 show addresses
ping 127.0.0.1
ping 206.191.86.29
ping mocomotion
ping www.google.com
ping -4 www.google.com
ping –a 206.191.86.29
ping -4 –a 206.191.86.29
ping -6 www.google.com
ping -6 2607:f8b0:400b:80b::2004
ping -6 -a 2607:f8b0:400b:80b::2004
arp -a
netsh int ipv4 show neighbors
netsh int ipv6 show neighbors


Computer networks can be divided into (2) distinct models
- Peer-to-Peer Network Models
Client/Server Network Models






Switch has two mode:
Access mode
used to connect an end device
Switch(config-if)# switchport mode access
Trunk mode(.1qi is the current popular encapsulation)
used to connect another switch(extend the switch)
Switch(config-if)# switchport mode trunk
Dynamic Trunking Protocol(Cisco owns)
Desirable - starts to negotiate truck(it is not safe to have all desirable mode)
Switch(config-if)# switchport mode dynamic desirable
Auto - accept truck mode.
Switch(config-if)# switchport mode dynamic auto
No Negotiate - turn DTP off
Switch(config-if)# switchport nonegotiate

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

VTP version 1/2  (2 default)
VTP domain - safety setting
VTP password

VTP Pruning
look at VLAN and prevent not useful information travel to other switch.
switchport trunk allowed vlan x

check
show vlan

each vlan has its own management IP


Connection
Speed
	Fast Ethernet(100Mbps) or  Gigabit Ethernet(1000Mbps)


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
		RIP      Old, distance vector, shortest path.
		OSPF  Link state, fastest path.
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

Update Timer  default every 30 second
Invalid Timer default 180 seconds - when no info received from certain network
Holddown Timer default 180 after invalid timer finish
Flush Tmer:240s starts when invalid timer starts

Rip problems
It has auto-summarzation for routing table. it cause problem.

adjacent router send misleading info about info network on opposite side network, loop for large hop count.
Solved by:
Split Horizon  -  don’t send info to router which u learn this info earlier.
Route poison  - generate large hop count(16(not accessible)) right away

Inter switch routing
router in between two switches

inter VLAN routing (router on a stick)
Use one cable from router with 2 - sub interface setting to connect one switch’s 2 VLAN seperately using truck mode.

DNS
find the IP of Domain names.
Check Local DNS record -> Resolver <-> Root Server
					<-TLD Server(Top level Domain)
					<->Authoritative name servers.
			     <-
Private Resolver for private Domain
public resolver for internet(ISP resolver and Google DNS)


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
