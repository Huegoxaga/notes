# Networking

## Network

- Network is a group of two or more interconnected devices regardless of the distance of the devices
- Purpose of a network
  - To share information (e.g. documents, messaging)
  - To share resources (e.g. applications, printers, access to other networks)
- Network Types categorized by size:
  - `LAN` - Local Area Network
    - `Ethernet` - Ethernet is the most common LAN technology
    - It is limited to a small area and does not extend beyond a building
  - `CAN` - Campus Area Network
    - adopted by universities or large corps in a limited geographic area or beyond
    - A `CAN` is a form of a `MAN` that connects several `LAN`s together
  - `MAN` - Metropolitan Area Network
    - It is defined as a network that connects `CAN`s or `LAN`s across a city-wide geographic area
    - May use fibre optic or wireless
    - Could have a primary site
  - `WAN` - Wide Area Network
    - `Internet` - a net of WANs
    - Crosses metropolitan, regional, or national boundaries
    - Tiered (hierarchical) architecture
    - May use private or public network links
  - Non-Classical Types
    - Body Area Network (`BAN`)
      - Wearable computing and/or sensor devices
      - E.g. activity trackers, heart rate monitor, smart watches
    - Personal Area Network (`PAN`)
      - Devices such as PCs, tablets, smart phones, wearables, etc.
    - Internet Area Network (`IAN`)
      - Cloud network (virtualized), not associated with specific geographic locations such as a `WAN`
- Network Types categorized by function:
  - `SAN`- Storage Area Network
    - It provides systems with high-speed, lossless access to high-capacity storage devices.
  - `VPN` - Virtual Private Network
    - It allows for information to be securely sent across a public or unsecure network(public Internet). Common uses of a VPN are to connect branch offices or remote users to a main office.
- Measurement:
  - `network speeds` - it is represented by the slowest connection in between.
    - Bits and Byte
      - 8 bits = 1 byte
      - 1024 Byte = 1 KB
      - 1024 Bits = 1 Kb
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
    - Peer-to-Peer - all hosts on the network can both request and provide data and services
      - Network has no central servers
      - Each node can be both a client and a server
      - Distributed, no single point of failure
      - Hybrid P2P networks have servers for performing certain functions Examples: Blockchains
    - Client/Server - hosts are assigned specific roles. Clients request data and services stored on servers
      - Clients request data or resources
      - Servers wait for and respond to the requests from clients
      - Typically, software is specialized to the server role or the client role
      - A server can be stateless or stateful in nature
        - stateful track the status of a client
        - stateless can be a web app without the use of cookies
      - Generally, client/server networks are more secure and scalable
    - Mainframe/Terminal - a single device (the mainframe) stores all data and services for the network.
- Topology:
  - It is the arrangement of the elements of a communication network.
  - Types:
    - `Bus` - share one cable
      - Nodes are connected to a shared communication line/medium (the "bus")
      - Simple and inexpensive, typically uses less cable than other topologies (e.g. one coaxial cable is used)
      - However, collisions can occur due to the shared communication medium (e.g. 10Base Ethernet)
    - `Star` - share one core switch
      - Nodes are connected to a central device
      - Easy to implement and extend by adding more nodes
      - More fault-tolerant than the bus topology
      - However, the central device is a single point of failure
    - `Ring` - connected one by one
      - Each node is connected to two and only two other nodes
      - Messages/data travel around the ring in one direction
      - The transmission time can be deterministic in a ring topology
      - However, adding or removing a node is difficult
    - `Mesh` - devices connected to each other
      - Each node is connected to all the other nodes
      - Very fault-tolerant as a result
      - For `N` number of nodes, the number of links required is `N(N-1)/2`
      - The most expensive and complex topology
    - `Wireless`
      - Typically uses radio frequency (RF) transmissions
      - An alternative is infrared (IR) transmissions
      - Ad hoc (autonomous, no central device) and infrastructure (access point) topologies
      - "Space" is considered the shared medium
      - Allows mobility of nodes in the network
    - `Hybrid` - a combination of any of above
      - Hybrid topologies blend two or more of the "classical" topologies
      - Most networks are deployed as hybrids, realizing both the pros and cons of each type used
      - Variations are also possible between physical and logical topologies, e.g. Token Ring, partial mesh, etc.
        - IBM’s Token Ring operated as a logical ring topology, using a modified physical star topology
        - Partial mesh networks provide significant redundancies, but also do not exhaustively connect all nodes

## Network Reference Models

- It is used to divide and break down a complicated network system into layers
- It is used to standardize networks

