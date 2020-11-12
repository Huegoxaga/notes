# Networking

## Network

- Α network is simply defined as something that connects things together for a specific purpose.
- A computer network connects two or more devices together to share a nearly limitless range of information and services
- Network Types categorized by size:
  - `LAN` - Local Area Network
    - `Ethernet` - Ethernet is the most common LAN technology.
  - `WAN` - Wide Area Network
    - `Internet` - a net of WANs.
  - `MAN` - Metropolitan Area Network
    - It is defined as a network that connects LAN’s across a city-wide geographic area.
- Network Types categorized by function:
  - `SAN`- Storage Area Network
    - It provides systems with high-speed, lossless access to high-capacity storage devices.
  - `VPN` - Virtual Private Network
    - It allows for information to be securely sent across a public or unsecure network(public Internet). Common uses of a VPN are to connect branch offices or remote users to a main office.
- Measurement:
  - `network speeds` - it is represented by the slowest connection in between.
    - Bits and Byte
      - 8 bits = 1 byte
      - `bits` are generally used to describe network speed. It should be represented as lowercase `b`. `1Mbps` means one megabits per second
      - `bytes` are generally used to describe data size. It should be represented as uppercase `B`. `1MB` means one megabytes.
    - Fast Ethernet(100Mbps) or Gigabit Ethernet(1000Mbps)
  - `delay` - It depends on the distance between devices.
  - `availability` - it depends on the links available
- Transmission Modes
  - `Full Duplex` - the communication between sender and receiver can occur simultaneously. The sender and receiver can both transmit and receive at the same time.
  - `Half Duplex` - The communication between sender and receiver occurs in both directions, but only one at a time. The sender and receiver can both send and receive the information, but only one is allowed to send at any given time.
  - `Simplex` - In simplex transmission mode, the communication between sender and receiver occurs in only one direction. The sender can only send the data, and the receiver can only receive the data.
- Network Architectures
  - It consisted of hosts(network devices) or nodes. It can act as one of the following three roles
    - A host can request data, often referred to as a client.
    - A host can provide data, often referred to as a server.
    - A host can both request and provide data, often referred to as a peer.
  - Types of Network Architectures
    - Peer-to-Peer - all hosts on the network can both request and provide data and services.
    - Client/Server - hosts are assigned specific roles. Clients request data and services stored on servers.
    - Mainframe/Terminal - a single device (the mainframe) stores all data and services for the network.
- Topology:
  - It is the arrangement of the elements of a communication network.
  - Types:
    - Star - share one core switch.
    - Ring - connected one by one.
    - Bus - share one cable.

## Network Reference Models

- It is used to divide and break down a complicated network system into layers.
- It is used to standardize networks.

### OSI model

- The Open Systems Interconnection (OSI) model.
- Developed by International Organization for Standardization(ISO), because IBM vs DEC cannot communicate.
- Each layer work independently

1. Physical - present data as bit, all hardwares likes cables and wires are in the physical layer.
2. Data Link - present data as frame with MAC address in the data link header. It will also handle error checking.
3. Network — present data as packet and add IP address in the packet header. It naviagte and find the best path for data transmition.
   - Each packet in the conversation will have the same source and destination addresses, however they may not take the same path.
4. Transport - present data as encapsulated segement with header. It decide which data transmition protocol to use and add a port number and a source port number to the IP address.
5. Session - create and maintain session.
6. Presentation - the layer generify data, deal with data encryption and convserion.
7. Application - the point of contact for network aware application

- Mnemonic: `Please Do Not Throw Sausage Pizza Away`
- 2, 3, 4 layers all have its own header that will be added or processed during data transmition.
  - as a result, a frame will have three headers. a segement will have one header.

### TCP/IP model

- Developed by the Department of Defense.

1. Network Interface - equivelent to OSI model 1 and 2.
2. Internet - equivelent to OSI model 3.
3. Transport - equivelent to OSI model 4.
4. Application - equivelent to OSI model 5,6,7.
   - This layer is handled by the operating system and will not be discussed by network engineer.

- Mnemonic: TCP/IP comes in `A TIN`.

## Protocols

### DataLink Layer Protocols

#### Address Resolution Protocol (ARP)

- Data transmition in the data link layer uses MAC addresses to find destination.
- This protocol is used to find MAC address of the destination device in a local network before sending the data.
  - If destination IP is not local the ARP request will be sent to the gateway.
- It is achieved by broading the destination IP address to all devices in the network.
- only device with the request Mac address will reply

### Network Layer Protocols

#### ICMP protocol

- Internet Control Message Protocol

#### Internet Protocol

- Internet Protocol (IP) is the logical address of devices.
- Responsible for packet delivery and routing

##### IPv4

- A group of 4 octets (8-bit) data with a total of 32 bits.
- 4.3 billions unique addresses available.
- IPv4 can be presented in dotted decimal notation: `130.132.19.31`. It can be converted to binary form as `10000010.10000100.00010011.00011111`.
- The gateway IP is the IP address of a router.
- Subnet Mask
  - It has network ID in the left portion and node ID in the right portion combined.
  - Subnet Mask is used to determine which part of the IP is networkID.
    - network ID is represented by subnet mask 1 value digit place. For an ip with a mask as `11111111.11111111.00000000.00000000` -> `255.255.0.0`, the first two groups of octets, represents networkID.
  - For `192.168.0.1/24` The number followed means the first n number is the networkID. This type of notation is called classless IP address (CIDR) notation the number after `/` is called network prefix .
- Among all the hosts in a network, the first IP is the network ID. The last one is the boardcast ID.
- IPv4 address can be devided into different classes according to its first octet.
  - class A: `1.0.0.0 - 126.255.255.255/8`
  - class B: `128.0.0.0 - 191.255.255.255/16`
  - class C: `192.0.0.0 - 223.255.255.255/24`
  - class D(multicast): `224.0.0.0 - 239.255.255.255`
  - class E(experimental purpose) `240.0.0.0 - 255.255.255.255`
- Subnetting is achieved by have 1 more bit of subnet mask compare to its IP class default mask.
- Supernetting is lend 1 bit to represent all the subnets. it is a summarization of ip addresses.
- ideal network size is less than 500 hosts.
- RFC 1918 reserves three ranges of IP addresses for private use
  - Class A range `10.0.0.0 - 10.255.255.255`
  - Class B range `172.16.0.0 - 172.31.255.255`
  - Class C range `192.168.0.0 - 192.168.255.255`
  - private ip is used in LAN while public ip is used in WAN
  - private addresses are not routable. In order to reach the internet NAT is used.
- Automatic Private IP Addressing (APIPA)
  - When there is no DHCP, APIPA is configured to assign random IP starts with `169.254` for local communication. `169.254.0.0 - 169.254.255.255`
- `0.0.0.0 - 0.255.255.255` is Unused/Reserved IP

##### IPv6

- 8 group of 4 hexadecimal values, delimited by colon
- 0s can be group and simplified.
- ::1 is loopback

### Transport Layer Protocols

##### Transmission Control Protocol(TCP)

- TCP is a connection oriented transmission.
- Responsible for establishing and maintaining network conversations
- It breaks the session data into packets and passes packets the network layer.
- It receives packets from the network layer, verifies and assembles them for delivery to the receiving application
- It is more reliable than UDP
  - TCP uses a three-way handshake to establish a reliable connection.
    1. SYN package
    2. SYN/ACK package
    3. ACK package
- Windowing - It is the trail process for testing the max packages can be sent at the same time using TCP connection.

##### User Datagram Protocol(UDP)

- It is a connectionless transmission.
- It is an alternative communications protocol to Transmission Control Protocol (TCP) used primarily for establishing low-latency and loss-tolerating connections between applications on the internet. It is faster than TCP.

### Presentation Layer Protocols

TLS,SSL

### Application Layer Protocols

FTP. TFTP,SNMP,DNS,HTTP, smtp pop imap
http(s)

##### Hypertext Transport Protocol(HTTP)