### OSI model

- The Open Systems Interconnection (OSI) model.
- Developed by International Organization for Standardization(ISO), because devices from IBM is not compatible with Digital Equipment Corp.(DEC) products
- Mnemonic: `Please Do Not Throw Sausage Pizza Away`
- 2, 3, 4 layers all have its own header
  - when data goes to lower layer one extra header will be added
  - when data goes to higher layer related header will be processed and removed
  - a segement will have one transport layer header followed by the application layer data
  - a packet will have a internet layer header followed by a transport layer header, then the application layer data
  - a frame will have link layer header, internet layer header and transpoer layer header, the application data followed by link layer trailer
  - The application layer data is the core
- From layer one to layer seven, they are:

#### Physical Layer

- present data as bit, all hardwares likes cables and wires are in the physical layer.
  - This is where the actual data transmission happens
  - Defines the physical and electrical specifications (as appropriate) for the transmission media
    - Media type, connector type, signaling type
    - Includes pin layouts, voltages, cable specifications, etc.
  - Functions and services of the physical layer:
    - Establishes/terminates a connection to the medium
    - Participates in resolving contention/flow control
    - Modulates the digital data (bits) into signals suitable for the transmission channe

#### Data Link Layer

- a functional and procedural means to transfer data as `frames` with MAC address in the data link header. It will also handle error checking for physical layer
- A frame is a Layer 2 Protocol Data Unit (PDU)
- Can Split into two sub-layers:
  - Logical Link Control (LLC)
    - Recognizes start/end of frames in the bitstream
    - Delimits frames when transmitting
    - Handles the Frame Check Sequence (FCS)
    - Inserts the source/destination MAC addresses into frames
    - It specifies:
      - Preamble: 7-byte value, e.g. 10101010...
      - Start of Frame Delimiter (SFD): 1-byte value, e.g. 10101011
        - Immediately follows the preamble
        - Signals the start of a new frame
        - Start of frame immediately follows the SFD
      - Frame Check Sequence
        - Cyclic Redundancy Check (CRC-32) value
        - Checksum used to detect whether any data was lost or altered during transit
      - Inter-Frame Gap (IFG): 12 bytes (idle channel)
  - Media Access Control (MAC) - Lower sublayer
    - Manages control of access to the physical transmission medium
    - Media Access Control(MAC) address is a unique physical address for each devices, it is hard-coded.
    - MAC is a 12 digit hexadecimal value, there are two digit in one pair, consisted of 6 pairs.
    - MAC address is a 12 X (Hexdecimal) 4 bit = 48 bit Number divided by : into 3 parts.
    - All device port(network interface) have its own unique MAC address.
    - Considered "burned in" at the factory
      - Can be, but is not typically changed
    - For virtual machine vNICs, they are selected from a pool, from the vendor’s OUI
    - first 3 bytes stores the organizationally unique identifier (OUI), last 3 bytes are NIC specific
      - Wireshark OUI Lookup Tool: https://www.wireshark.org/tools/oui-lookup.html
      - OUI are registered through IEEE Registration Authority: https://regauth.standards.ieee.org/standards-ra-web/pub/view.html
    - Broadcast MAC address: FF-FF-FF-FF-FF-FF (all ones)
    - CSMA/CD for IEEE 802.3 Ethernet, Carrier Sense, Multiple Access (CSMA)
      - To ensure one singal is being transferred at a time, with Collision Detection (CD)
      - 32-bit jam signal sent when a collision is detected (101010...)
      - Stations use an exponential back-off algorithm to pause and resend until successful
      - Stations require 2tprop to capture the channel and ensure exclusive access
        - otherwise it will be to late for the devices to realize the collision, becuase they are too far away from each other

#### Network Layer

- present data as `Packet` and add IP address in the packet header. It naviagtes and find the best path for data transmition if the destination address is not in the local subnet
- Each packet in the conversation will have the same source and destination addresses, however they may not take the same path
- Translates logical addresses into physical (MAC) addresses
- Provides Quality-of-Service (QoS) markers to indicate traffic priority

#### Transport Layer

- present data as encapsulated `Segement` with header. It is responsible for end-to-end data transfer and connection establishment. It decides which data transmition protocol to use and add a port number and a random source port number to the IP address.

#### Session Layer

- Controls the establishing, managing, and ending of a session between two hosts
- Provides full-duplex and half-duplex dialogue
- Enhances a reliable transfer service
- Provides checkpoints and synchronization for error recovery

#### Presentation Layer