- It uses port 80.
- HTTP is called a stateless protocol because each command is executed independently, without any knowledge of the commands that came before it.
- HTTP Request
  - It has request methods as `POST`, `GET`, `PUT` etc.
  - `GET` request cannot have request body, the parameter can only be encoded at the end of the request url
  - Request header content type decide the content type of the request body
    - On the server side, `Access-Control-Allow-Headers` need to be setup to allow certain headers in request.
    - `"Cache-Control", "no-cache"`, `"Pragma", "no-cache"` can be used to disable client side broswer cache
- It has a Authentication realms for authentication
- HTTP Response
  - The response message contain:
    - a status line which includes the status code and reason message (e.g., HTTP/1.1 200 OK, which indicates that the client's request succeeded)
    - response header fields (e.g., Content-Type: text/html)
    - an empty line
    - an optional message body
  - The response status codes are
    - 1×× Informational
      - 100 Continue
      - 101 Switching Protocols
      - 102 Processing
        2×× Success
      - 200 OK
      - 201 Created
      - 202 Accepted
      - 203 Non-authoritative Information
      - 204 No Content
      - 205 Reset Content
      - 206 Partial Content
      - 207 Multi-Status
      - 208 Already Reported
      - 226 IM Used
    - 3×× Redirection
      - 300 Multiple Choices
      - 301 Moved Permanently
      - 302 Found
      - 303 See Other
      - 304 Not Modified
      - 305 Use Proxy
      - 307 Temporary Redirect
      - 308 Permanent Redirect
    - 4×× Client Error
      - 400 Bad Request
      - 401 Unauthorized
      - 402 Payment Required
      - 403 Forbidden
      - 404 Not Found
      - 405 Method Not Allowed
      - 406 Not Acceptable
      - 407 Proxy Authentication Required
      - 408 Request Timeout
      - 409 Conflict
      - 410 Gone
      - 411 Length Required
      - 412 Precondition Failed
      - 413 Payload Too Large
      - 414 Request-URI Too Long
      - 415 Unsupported Media Type
      - 416 Requested Range Not Satisfiable
      - 417 Expectation Failed
      - 418 I'm a teapot
      - 421 Misdirected Request
      - 422 Unprocessable Entity
      - 423 Locked
      - 424 Failed Dependency
      - 426 Upgrade Required
      - 428 Precondition Required
      - 429 Too Many Requests
      - 431 Request Header Fields Too Large
      - 444 Connection Closed Without Response
      - 451 Unavailable For Legal Reasons
      - 499 Client Closed Request
    - 5×× Server Error
      - 500 Internal Server Error
      - 501 Not Implemented
      - 502 Bad Gateway
      - 503 Service Unavailable
      - 504 Gateway Timeout
      - 505 HTTP Version Not Supported
      - 506 Variant Also Negotiates
      - 507 Insufficient Storage
      - 508 Loop Detected
      - 510 Not Extended
      - 511 Network Authentication Required
      - 599 Network Connect Timeout Error
- The URL will be encoded using the `UTF-8` encoding scheme
  - `+` means a space only in `application/x-www-form-urlencoded` content, such as the query part of a URL.
- A CORS preflight request is a CORS request that checks to see if the CORS protocol is understood and a server is aware using specific methods and headers.
- A simple request does not use reflight check, itmeets all the following conditions:
  - One of the allowed methods:
    - `GET`
    - `HEAD`
    - `POST`
  - One of the following Content-Type header:
    - `application/x-www-form-urlencoded`
    - `multipart/form-data`
    - `text/plain`

##### Hyper Text Transfer Protocol Secure(HTTPS)

- It use port number 443.
- It is the secure version of HTTP.
- Communications between the browser and website are encrypted by two ways:
  - Secure Sockets Layer (SSL)
    - Website uses SSL certificate to identify itself and establish secure connections with clients.
  - Transport Layer Security (TLS)
    - It is the next generation of SSL.
- Digital certificates will be issued by certificate authorities(CAs) for SSL/TLS connection
- Each SSL/TLS connection begins with a “handshake” – the negotiation between two client and host that nails down the details of how they’ll proceed. The handshake determines what cipher suite will be used to encrypt their communications, verifies the server, and establishes that a secure connection is in place before beginning the actual transfer of data.

##### Simple Mail Transport Protocol(SMTP)

##### Post Office Protocol(POP)

##### Internet Message Access Protocol(IMAP)

##### Dynamic Host Configuration Protocol(DHCP)

- Is a protocol that automatically configure IP to a host
- It generates 6 messages
  - 4 mandatory messages
    - `DHCP Discocvery` broadcast to find DHCP
    - `DHCP offer` all DHCP server in the network reserver one IP address and sent a offer
    - `DHCP Request` Client confirm
    - `DHCP Ack` accepted server confirm. others server take the offer back and free its IP pool.
  - 2 non-critical messages
    - `DHCP Information` If the client need more information from the DHCP offer
    - `DHCP Release` The client tell the server to release its IP address when done.

## Basic Concepts

### Port Number

- It is used to marking destination and source devices
- Source port number is a random number in upper part of 65535
- Destination port number uses well-known port number.
  - A frame has both a source port number and a destination port number
- A socket is an IP address with a port number.
- Port numbers have a range between 0-65535.
- Port numbers are used to identify the type of application or services during data transmission.
- Here are Some standard port number.
  80 - Unsecured web browsing (http)
  443 - Secured web browsing (https)
  25 - Unsecured/secured sending of e-mail messages (smtp/smtp-s)
  110 - Unsecured/secured receiving of e-mail messages (pop/pop-s)
  143 - Unsecured/secured receiving of e-mail messages ( imap imap-s )
- There are (3) sub-ranges for stanrdrand port numbers
  - Well-known Ports: registered with a governing body(a.k.a. System Ports)
    - Range: 0 - 1,023
  - Registered Ports: registered by developer, can be used when no conflict.
    - Range: 1,024 - 49,151
  - Dynamic, Private, or Ephemeral Ports: not registered, for temp use. like web browser applications.
    - Range: 49,152 - 65,535

### Fully Qualified Domain Names

- A fully qualified domain name (FQDN) is the complete domain name for a specific computer, or host, on the internet.
- The FQDN consists of two parts: the hostname and the domain name.
  - For `www.example.com`. `www` is the hostname and `example.com` is the domain name.
- Top-level domain (TLD) is the last part of an URL. Ex, `.com`

### Domain Name Service(DNS)

- It is a distributed database system.
- It provides two services.
  - Forward lookups converts FQDN to IP address.
  - Reverse lookups converts IP address to FQDN.
- Steps
  1. For any FQDN, The host machine will check Local DNS record first.
     - For Window, it is located in `C:\Windows\System32\drivers\etc\hosts`.
     - For Linux, It is located in `/etc/hosts`.
  2. If not found. the host will ask the DNS resolver from its ISP(Internet Service Provider).
     - Private Resolver resolves private Domains
     - Public resolver resolves domains in the internet(ISP resolver and Google DNS)
  3. If the record not found in the Resolver's cache, The DNS resolver will ask the Root Server
     - There are 13 sets of root servers around the world.
  4. Root Server will tell resolver the corresponding TLD Server(Top level Domain) IP
  5. The TLD Server will tell the resolver which Authoritative name servers to ask.
  6. The authoritative name servers will provide the answer to the resolver.
  7. The resolver will send the request IP to the host.

## Network Devices

- Media Access Control is a unique physical address for each devices, it is hard-coded.
- MAC is a 12 digit hexadecimal value, there are two digit in one pair, consisted of 6 pairs.
- MAC address is a 12 X (Hexdecimal) 4 bit = 48 bit Number divided by : into 3 parts.
- All device port(network interface) have its own unique MAC address.
- All frame transmit data using above model to add headers for each one of them and strip the header according layer types.
- Nodes are connected by switches, wireless access points, and routers.
- collision domain - A collision domain is, as the name implies, the part of a network where packet collisions can occur.
  - A collision occurs when two devices send a packet at the same time on the shared network segment.
- Broadcast domain - A broadcast domain is the domain in which a broadcast is forwarded. A broadcast domain contains all devices that can reach each other at the data link layer (OSI layer 2) by using broadcast.

### Cable

- Twisted pair cable
  - Widely used for Enthenet in LAN.
  - It has two types:
    - Unshielded-Twisted-Pair (UTP) Cable - widely used everywhere.
    - Shielded-Twisted-Pair (UTP) Cable - used for industrial purpose.
  - RJ45 connector should be connected on each end of the cable.
  - use cable striper to remove the shield or skin of the cable.
  - use wire crimper to attach the RJ45 to the cable.
  - There are two wiring standards
    - T568A
    - T568B
      - more popular
  - The order of the cables has two types.
    - straight(patch) cable
      - two end of the cable used the same wiring standards
      - it is used to connect different types of devices.
    - crossover cable
      - two end of the cable used the opposite wiring standards.
      - it is used to connect same types of devices.
    - Auto MDIX is a technology that can auto convert between straight and crossover cable based on the current use cases.
  - Twisted pair cables have the following categories. Each has different Max speed.
    - CAT3 10Mbps
    - CAT5 100Mbps
    - CAT5e(enhanced) 100Mbps 125MHz
    - CAT6 1Gbps 250MHz
    - CAT6a 1Gbps 500MHz (10 Gbps under 100 meters)
    - CAT7(shielded CAT6a) 10Gps
    - CAT8 40Gps (under 30 meters)
    - Higher level has tigher twist, result in higher Max speed.

### Hub

- it copy info from 1 port to all port.
- 1 collision domain
- 1 broadcast domain

### Bridge

- It has more function that hub and less function than switch.

### Switch

- It has Application specific integration cicuitry(ASIC)
  - It learns Mac address of devices on CAM table(Address Learning)
- Many Collision Domains - 1 port a collision domains
- One or more broadcast domains - as many as the VLANs
- Manegement IP is the switch IP used for telnet connection
- It does not need power if it is not used as power source for devices(POE)
- works at layer two.
- Each on of its port has access mode that is used to connected to end devices, and trunk mode that connects to other switches.
  - Two switches connected in trunk mode will act like one combined switch.
  - There are two encapuslation protocal for trunking:
    - `802.1q` most used
    - `ISL` - inter switch link
- Dynamic Trunking Protocol is a Cisco Switch protocol that controls the port to be in either access mode or trunk mode. It has the following settings:
  - `Desirable` - It will start to negotiate trunk mode connection.
  - `Auto` - It accepts trunk mode connection.
  - `No Negotiate` - It won't accept trunk mode connection.
- Spanning Tree Protocol - It is used for loop avoidance. It detects if the network has duplicated connection that will causes layer-2 loops. It will disconnect thoese links logically.
- Forwarding Decision - A switch will have two types of forwarding decision:
  - `Cut Through` - forwarding immediately.
  - `Store & Forward` - wait to receive the entire frame then do error checking before forwarding.
- Virtual LAN(VLAN) - Logically separate ports, each group of ports in a VLAN is isolated from others.
  - Native VLAN - When a port is added to a VLAN it will have a tag, by default when a port has no tag it will be put in the native VLAN.
  - Each switch has a VLAN database, and there is a revision number starts at 0, it increment by 1 everything an change is made.
- VLAN Trunking Protocol(VTP) - it will copy and paste VLAN settings among all switches in trunk mode based on the highest revision number. There are three mode for VTP setting:
  - `Server` - For switch with `Server` setting, all the changes are made on this single switch.
  - `Client` - Other switches that accept updates from the `Server` switch.
  - `Transparent` - Turn VTP off on this switch.
- VTP Pruning - Stop transmitting traffic for a certain VLAN on the switch with VTP Pruning setting.

### Router

- Intelligent - only exchange info between different networks,
- Many Collision Domains
- Many broadcast Domains
- It has the ability to assign source and destination mac address according to the source and destination ip addresses if the IP addresses are from different sub networks.
- router is the only way for traffic goes in and out. it is the gateway and has a routing table.
- It works at layer three.
- Cyclic Redundancy Check(CRC) is the hash value attached to the beginning of the frame for error checking process before data is out and in the LAN. It is the job for routers to apply the hash algorithm and check if the hash value matches.
- Network Address Translation(NAT) is a router features that auto translate LAN IP and WAN IP address according to port number. In order to let private IPs share a common public IP because the number of public IPs are limited.
- Port Forwarding is an application of NAT that redirects a communication request from one address and port number combination to another while the packets are traversing a network gateway, such as a router or firewall.
  - It is commonly used for remote desktop connection using port number 3389.
- Cisco uses CEF Enhanced semi-hardware and semi-software structure to improve performance.
- Router uses software to control routing.
  - Routing can be static, the router make routing based on memorized rules.
  - Dynamic routing, the router make routing by itself.
- Dynamic routing have the following categories.
  - Internal Gateway Protocol - Used in LAN
    - RIP - routing based on distance, it belonds to distance vector type
      - RIP has two version `RIPv1` and `RIPv2`. Compared to the second version, the first version does not have supports VLSM(classless IP), authentication, and multicast.
      - It has for timer:
        1. update timer - the time interval for sending info about routes.
        2. flush timer - starts once no info is received about a route
        3. holddown timer - starts when invalid timer ran out.
        4. invalid timer - starts once no info is received about a route
      - It uses a hoop count that updated every 30 seconds to determine the distance.
      - When a connection is lost due to the delayed infomation, the router might still thinks there is a connection then devices lie to each other. This is called counting to infinity.
    - OSPF - routing based on speed, it belongs to link state type
    - EIGRP - combines the best of RIP and OSPF, Used by Cisco devices.
  - External Gateway Protocol - Used in WAN
    - BGP
    - EGP

### Firewall

- A firewall is designed to prevent unauthorized access to or from a network or host.  
  Network perimeter firewalls:
  Routes packets based on rules that define:
  what packets are allowed into internal networks and hosts
  what packets are allowed to leave the internal network and to what destination
  Host based firewalls:
  Used to define what incoming and outgoing network connections are allowed on that single host.
  Network firewalls cannot provide protection from traffic generated within a trusted network. Host based firewalls provide that second layer of protection.

#### Security zones

- scurity zones are discrete network segments containing systems that share common requirements (eg. Info, processes, security level, etc.)
- Developed to separate systems available to the public Internet from private systems in use by an organization
- These systems were separated by a firewall.

#### The Demilitarized Zone

- The DMZ is a network segment where systems accessible from the internet are placed, and which offers some basic levels of protection against attacks
  - DMZ systems are placed between two firewall devices that have different rule sets, which allow Internet access to services offered by the DMZ systems but not to the computers on the protected network
  - A third interface can be added to a single firewall, and the DMZ systems are placed on that network segment.

#### Firewall

- a device that filters traffic based upon established rules
- packet filters Firewall can act only on a combination of source IP address, destination IP address, and port numbers based only on the contents of the IP headerThey are fast and inexpensiveWork at the network layer of the OSI model.
  - some packet filter firewalls also maintain a record of the state in which network conversations are being conducted.
- Proxy-based Firewall
- In addition to packet filter, it inspects the data load portion of a packet and attempts to decide if the data fits the proxies requirements for such a conversationDue to this additional processing, they are slower than packet filters, and often cannot handle high network throughput
- Host Based Firewall
  - Work on the server.

#### Intrusion Detection Systems

- IDS compares network traffic or user patterns against databases of known attack fingerprints or signatures
- When an attack signature is matched, the IDS responds in one of two ways:
  - Passive IDS
    - Logs the details of the intrusion
    - Alerts an administrator that an event has occurred
  - Active IDS
    - Also refer to as Intrusion Prevention System (IPS)
    - Attempts to interrupt the attack or prevent further damage
    - May reset attackers connection or notify the firewall to deny packets from the attackers host
- It can be:
  - Network-based IDS
    - Monitor the network traffic streams for suspicious traffic patterns, matching against the database of know attack signatures
    - Cannot read encrypted traffic as it cannot be decrypted on the fly
  - Host-based IDS
    - Reside on the host and watch events from the view of the computer’s OS
    - As events occur, they are compared against their rules base, and if matched, an alert or action is issued