- the layer generify data, it is where files are generated from session data. It formats and codes data to present a standard interface to the application layer
- Examples of Presentation Layer functions:
  - MIME encoding/decoding of content (e.g. base64, 7bit)
  - Data compression/decompression (e.g. gzip, deflate)
  - Data encryption/decryption (e.g. RSA, AES)
  - Character set conversion (e.g. ASCII, UTF-8, UTF-16, ISO 8859-1

#### Application Layer

- the point of contact for network aware application

### TCP/IP model

- Also known as IP stack
- Developed by the Department of Defense.
- A simplified version of OSI and now become the industry standart
  1. Network Interface or Link - equivelent to OSI model 1 and 2
  2. Internet - equivelent to OSI model 3
  3. Transport - equivelent to OSI model 4, 5
  4. Application - equivelent to OSI model 6, 7
     - This layer is handled by the operating system and will not be discussed by network engineer.
- Mnemonic: TCP/IP comes in `A TIN`.

## Protocols

### Physical Layer Protocols (Line Coding Schemes)

- Line codes are used in digital transmission
- The code is tuned to the properties of the channel
- Digital signal is encoded into a pattern, e.g. NRZ, Bipolar, Manchester, etc.
- Receiver can also use the line code to synchronize its clock signal
- Line coding can also assist in error detection (e.g. receiving a "non-existent" code)
- main line coding schemes used for Ethernet
  - 4B5B, used by Fast Ethernet
  - 4D-PAM5, used by Gigabit Ethernet over copper
  - 8b/10b, used by Gigabit Ethernet (non-copper)

#### 4B5B Line Code

- Used in Fast Ethernet
- Maps groups of 4 bits into 5-bit symbols
- 4 bits: 16 data patterns
- 5 bits: 32 symbols, extra symbols can be used for error detection or control characters
- Transitions in the analog signal provide clocking information to the receiver
- Requires 25% extra bandwidth due to the extra bit per symbol

#### 4D-PAM5 Line Code

- Used in Gigabit Ethernet over Copper
- Recall that Gigabit Ethernet over Copper (1000BaseT) uses all 4 twisted-pairs
- 4-Dimensional due to the use of all pairs
- PAM5 from use of 5 symbol levels: -2, -1, 0, +1, +2
  - Which map to -1V, -0.5V, 0, +0.5V, +1V
- 5x5x5x5 = 54 = 625 possible symbols
- 8-bit words require 28 = 256 symbols
- Therefore, this allows full redundancy + 113 control symbols in the coding scheme

#### 8b/10b Line Code

- Used in Gigabit Ethernet, non-copper
- Maps groups of 8 bits into 10-bit symbols
- Low 5 bits are encoded into a 6-bit group
- High 3 bits are encoded into a 4-bit group
- Same properties from 4B5B apply
- Synchronized clocking is vital for high data rates
- Encoding is performed in hardware using a look-up table (LUT)

### DataLink Layer Protocols

#### Address Resolution Protocol (ARP)

- Data transmition in the data link layer uses MAC addresses to find destination.
- This protocol is used to find MAC address of the destination device in a local network before sending the data.
  - If destination IP is not local the ARP request will be sent to the gateway.
- It is achieved by broading the destination IP address to all devices in the network.
- only device with the request Mac address will reply
- ARP Header Format
  - Hardware Type: 1 for Ethernet
  - Protocol Type: 0x0800 for IPv4
  - Hardware and Protocol Address Length fields: specified in bytes
  - Opcode: defines a request (1), a reply (2), and others
  - Source/Destination Hardware/Protocol Address fields: variable lengths based on headers
  - Data: further data (optional)
  - ARP is not encapsulated by IP (it is directly encapsulated by L2 frames)

#### Ethernet

- An Ethernet frame is the one type of L2 PDU
- Ethernet Frame Formats [Ethernet Frames](img/ether-frames.jpg)
  - Ethernet II (DIX v2), i.e. “Ethernet Type II”
  - IEEE 802.3 Ethernet (original – rarely used)
  - IEEE 802.3 Ethernet with SNAP header
- Minimum Ethernet frame size: 64 bytes
- Maximum Transmission Unit: 1518 bytes (not including "jumbo frames")
- Ethernet II is the most common type
  - DIX: DEC, Intel, Xerox jointly developed this format
  - Uses an EtherType field to define the upper-layer protocol
- EtherType/Length Field
  - Values from 0-1500 in this field indicate the length of the frame (IEEE 802.3 format)
  - Values of 1536 (0x600) and higher in this field indicate the EtherType sub-protocol identifier (DIX v2)
  - E.g. a value of 0x0800 indicates IPv4 is the Ethernet frame payload’s protocol
  - The length of the frame could be calculated from using delimiter symbols or encapsulated payload headers, e.g. with IP header information
- Today, networks support both DIX v2 and IEEE 802.3 frames simultaneously
  - IEEE 802.2 LLC header fields: DSAP, SSAP, Control
  - DSAP: Destination Service Access Point and SSAP: Source Service Access Point
    - These fields identify the contents/protocol of the data
    - E.g. DSAP=SSAP=0xAA means the 802.3 format with SNAP
  - Control: always 0x3 for the 802.3 format with SNAP
- SNAP: Sub-Network Access Protocol
  - The 1-byte SAP fields do not accommodate all of the available protocols; hence, purpose of the SNAP
  - SNAP is comprised of:
    - A 3-byte OUI (mostly unused)
    - A 2-byte protocol type field (essentially the same as EtherType, e.g. 0x0800 = IPv4)
  - Current frame formats use the joint EtherType/Length definition to identify the type of frame received

### Network Layer Protocols

#### ICMP protocol

- Internet Control Message Protocol
- ICMPv4 for IPv4 (similarly, ICMPv6 for IPv6)
- Provides control and messaging capabilities
- Sends error and control messages
- Examples: Destination Unreachable, Time Exceeded, Echo Request/Reply, etc.
- ICMP is encapsulated by IP, but is considered to be in the same layer (L3)
- Depending on ICMP message type, extra fields may be included to carry more information
- ICMP Header Format
  - Type: specifies the format of the ICMP message
  - Code: further information about the message
  - Checksum: integrity check for the header
  - Rest of Header: specific to the type of the messages
  - E.g. “ping”: ICMP Echo Request (type 8)/Echo Reply (type 0), Data
  - ICMP Echo also includes Identifier and Sequence Number fields following the Checksum

#### Internet Protocol

- Internet Protocol (IP) is the logical address of devices.
- Responsible for packet delivery and routing
- Address allocation is managed by IANA and the RIRs

##### IPv4

- A group of 4 octets (8-bit) data with a total of 32 bits.
- 4.3 billions unique addresses available.
- IPv4 can be presented in dotted decimal notation: `130.132.19.31`. It can be converted to binary form as `10000010.10000100.00010011.00011111`.
- Subnet Mask
  - It has network ID in the left portion and node ID in the right portion combined.
  - Subnet Mask is used to determine which part of the IP is network ID.
    - network ID is represented by subnet mask 1 value digit place. For an ip with a mask as `11111111.11111111.00000000.00000000` -> `255.255.0.0`, the first two groups of octets, represents networkID.
  - For `192.168.0.1/24` The number followed means the first n number is the networkID. This type of notation is called classless IP address (CIDR) notation the number after `/` is called network prefix
- Among all the hosts in a network, the first IP is the network ID. The last one is the boardcast ID.
- Gateway IP is the IP address of a router
  - The network ID portion of the gateway IP and all other IP addresses in the same local network should be the same
- IPv4 address can be devided into different classes according to its first octet, each class has a different default mask value.
  - class A: `1.0.0.0 - 126.255.255.255/8`
  - class B: `128.0.0.0 - 191.255.255.255/16`
  - class C: `192.0.0.0 - 223.255.255.255/24`
  - class D(multicast): `224.0.0.0 - 239.255.255.255`
  - class E(experimental purpose) `240.0.0.0 - 255.255.255.255`
- Subnetting is achieved by have 1 more bit of subnet mask compare to its IP class default mask.
  - One network can do subnetting with different CIDR value, it is called Variable Length Subnet Mask(VLSM), e.g. subnets with network ID `192.168.1.0/25`, then `192.168.1.128/26` and `192.168.1.192/26`
- Supernetting is lending bits to represent a larger network. it is a summarization of ip addresses from a range of adjacent small subnets
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
- Broadcasts (three types)
  - Flooded broadcast (255.255.255.255)
    - Not propagated, considered a local broadcast
  - Directed broadcast (e.g. 192.168.2.255 for subnet 192.168.2.0/24)
    - All hosts on a specific subnet (host bits all 1)
  - All subnets broadcast (e.g. 192.168.255.255 for network 192.168.0.0/16)
    - All hosts on all subnets in a specific network
    - Subnet and host bits all 1
- IPv4 Header Fields
  - Version: IP version number (we consider version 4 only, “0100”)
  - Internet Header Length: length in 32-bit words
  - DSCP: Differentiated Services Code Point, indicates traffic class/priority
  - ECN: Explicit Congestion Notification, RFC 3168
  - Total Length: length of the IP header + the data (payload) in bytes
  - Identification: unique to identify a group of IP packet fragments
  - Flags: specifies IP fragmentation options
  - Fragment Offset: indicates the position of a fragment, relative to the complete group of fragments
  - Time-to-Live: maximum hop count
  - Protocol: defines the protocol used in the data portion
    - E.g. Protocol = 6 for TCP, 17 for UDP, 1 for ICMP
  - Header Checksum: integrity check for the header only
  - Source Address: 32-bit source IP address
  - Destination Address: 32-bit destination IP address
  - Options: optional field, size must be a multiple of 32-bit words (padding added if necessary)
  - The data (payload) immediately follows the IP header
- Fragmentation
  - Maximum Transmission Unit (MTU) - Ethernet II MTU is 1518 bytes (maximum frame size), L3 packet payload maximum is 1500 bytes
  - Larger packets must be fragmented
  - Fragments are forwarded and routed independently
  - Reassembly is performed at the destination
  - Fragmentation information is carried in the IP header
  - If any fragments are lost, all received fragments must be discarded
  - Timer is set when the first fragment is received, If the timer expires before all fragments are received, the others will be discarded
  - Flags: 1 bit: reserved (always 0); 1 bit: don’t fragment (DF); 1 bit: more fragments (MF)
  - If the packet length > MTU and DF is set, the packet must be dropped
  - First fragment: offset of 0 (byte position #0)
  - Offset: indicates the number of 8-byte units for the current fragment
  - Length of a fragment (except the final one): therefore must be a multiple of 8 bytes
  - Example: 6500 bytes of data to transmit
    - Ethernet Type II MTU is 1518 bytes (maximum Ethernet frame size), IP header is 20 bytes (without options)
    - Maximum usable data per packet: 1518 – 18 (frame header) – 20 (IP header) = 1480 bytes
    - We can use 185 x 8 = 1480-byte fragments; requires 5 packets in total (4 x 1480 bytes, 1 x 580 bytes)

##### IPv6

- 8 group of 4 hexadecimal values, delimited by colon
- 0s can be group and simplified.
- ::1 is loopback

### Transport Layer Protocols

#### Transmission Control Protocol(TCP)

- TCP is a connection oriented transmission.
- Responsible for establishing and maintaining network conversations
- It breaks the session data into packets and passes packets the network layer.
- It receives packets from the network layer, verifies and assembles them for delivery to the receiving application
- Its data unit is called segment
- It is more reliable than UDP
  - TCP uses a three-way handshake to establish a reliable connection.
    1. SYN package
    2. SYN/ACK package
    3. ACK package
- Windowing - It is the trail process for testing the max packages can be sent at the same time using TCP connection.

#### User Datagram Protocol(UDP)

- It is a connectionless transmission.
- Its data unit is called datagram
- It is an alternative communications protocol to Transmission Control Protocol (TCP) used primarily for establishing low-latency and loss-tolerating connections between applications on the internet. It is faster than TCP.

### Presentation Layer Protocols

#### TLS

#### SSL

### Application Layer Protocols

#### Hypertext Transport Protocol(HTTP)

- It uses port 80.
- HTTP is called a stateless protocol because each command is executed independently, without any knowledge of the commands that came before it.
- HTTP Request
  - It has request methods as `POST`, `GET`, `PUT` etc.
  - `GET` request cannot have request body, the parameter can only be encoded at the end of the request url
  - Request header content type decide the content type of the request body
    - On the server side, `Access-Control-Allow-Headers` need to be setup to allow certain headers in request.
    - `"Cache-Control", "no-cache"`, `"Pragma", "no-cache"` can be used to disable client side broswer cache
- It has a Authentication realms for authentication, it accepts the following types in the authorization header
  - `Basic Auth`: `Basic Base64Encoded(username:password)`
  - `API Key`: `Token <API_Key>`
  - `Bearer Token`: `Bearer <JWT_Token>`
- HTTP Response
  - The response message contain:
    - a status line which includes the status code and reason message (e.g., HTTP/1.1 200 OK, which indicates that the client's request succeeded)
    - response header fields
      - Content-Type:
        - `text/html`
        - `image/jpeg` request url can be used to retrive or download image
          - images can be based64 encode strings, with request parameter `isBase64Encoded` set to `True`
        - [Click Here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types) to see a list of common content type
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
      - 204 No Content (no message body)
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
      - 500 Internal Server Error(backend program has unhandled exceptions)
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
  - `+` means a space only in `application/x-www-form-urlencoded` content, such as the query part of a URL
- Same-origin policy controls interactions between two different origins
  - Same-origin means two sites have identical domian, protocol, and port
  - `CORS` is used to allow cross-origin access, it opens a backdoor for same-origin policy
    - A CORS preflight request is a CORS request that checks to see if the CORS protocol is understood and a server is aware using specific methods and headers.
- HTTP Cookies (web cookie, browser cookie) - is a small piece of data that a server sends to the user's web browser
  - A cookie stores a key-value pair data which is limited to 4KB
  - it is sent automatically along with HTTP requests if the following conditions satisfied
    - The cookie still exists, based on its lifetime definition
      - `Session cookies` are deleted when the current session ends
      - `Permanent cookies` are deleted at a date specified by the `Expires` attribute, or after a period of time specified by the `Max-Age` attribute
    - The restricted access of the cookie
      - A cookie with the Secure attribute is sent to the server only with an encrypted request over the HTTPS protocol
      - A cookie with the HttpOnly attribute is inaccessible to the JavaScript Document.cookie API; it is sent only to the server
    - The applicable `Domain` and `Path` for the cookie, or the defined `SameSite` attribute
  - Local storage and session storage are used to store data for the web app only, as their contents are not sent through HTTP requests
    - Local storage persists while session storage is cleared at the end of each session
- A simple request does not use reflight check, itmeets all the following conditions:
  - One of the allowed methods:
    - `GET`
    - `HEAD`
    - `POST`
  - One of the following Content-Type header:
    - `application/x-www-form-urlencoded`
    - `multipart/form-data`
    - `text/plain`

#### Hyper Text Transfer Protocol Secure(HTTPS)

- It use port number 443.
- It is the secure version of HTTP.
- Communications between the browser and website are encrypted by two ways:
  - Secure Sockets Layer (SSL)
    - Website uses SSL certificate to identify itself and establish secure connections with clients.
  - Transport Layer Security (TLS)
    - It is the next generation of SSL.
- Digital certificates will be issued by certificate authorities(CAs) for SSL/TLS connection
- Each SSL/TLS connection begins with a “handshake” – the negotiation between two client and host that nails down the details of how they’ll proceed. The handshake determines what cipher suite will be used to encrypt their communications, verifies the server, and establishes that a secure connection is in place before beginning the actual transfer of data.

#### Simple Mail Transport Protocol(SMTP)

#### Post Office Protocol(POP)

#### Internet Message Access Protocol(IMAP)

#### Dynamic Host Configuration Protocol(DHCP)

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

#### FTP

#### TFTP

#### SNMP

#### DNS

## Basic Concepts

### Port Number

- It is used to marking destination and source devices
- Source port number is a random number in upper part of 65535
- Destination port number uses well-known port number.
  - A frame has both a source port number and a destination port number
- A socket is an IP address with a port number.
- Port numbers have a range between 0-65535.
  - Application can use port range from 1025 to 65535
- Port numbers are used to identify the type of application or services during data transmission.
- Here are Some standard port number.
  - `80` - Unsecured web browsing (http)
  - `443` - Secured web browsing (https)
  - `25` - Unsecured/secured sending of e-mail messages (smtp/smtp-s)
  - `110` - Unsecured/secured receiving of e-mail messages (pop/pop-s)
  - `143` - Unsecured/secured receiving of e-mail messages ( imap imap-s )
  - Standard port numbers used by TCP and UDP are different or sometimes shared
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

- All frame transmit data using above model to add headers for each one of them and strip the header according layer types.
- Nodes are connected by switches, wireless access points, and routers.
- collision domain - A collision domain is, as the name implies, the part of a network where packet collisions can occur.
  - A collision occurs when two devices send a packet at the same time on the shared network segment.
- Broadcast domain - A broadcast domain is the domain in which a broadcast is forwarded. A broadcast domain contains all devices that can reach each other at the data link layer (OSI layer 2) by using broadcast.

### Cables

- All cables and its connectors are layer one devices

#### Twisted Pair Cable

- Widely used for Enthenet in LAN.
- Consists of several individually-insulated wires twisted together in coloured pairs
- Wire pairs are twisted together to reduce crosstalk and noise
  - Interference will be picked up by both wires
  - Difference between the pair will be minimal
  - Twisting also reduces crosstalk
  - Flat ribbon cables with parallel wires are limited to short distances for these reasons
- May be shielded and/or screened, or unshielded
- It has two types:
  - Unshielded-Twisted-Pair (UTP) Cable - widely used everywhere
  - Shielded-Twisted-Pair (STP) Cable - used for industrial purpose
  - Screened UTP (ScTP) - surrounded by a shield of foil and includes a single drain wire used for grounding
- RJ45, or 8P8C (8 Position, 8 Conductor) connector should be connected on each end of the cable.
- use cable striper to remove the shield or skin of the cable.
- use wire crimper to attach the RJ45 to the cable.
- There are two wiring standards
  - T568A
  - T568B (more popular)
- The order of the cables has two types
  - straight(patch) cable
    - two end of the cable used the same wiring standards
    - it is used to connect different types of devices.
  - crossover cable
    - two end of the cable used the opposite wiring standards.
    - it is used to connect same types of devices.
  - Auto MDIX is a technology that can auto convert between straight and crossover cable based on the current use cases.
- Twisted pair cables have the following categories. Each has different Max speed.
  - CAT1 - 2 pairs of wires, used by PSTN, ISDN, doorbell wiring
  - CAT2 - 4 pairs of wires, Uncommon, used by 4 Mbps Token Ring
  - CAT3 - 4 pairs of wires, 16 MHz Bandwidth, used by 10Mbps Ethernet
  - CAT4 - 4 pairs of wires, 20 MHz Bandwidth, Uncommon, used by 16 Mbps Token Ring
  - CAT5 - 4 pairs of wires, 100 MHz Bandwidth, used by 100Mbps Ethernet
  - CAT5e(enhanced) - 4 pairs of wires, 125 MHz Bandwidth, used by 100 Mbps Fast Ethernet, 1 Gbps Gigabit Ethernet
  - CAT6 - 4 pairs of wires, 125 MHz Bandwidth, used by 1 Gbps (100 metres), 10 Gbps Ethernet (55 metres)
  - CAT6a - 4 pairs of wires, 500 MHz Bandwidth, used by 10 Gbps Ethernet (100 metres)
  - CAT7(shielded CAT6a) - 4 pairs of wires, 10Gps
  - CAT8 - 4 pairs of wires, 40Gps (under 30 meters)
  - Higher level has tigher twist, result in higher Max speed.
- In general TPC hasL
  - Limited bandwidth (typically 100-500 MHz)
  - Maximum distance: typically 100 metres for Ethernet applications
- In Fast Ethernet over Category 5/5e, only 2 pairs are used for transmit/receive
- In Gigabit Ethernet, all 4 pairs are used

#### Coaxial Cable

- Consists of an outer jacket, outer conductor (copper braid), insulating spacer (plastic/Teflon), and a centre conductor (copper wire)
- High frequency signal transmission line
- Capable of carrying broadband services (e.g. analog/digital TV, Internet, phone)
- Types of coaxial cables:
  - `RG-6/U`, also known as `CATV`, uses Copper-coated steel (75 Ω)
  - `RG-8` also known as `Thicknet`, adopted by `10Base5` Ethernet, uses Solid copper (50 Ω)
  - `RG-58`, also known as `Thinnet`, adopted by `10Base2` Ethernet, uses Stranded copper (50 Ω)
- It has minimal external interference effects
- Provides a significant amount of bandwidth (1-3 GHz)
- Capable of up to 10 Gbps downstream (DOCSIS 4.0)
- Relatively expensive compared to UTP
- Supports longer cable runs
  - `10Base2` – up to 185 metres
  - `10Base5` – up to 500 metres
- HFC (hybrid fibre-coaxial) networks – typically >100 metres
- Not often used for data networks today, except "last mile" in existing cable infrastructure
- It uses connectors:
  - F-connector
  - BNC with terminators

#### Fibre-Optic Cable

- Consists of a glass core, cladding, protective buffer, and an outer sheath
- The core is a waveguide that can transmit light of varying wavelengths through WDM
- Total internal reflection keeps light in the waveguide
- Immune to Electro-Magnetic Interference (EMI) and Radio frequency interference (RFI)
- High bandwidth, high electrical resistance
- Smaller cable size (diameter), lightweight but fragile
- More difficult to install/splice
- More expensive than coaxial cable/UTP
- Single-mode (SM)
  - Optical fibre with a small core diameter, e.g. 9 μm
  - Greater distances possible, e.g. over 60 km
  - Higher precision/stricter tolerances
- Multi-mode (MM)
  - Optical fibre with a larger core diameter, e.g. 50 or 62.5 μm
  - Distances up to 550 metres for 1 Gbps Ethernet
  - Best used within a building (shorter runs)
- Fibre-Optic Connectors
  - ST – Straight Tip, simplex
    - For simplex cables, Rx/Tx cables are separable
  - SC – Subscriber Connector (sometimes called Square Connector), simplex and duplex
  - LC – Lucent Connector, typically duplex
    - Common in data networking applications along with (but increasingly displacing) SC
- Small Form-factor Pluggable (SFP/SFP+) Transceivers
  - Often used in conjunction with fibre connectors

### Network Interface Controller/Card/Chipset (NIC)

- Also called a network chipset or network adapter
- Allows a device (such as a computer, tablet, etc.) to connect to a network
- Contains (or emulates) electronic circuitry needed to communicate on the network
- A network chipset is designed for wired or wireless operation
- May be physical (both discrete and embedded), or virtual
- has a 48-bit MAC address

### Space

- Space is the "physical medium" for wireless signal transmission, examples:
  - IEEE 802.11 Wi-Fi (Wireless LAN)
  - IEEE 802.16 Wireless MAN (WiMAX)
- Uses radio frequency (RF) signals (electromagnetic waves)
  - Bluetooth and 802.11b/g/n/ax Wi-Fi: 2.4 GHz band
  - 802.11a/n/ac/ax Wi-Fi: 5 GHz band
- WiMAX: Worldwide Interoperability for Microwave Access
  - 2 – 66 GHz range (physical layer specification)
  - Spectrum profiles of 2.3, 2.5, and 3.5 GHz
  - Meant to deliver "last mile" broadband services
- Flexible, inexpensive to deploy, but subject to interference
- Isotropic Antennas
  - Omnidirectional: the most common type
  - Transmits data (signal power) equally in all directions
  - Suitable for multiple receivers
  - E.g. radio, Wi-Fi, cellular, etc.
- Directional Antennas
  - Focus transmission power in one direction or a narrow arc/cone
  - Usually must maintain "line of sight"
  - Most suitable for a single receiver, provides superior noise rejection
  - E.g. satellite

### Hub

- it copy info from 1 port to all port.
- 1 collision domain
- 1 broadcast domain
- A physical layer device

### Bridge

- It has more function that hub and less function than switch
- A data link layer device
- Connects (usually) two similar segments together
- Separates data (Ethernet frames) and partitions the collision domain
- Performs forwarding and filtering with a MAC table called bridging table
  - Forwards the message if the destination is on the “other” side
  - Filters the message if the destination is known to be on the “same” side
  - Builds a table of MAC addresses to learn where hosts are located

### Switch

- It has Application specific integration cicuitry(ASIC)
  - It learns MAC addresses of devices on CAM table(Address Learning)
- Many Collision Domains - 1 port can be a collision domain
- One or more broadcast domains - as many as the VLANs
- Manegement IP is the switch IP used for telnet connection
- It does not need power if it is not used as power source for devices(POE)
- A data link layer (Layer 2) device
- Forwarding strategies used:
  - Store and forward - most conservative, buffer the entire frame by receiving, verifying, and forwarding each frame
  - Cut through - most aggresive with highest performance, forwarding frame once destination MAC address is received
  - Fragment free - like cut through but only transmit frame larger than 64 bytes to prevent transmitting corrupted, runt frame
  - Adaptive - switch between the above three depending on the network conditions
- Each on of its port has access mode that is used to connected to end devices, and trunk(attack) mode that connects to other switches.
  - Two switches connected in trunk mode will act like one combined switch.
  - There are two encapuslation protocal for trunking:
    - `802.1q` most used
    - `ISL` - inter switch link
- Dynamic Trunking Protocol is a Cisco Switch protocol that controls the port to be in either access mode or trunk mode. It has the following settings:
  - `Desirable` - It will start to negotiate trunk mode connection.
  - `Auto` - It accepts trunk mode connection.
  - `No Negotiate` - It won't accept trunk mode connection.
- Spanning Tree Protocol - It is used for loop avoidance. It detects if the network has duplicated connection that will causes layer-2 loops. It will disconnect those links logically.
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

- Intelligent - only exchange info between different networks, it is the gateway in most cases
- Many Collision Domains
- Many broadcast Domains
- Operates using IP addresses
  - It has the ability to assign source and destination mac address according to the source and destination ip addresses if the IP addresses are from different sub networks.
- router is the only way for traffic goes in and out. it is the gateway and has a routing table
  - Routing table is a `Forwarding Information Base` (`FIB`)
- It works at layer three (network layer)
  - It forwards (routes) packets toward the destination
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
