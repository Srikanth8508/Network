# Computer Networking -- Beginner to Advanced

## Focus: Network Devices, Networking Fundamentals and Linux Networking

**Audience:** Beginners progressing toward practical Linux system
administration and networking troubleshooting\
**Scope:** Network concepts, devices, protocols, IP addressing,
subnetting, routing, switching, security fundamentals, Linux networking,
diagnostic tools and hands-on labs.

> **Out of scope:** AWS, Docker, Kubernetes and cloud/container
> networking. This guide concentrates on conventional computer networks
> and Linux hosts.

------------------------------------------------------------------------

# Table of Contents

1.  [Learning roadmap](#1-learning-roadmap)
2.  [Networking fundamentals](#2-networking-fundamentals)
3.  [Network types and topologies](#3-network-types-and-topologies)
4.  [Network devices](#4-network-devices)
5.  [How communication works](#5-how-communication-works)
6.  [OSI and TCPIP models](#6-osi-and-tcpip-models)
7.  [Ethernet, MAC addresses and
    switching](#7-ethernet-mac-addresses-and-switching)
8.  [IP addressing](#8-ip-addressing)
9.  [Subnetting and CIDR](#9-subnetting-and-cidr)
10. [Routing and gateways](#10-routing-and-gateways)
11. [Core network protocols](#11-core-network-protocols)
12. [Ports and common services](#12-ports-and-common-services)
13. [Network security fundamentals](#13-network-security-fundamentals)
14. [Linux networking fundamentals](#14-linux-networking-fundamentals)
15. [Linux network configuration](#15-linux-network-configuration)
16. [Linux routing, DNS and
    firewalling](#16-linux-routing-dns-and-firewalling)
17. [Network troubleshooting tools](#17-network-troubleshooting-tools)
18. [Practical Linux networking
    labs](#18-practical-linux-networking-labs)
19. [Troubleshooting scenarios](#19-troubleshooting-scenarios)
20. [Interview questions](#20-interview-questions)
21. [Quick reference sheets](#21-quick-reference-sheets)
22. [Learning plan](#22-learning-plan)
23. [Glossary](#23-glossary)

------------------------------------------------------------------------

# 1. Learning roadmap

Study the topics in this order:

  -----------------------------------------------------------------------
  Stage                   Topics                  Outcome
  ----------------------- ----------------------- -----------------------
  1\. Fundamentals        Networks, devices,      Understand what a
                          topology, communication network is

  2\. Models              OSI, TCP/IP,            Understand how data
                          encapsulation           travels

  3\. Addressing          MAC, IPv4, IPv6, subnet Identify hosts and
                          masks, CIDR             networks

  4\. Switching and       Ethernet, VLAN          Understand local and
  routing                 concepts, routes,       remote communication
                          gateways                

  5\. Protocols           TCP, UDP, DNS, DHCP,    Understand common
                          ARP, ICMP, HTTP, SSH    network services

  6\. Linux               Interfaces, Netplan,    Configure a Linux host
                          routes, resolver,       
                          firewall                

  7\. Troubleshooting     ping, ip, ss, dig,      Diagnose connectivity
                          curl, tcpdump           problems

  8\. Practical work      Multi-host LAN, SSH,    Apply the concepts
                          DNS and web service     
  -----------------------------------------------------------------------

## Suggested study method

For each topic:

1.  Learn the definition and purpose.
2.  Draw the communication path.
3.  Identify the OSI layer involved.
4.  Run the related Linux command.
5.  Observe the result.
6.  Introduce a controlled fault and troubleshoot it.
7.  Write down the root cause and solution.

------------------------------------------------------------------------

# 2. Networking fundamentals

## 2.1 What is computer networking?

Computer networking is the connection of two or more devices so that
they can exchange data and share resources.

Examples include:

-   A laptop communicating with a printer over Wi-Fi.
-   Two office computers sharing a file server.
-   A Linux server communicating with a database server.
-   A browser accessing a website over the Internet.

A network requires devices, transmission media, addressing and rules
called protocols.

## 2.2 Why do we need networks?

-   Resource sharing: printers, storage and applications.
-   Communication: email, messaging and voice/video calls.
-   Centralized management: user accounts, files and policies.
-   Remote access: securely administering systems from another location.
-   Reliability: alternate links and devices can provide resilience.
-   Monitoring: observing availability, performance and security.

## 2.3 Basic network components

  -----------------------------------------------------------------------
  Component                           Purpose
  ----------------------------------- -----------------------------------
  End device                          Generates or receives data, such as
                                      a laptop or server

  Network interface                   Connects a device to a network

  Transmission medium                 Carries signals, such as copper,
                                      fiber or radio

  Switch                              Connects devices within a LAN

  Router                              Forwards packets between IP
                                      networks

  Access point                        Connects wireless clients to a
                                      network

  Firewall                            Applies traffic security rules

  Protocol                            Defines communication rules
  -----------------------------------------------------------------------

## 2.4 Important networking terms

-   **Bandwidth:** The theoretical or configured capacity of a link,
    commonly measured in bits per second.
-   **Throughput:** The actual rate of successful data transfer.
-   **Latency:** Time taken for data to travel between endpoints.
-   **Jitter:** Variation in packet delay.
-   **Packet loss:** Packets that fail to reach their destination.
-   **Duplex:** Whether a link can transmit and receive simultaneously.
-   **MTU:** Maximum Layer 3 packet size that can be carried over a link
    without fragmentation at that layer.
-   **Availability:** The proportion of time a service or link is
    operational.

Bandwidth and throughput are not the same. A 1 Gbps link does not
guarantee an application will transfer data at 1 Gbps.

------------------------------------------------------------------------

# 3. Network types and topologies

## 3.1 Types of networks

  -----------------------------------------------------------------------
  Type                    Full form               Typical scope
  ----------------------- ----------------------- -----------------------
  PAN                     Personal Area Network   Personal devices, often
                                                  Bluetooth

  LAN                     Local Area Network      Home, office or
                                                  building

  WLAN                    Wireless LAN            LAN using Wi-Fi

  CAN                     Campus Area Network     Multiple buildings in a
                                                  campus

  MAN                     Metropolitan Area       City or metropolitan
                          Network                 area

  WAN                     Wide Area Network       Large geographic areas

  VPN                     Virtual Private Network Private connectivity
                                                  over an underlying
                                                  network
  -----------------------------------------------------------------------

## 3.2 Network topologies

Topology describes how devices and links are arranged.

### Bus topology

All devices share a common communication medium.

-   Simple historical design.
-   A fault in the shared backbone can affect the network.
-   Not common in modern switched Ethernet LANs.

### Star topology

Each endpoint connects to a central switch or access point.

-   Easy to expand.
-   A single endpoint cable failure usually affects only that endpoint.
-   Failure of the central device can affect many endpoints.

### Ring topology

Devices are connected in a circular arrangement.

-   Traffic follows a ring-based path.
-   Some technologies provide ring protection.
-   Used in selected industrial and carrier networks.

### Mesh topology

Devices have multiple interconnections.

-   Provides alternate paths.
-   Can improve resilience.
-   Requires more links and management.

### Tree or hierarchical topology

Devices are arranged in access, distribution and core layers.

This is a common design approach for enterprise networks.

------------------------------------------------------------------------

# 4. Network devices

## 4.1 Network Interface Card (NIC)

A NIC is the hardware or virtual interface that connects a device to a
network.

Examples:

-   Ethernet adapter.
-   Wi-Fi adapter.
-   Fiber network adapter.
-   Virtual network interface.

A NIC has a link-layer address, commonly called a MAC address.

Linux commands:

``` bash
ip link show
ip addr show
ethtool eth0
```

The interface may have a name such as `eth0`, `ens33`, `enp0s3` or
`wlan0`.

## 4.2 Hub

A hub is a basic Layer 1 device that repeats incoming electrical signals
to its other ports.

Characteristics:

-   Does not learn MAC addresses.
-   Sends signals to all other ports.
-   Shared collision domain.
-   Largely obsolete; switches replaced hubs in modern Ethernet LANs.

## 4.3 Switch

A switch primarily operates at OSI Layer 2.

Its main job is to forward Ethernet frames using a MAC address table.

How a switch learns:

1.  A frame arrives on a port.
2.  The switch reads the source MAC address.
3.  It records the source MAC and incoming port.
4.  It looks up the destination MAC.
5.  If known, it forwards the frame to the corresponding port.
6.  If unknown, it floods the frame within the applicable VLAN, except
    to the incoming port.

Important concepts:

-   MAC address table.
-   Access port.
-   Trunk port.
-   VLAN.
-   Broadcast domain.
-   Full-duplex communication.
-   Spanning Tree Protocol (STP).

### Managed vs unmanaged switch

  Unmanaged switch               Managed switch
  ------------------------------ ----------------------------------------
  Minimal configuration          Configurable
  Usually plug and play          Supports VLANs and monitoring features
  Limited visibility             Supports management and diagnostics
  Suitable for simple networks   Suitable for business networks

## 4.4 Router

A router connects different IP networks and forwards packets using a
routing table.

Example:

``` text
LAN A: 192.168.10.0/24
           |
         Router
           |
LAN B: 192.168.20.0/24
```

The router examines the destination IP address and selects a route.

Important concepts:

-   Routing table.
-   Next hop.
-   Default route.
-   Static routing.
-   Dynamic routing.
-   Routing metrics.
-   Network Address Translation (NAT).

Linux routing commands:

``` bash
ip route
ip route get 8.8.8.8
```

## 4.5 Modem

A modem provides the signaling or access technology required to connect
to an Internet service provider's network.

The exact function depends on the access technology, such as cable, DSL
or cellular.

A modem and router are different functions, although home devices often
combine them.

## 4.6 Wireless Access Point (AP)

An access point connects wireless clients to a wired network.

Important concepts:

-   SSID: Wireless network name.
-   Channel: Radio-frequency channel.
-   Band: Commonly 2.4 GHz, 5 GHz or 6 GHz where supported.
-   Authentication: How clients prove they are allowed to connect.
-   Encryption: Protection of wireless traffic.

Wi-Fi security should use modern WPA2-AES or WPA3 configurations where
supported.

## 4.7 Firewall

A firewall permits or blocks traffic according to rules.

Common types:

-   Stateless packet filter.
-   Stateful firewall.
-   Host-based firewall.
-   Network firewall.
-   Application-aware firewall.

A firewall may filter by source, destination, protocol, port, connection
state or application.

## 4.8 Load balancer

A load balancer distributes requests or connections across multiple
servers.

Common approaches:

-   Round robin.
-   Weighted round robin.
-   Least connections.
-   Source-IP hashing.

A load balancer is not a replacement for a router or firewall; each
serves a different purpose.

## 4.9 Repeater, bridge and gateway

  -----------------------------------------------------------------------
  Device                              Function
  ----------------------------------- -----------------------------------
  Repeater                            Regenerates or repeats signals

  Bridge                              Connects Layer 2 network segments

  Gateway                             Connects systems or networks using
                                      compatible or translated protocols

  Media converter                     Converts one physical media type to
                                      another, such as copper Ethernet to
                                      fiber
  -----------------------------------------------------------------------

## 4.10 Device comparison

  -----------------------------------------------------------------------
  Device                  Main OSI layer          Main function
  ----------------------- ----------------------- -----------------------
  Hub                     Layer 1                 Repeats signals

  Repeater                Layer 1                 Regenerates signals

  Bridge                  Layer 2                 Connects LAN segments

  Switch                  Layer 2                 Forwards frames using
                                                  MAC addresses

  Router                  Layer 3                 Forwards packets using
                                                  IP routes

  Firewall                Multiple                Enforces traffic policy

  Access point            Mainly Layer 2          Connects Wi-Fi clients

  Load balancer           Layer 4 or 7, depending Distributes traffic
                          on type                 
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 5. How communication works

## 5.1 Communication within the same subnet

Assume:

-   Host A: `192.168.1.10/24`
-   Host B: `192.168.1.20/24`

Host A determines that Host B is in the same subnet.

If Host A does not know Host B's MAC address, it uses ARP to request it.
Host B responds with its MAC address. Host A then sends an Ethernet
frame to Host B through the switch.

## 5.2 Communication with another subnet

Assume:

-   Host A: `192.168.1.10/24`
-   Default gateway: `192.168.1.1`
-   Remote server: `10.10.10.20`

Host A determines that the remote IP is outside its local subnet.

It sends the Ethernet frame to the MAC address of its default gateway.
The IP packet still has the remote server as its destination. The router
checks its routing table and forwards the packet toward the destination.

## 5.3 What happens when you open a website?

A simplified sequence:

1.  The browser checks available DNS caches.
2.  The system resolves the domain name if necessary.
3.  The client determines the route to the destination.
4.  The client establishes the required transport connection.
5.  For HTTPS, TLS establishes an encrypted session.
6.  The browser sends an HTTP request.
7.  The server returns a response.
8.  The browser renders the content.

The actual sequence can vary with HTTP/3, DNS caching, proxies,
connection reuse and other optimizations.

------------------------------------------------------------------------

# 6. OSI and TCP/IP models

## 6.1 OSI seven-layer model

  -----------------------------------------------------------------------
  Layer             Name              Main              Examples
                                      responsibility    
  ----------------- ----------------- ----------------- -----------------
  7                 Application       Application       HTTP, DNS, SMTP
                                      network services  

  6                 Presentation      Data              Encoding, TLS
                                      representation,   conceptually
                                      encryption        
                                      concepts          

  5                 Session           Session           Session
                                      coordination      management

  4                 Transport         End-to-end        TCP, UDP
                                      transport         

  3                 Network           Logical           IPv4, IPv6, ICMP
                                      addressing and    
                                      routing           

  2                 Data Link         Frames and local  Ethernet, Wi-Fi
                                      delivery          

  1                 Physical          Signals and media Copper, fiber,
                                                        radio
  -----------------------------------------------------------------------

Memory aid:

-   Layer 1: Signals.
-   Layer 2: Frames and MAC addresses.
-   Layer 3: Packets and IP addresses.
-   Layer 4: Segments/datagrams and ports.
-   Layers 5--7: Application communication functions.

The OSI model is a learning and troubleshooting model. Real protocols do
not always map perfectly to one layer.

## 6.2 TCP/IP model

  TCP/IP layer     Approximate OSI mapping   Examples
  ---------------- ------------------------- -----------------
  Application      5--7                      HTTP, DNS, SSH
  Transport        4                         TCP, UDP
  Internet         3                         IP, ICMP
  Network Access   1--2                      Ethernet, Wi-Fi

## 6.3 Encapsulation

When data is sent, each layer adds control information.

``` text
Application data
      |
TCP segment or UDP datagram
      |
IP packet
      |
Ethernet frame
      |
Bits on the medium
```

At the destination, the corresponding headers are processed and removed.
This is decapsulation.

------------------------------------------------------------------------

# 7. Ethernet, MAC addresses and switching

## 7.1 MAC address

A MAC address is a link-layer address used for delivery on a local
network.

Example:

``` text
00:1A:2B:3C:4D:5E
```

A MAC address is commonly 48 bits for Ethernet.

A MAC address is not a reliable proof of a device's identity: addresses
can be changed or spoofed.

## 7.2 Ethernet frame

An Ethernet frame includes:

-   Destination MAC address.
-   Source MAC address.
-   EtherType or length field.
-   Payload.
-   Frame Check Sequence (FCS).

The FCS helps detect frame corruption.

## 7.3 ARP

Address Resolution Protocol maps an IPv4 address to a MAC address on the
local link.

View the neighbor table:

``` bash
ip neigh
```

Generate traffic and inspect it:

``` bash
ping -c 1 192.168.1.20
ip neigh
```

For IPv6, Neighbor Discovery uses ICMPv6 rather than ARP.

## 7.4 VLAN

A Virtual LAN divides a switched Layer 2 network into separate logical
broadcast domains.

Example:

  VLAN   Purpose          Subnet
  ------ ---------------- -----------------
  10     Administration   192.168.10.0/24
  20     Servers          192.168.20.0/24
  30     Guest Wi-Fi      192.168.30.0/24

VLANs provide logical separation, but they are not a substitute for
complete security controls.

### Access port

Normally carries traffic for one configured VLAN.

### Trunk port

Carries traffic for multiple VLANs, commonly using IEEE 802.1Q tagging.

### Inter-VLAN routing

Communication between different VLANs requires a Layer 3 routing
function, such as a router or Layer 3 switch.

## 7.5 Spanning Tree Protocol

STP prevents Layer 2 switching loops by blocking redundant paths when
necessary.

Why loops are dangerous:

-   Broadcast storms.
-   Duplicate frames.
-   MAC address table instability.
-   Network disruption.

RSTP is a faster-converging version of STP.

------------------------------------------------------------------------

# 8. IP addressing

## 8.1 What is an IP address?

An IP address is a logical address used to identify an interface in an
IP network.

IPv4 example:

``` text
192.168.1.10
```

IPv4 uses 32 bits, commonly written as four decimal octets.

## 8.2 IPv4 vs IPv6

  Feature              IPv4             IPv6
  -------------------- ---------------- ---------------------------
  Address size         32 bits          128 bits
  Example              192.168.1.10     2001:db8::10
  Notation             Decimal octets   Hexadecimal groups
  Broadcast            Yes              No broadcast
  Neighbor discovery   ARP              ICMPv6 Neighbor Discovery

## 8.3 Private IPv4 ranges

  Range                            CIDR
  -------------------------------- ----------------
  10.0.0.0 -- 10.255.255.255       10.0.0.0/8
  172.16.0.0 -- 172.31.255.255     172.16.0.0/12
  192.168.0.0 -- 192.168.255.255   192.168.0.0/16

These addresses are not globally routed on the public Internet.

## 8.4 Other special IPv4 ranges

  Range             Purpose
  ----------------- -----------------------------------------------------------
  127.0.0.0/8       Loopback
  169.254.0.0/16    Link-local
  0.0.0.0           Unspecified address; also used in route and bind contexts
  255.255.255.255   Limited broadcast

## 8.5 Public and private IP addresses

-   Private addresses are used inside private networks.
-   Public addresses are globally routable.
-   NAT is commonly used to allow private IPv4 hosts to communicate
    externally.
-   A public IP address alone does not guarantee reachability; routing
    and firewall rules also matter.

## 8.6 Static and dynamic addresses

  Static                                Dynamic
  ------------------------------------- -------------------------
  Configured to remain stable           Assigned dynamically
  Useful for infrastructure             Common for user devices
  Requires careful address management   Often uses DHCP

## 8.7 Subnet mask

A subnet mask identifies the network portion of an IPv4 address.

Example:

``` text
IP address:  192.168.1.10
Subnet mask: 255.255.255.0
CIDR:        /24
Network:     192.168.1.0
Broadcast:   192.168.1.255
```

------------------------------------------------------------------------

# 9. Subnetting and CIDR

## 9.1 What is subnetting?

Subnetting divides a larger IP network into smaller logical networks.

Benefits:

-   Organizes devices.
-   Limits broadcast domains.
-   Supports network segmentation.
-   Helps manage address allocation.
-   Supports routing and security boundaries.

## 9.2 CIDR notation

CIDR means Classless Inter-Domain Routing.

Example:

``` text
192.168.1.0/24
```

The `/24` means 24 bits are used for the network prefix.

## 9.3 Common subnet sizes

  CIDR     Total IPv4 addresses          Traditional usable host addresses
  ------ ---------------------- ------------------------------------------
  /24                       256                                        254
  /25                       128                                        126
  /26                        64                                         62
  /27                        32                                         30
  /28                        16                                         14
  /29                         8                                          6
  /30                         4                                          2
  /31                         2   2 on point-to-point links under RFC 3021
  /32                         1                         One address/prefix

For ordinary IPv4 subnets, the traditional usable-host calculation
excludes the network and broadcast addresses. Special cases such as
`/31` point-to-point links differ.

## 9.4 Subnetting example

Given:

``` text
Network: 192.168.1.0/24
Requirement: Four equal subnets
```

Borrow two host bits:

``` text
/24 + 2 = /26
```

Each subnet contains 64 addresses.

  Subnet   Network            Usable host range    Broadcast
  -------- ------------------ -------------------- ---------------
  1        192.168.1.0/26     192.168.1.1--62      192.168.1.63
  2        192.168.1.64/26    192.168.1.65--126    192.168.1.127
  3        192.168.1.128/26   192.168.1.129--190   192.168.1.191
  4        192.168.1.192/26   192.168.1.193--254   192.168.1.255

## 9.5 Subnetting formulas

For ordinary IPv4 subnet calculations:

``` text
Total addresses = 2^(32 - prefix length)
Traditional usable hosts = Total addresses - 2
```

The usable-host formula has exceptions, including `/31` point-to-point
networks and `/32` host routes.

## 9.6 Subnetting practice

Try these:

1.  How many total addresses are in a `/26`?
2.  How many traditional usable hosts are in a `/27`?
3.  What is the network address of `192.168.10.75/24`?
4.  What is the broadcast address of `192.168.10.64/26`?
5.  How many `/28` subnets fit inside a `/24`?

Answers:

1.  64. 
2.  30. 
3.  `192.168.10.0`.
4.  `192.168.10.127`.
5.  16. 

------------------------------------------------------------------------

# 10. Routing and gateways

## 10.1 What is routing?

Routing is the process of selecting a path for IP packets to reach their
destination.

A router uses its routing table to select the most specific matching
route, then applies route preference and other rules where necessary.

## 10.2 Default gateway

A default gateway is the next hop used when no more specific route
matches a destination.

Example:

``` text
Host IP:       192.168.1.10/24
Default route: via 192.168.1.1
```

## 10.3 Routing table

Example:

``` text
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0 proto kernel scope link
```

Inspect:

``` bash
ip route
ip route get 8.8.8.8
```

## 10.4 Static routing

A static route is manually configured.

Example:

``` bash
sudo ip route add 10.10.0.0/16 via 192.168.1.1
```

This is generally temporary unless saved in persistent network
configuration.

## 10.5 Dynamic routing

Dynamic routing protocols exchange routing information between routers.

  Protocol   Description
  ---------- ------------------------------------------------------
  RIP        Older distance-vector routing protocol
  OSPF       Link-state interior gateway protocol
  IS-IS      Link-state routing protocol
  BGP        Path-vector protocol used between autonomous systems

## 10.6 NAT and PAT

Network Address Translation modifies IP addressing information as
packets pass through a network device.

PAT also uses transport-layer port numbers so multiple private hosts can
share a public IPv4 address.

Example:

``` text
Host A: 192.168.1.10
Host B: 192.168.1.11
             |
           Router
             |
       Public IPv4 address
             |
          Internet
```

## 10.7 Port forwarding

Port forwarding maps incoming traffic on an address and port to an
internal destination.

Example:

``` text
Public-address:8080 → 192.168.1.50:80
```

Only expose services that need to be reachable, and protect
administrative services appropriately.

------------------------------------------------------------------------

# 11. Core network protocols

## 11.1 TCP

Transmission Control Protocol provides a reliable, ordered byte stream.

Characteristics:

-   Connection-oriented.
-   Sequence numbers.
-   Acknowledgements.
-   Retransmission.
-   Flow control.
-   Congestion control.

### TCP three-way handshake

``` text
Client                  Server
  | ------ SYN --------> |
  | <--- SYN-ACK ------- |
  | ------ ACK --------> |
  |                      |
  |   Connection ready   |
```

The handshake establishes the TCP connection.

## 11.2 UDP

User Datagram Protocol provides connectionless datagram delivery.

Characteristics:

-   No connection handshake.
-   Low protocol overhead.
-   No built-in retransmission.
-   No built-in ordering guarantee.

Examples include DNS queries, real-time media and some streaming
protocols.

## 11.3 TCP vs UDP

  -----------------------------------------------------------------------
  Feature                 TCP                     UDP
  ----------------------- ----------------------- -----------------------
  Connection              Connection-oriented     Connectionless

  Delivery guarantee      Built-in reliability    No delivery guarantee
                          mechanisms              

  Ordering                Ordered byte stream     No ordering guarantee

  Overhead                More                    Less

  Typical examples        SSH, HTTPS over TCP     DNS, voice/video
                                                  traffic
  -----------------------------------------------------------------------

HTTP/3 uses QUIC over UDP.

## 11.4 DNS

Domain Name System resolves names to records such as IP addresses.

Common record types:

  Record   Purpose
  -------- -----------------------------------
  A        IPv4 address
  AAAA     IPv6 address
  CNAME    Alias
  MX       Mail exchanger
  TXT      Text and verification information
  NS       Name server
  PTR      Reverse lookup
  SRV      Service location
  SOA      Zone authority information

DNS commonly uses UDP port 53; TCP port 53 is also used, including for
some large responses and zone transfers.

Commands:

``` bash
dig example.com
dig A example.com
dig AAAA example.com
dig MX example.com
dig NS example.com
dig +trace example.com
```

## 11.5 DHCP

Dynamic Host Configuration Protocol automatically provides IP
configuration.

IPv4 DHCP uses UDP ports 67 and 68.

DORA sequence:

1.  Discover.
2.  Offer.
3.  Request.
4.  Acknowledge.

DHCP can provide an IP address, subnet mask, gateway, DNS servers and
lease time.

## 11.6 ARP

ARP resolves IPv4 addresses to MAC addresses on a local network.

``` bash
ip neigh
```

## 11.7 ICMP

Internet Control Message Protocol is used for diagnostics and network
error reporting.

Examples:

``` bash
ping 8.8.8.8
tracepath example.com
```

ICMP filtering can cause ping to fail even when application traffic
works.

## 11.8 HTTP and HTTPS

-   HTTP transfers web resources.
-   HTTPS protects HTTP using TLS.
-   Common ports: TCP 80 and TCP 443.
-   HTTP/3 uses QUIC over UDP.

Test:

``` bash
curl -I http://example.com
curl -I https://example.com
curl -v https://example.com
```

## 11.9 SSH

Secure Shell provides encrypted remote administration.

Default port: TCP 22.

``` bash
ssh username@192.168.1.20
```

Key-based login:

``` bash
ssh-keygen -t ed25519
ssh-copy-id username@192.168.1.20
```

## 11.10 FTP, SFTP and SCP

  Protocol   Purpose
  ---------- -----------------------------------------
  FTP        File transfer; not encrypted by default
  SFTP       File transfer over SSH
  SCP        Secure file copy over SSH

SFTP and FTP are different protocols.

## 11.11 Email protocols

  Protocol          Purpose                              Common port
  ----------------- ---------------------------------- -------------
  SMTP              Sending email                                 25
  SMTP submission   Client email submission                      587
  SMTP over TLS     Secure submission                            465
  POP3              Retrieving email                             110
  POP3S             Secure POP3                                  995
  IMAP              Email access and synchronization             143
  IMAPS             Secure IMAP                                  993

## 11.12 NTP

Network Time Protocol synchronizes system clocks.

NTP commonly uses UDP port 123.

Correct time is important for logs, authentication, certificates and
troubleshooting.

Linux:

``` bash
timedatectl
timedatectl status
```

## 11.13 SNMP

Simple Network Management Protocol is used to monitor and manage network
devices.

It can expose:

-   Interface status.
-   Interface traffic counters.
-   CPU and memory metrics.
-   Device health.
-   Error counters.

Common ports:

-   UDP 161: Queries.
-   UDP 162: Traps and notifications.

Prefer SNMPv3 where supported because it provides authentication and
privacy features.

------------------------------------------------------------------------

# 12. Ports and common services

A port number identifies a transport-layer endpoint on a host.

Example:

``` text
192.168.1.10:22
```

The IP identifies the destination host/interface; the port identifies
the service endpoint.

## 12.1 Important ports

       Port Protocol/service   Purpose
  --------- ------------------ ------------------------------
      20/21 FTP                File transfer
         22 SSH                Remote administration
         23 Telnet             Insecure remote terminal
         25 SMTP               Email transfer
         53 DNS                Name resolution
      67/68 DHCP               IPv4 address allocation
         69 TFTP               Simple file transfer
         80 HTTP               Web traffic
        110 POP3               Email retrieval
        123 NTP                Time synchronization
        143 IMAP               Email access
    161/162 SNMP               Monitoring and notifications
        389 LDAP               Directory access
        443 HTTPS              Secure web traffic
        445 SMB                Windows file sharing
    465/587 SMTP submission    Email submission
        514 Syslog             Logging
        636 LDAPS              LDAP over TLS
        993 IMAPS              Secure IMAP
        995 POP3S              Secure POP3
       3306 MySQL              Database
       5432 PostgreSQL         Database
       6379 Redis              Data store/cache

Ports are conventions. A service can be configured to listen on a
different port.

## 12.2 Check whether a port is listening

``` bash
sudo ss -tulnp
sudo ss -ltnp 'sport = :22'
sudo lsof -i :22
```

## 12.3 Test a remote port

``` bash
nc -vz 192.168.1.20 22
nc -vz 192.168.1.30 5432
```

A successful TCP connection proves that the TCP handshake completed. It
does not prove that the application authentication or operation will
succeed.

------------------------------------------------------------------------

# 13. Network security fundamentals

## 13.1 Firewall rules

A firewall can filter traffic using:

-   Source IP.
-   Destination IP.
-   Source and destination ports.
-   Protocol.
-   Connection state.
-   Interface or zone.
-   Application characteristics, depending on firewall type.

## 13.2 Stateful vs stateless firewall

  -----------------------------------------------------------------------
  Stateful                            Stateless
  ----------------------------------- -----------------------------------
  Tracks connection state             Evaluates packets independently

  Can automatically allow matching    Return traffic needs matching rules
  return traffic                      

  Understands connection context      Uses configured packet attributes
  -----------------------------------------------------------------------

## 13.3 VPN

A Virtual Private Network creates protected connectivity over another
network.

Common uses:

-   Remote employee access.
-   Connecting office networks.
-   Connecting separate sites.
-   Secure administration.

IPsec is commonly used for site-to-site VPNs. Other technologies include
WireGuard and OpenVPN.

## 13.4 TLS and certificates

TLS protects data in transit.

Important terms:

-   Certificate.
-   Public key.
-   Private key.
-   Certificate Authority.
-   Certificate chain.
-   Certificate Signing Request.
-   Expiration date.
-   Hostname validation.

Inspect a TLS connection:

``` bash
openssl s_client -connect example.com:443 \
  -servername example.com
```

Inspect a certificate:

``` bash
openssl x509 -in certificate.crt -text -noout
```

## 13.5 Security best practices

-   Use SSH keys rather than weak passwords.
-   Restrict administrative ports to trusted networks.
-   Disable unused services.
-   Patch network operating systems and Linux.
-   Use encrypted protocols.
-   Separate guest, user and server networks.
-   Monitor firewall logs.
-   Back up device configurations.
-   Use SNMPv3 rather than insecure community strings.
-   Avoid exposing database ports to untrusted networks.

------------------------------------------------------------------------

# 14. Linux networking fundamentals

## 14.1 Linux networking architecture

A Linux system contains:

-   Applications.
-   Sockets.
-   Transport protocols.
-   IP networking stack.
-   Routing and neighbor handling.
-   Netfilter firewall framework.
-   Network interfaces and drivers.

Simplified path:

``` text
Application
    |
  Socket
    |
 TCP / UDP
    |
 IPv4 / IPv6
    |
 Ethernet / Wi-Fi
    |
 Network Interface
```

## 14.2 Network interface names

Common names:

-   `lo`: Loopback.
-   `eth0`: Ethernet-style name.
-   `ens33`: Predictable interface name.
-   `enp0s3`: PCI-based predictable name.
-   `wlan0`: Wireless interface.

List interfaces:

``` bash
ip link show
```

Show IP addresses:

``` bash
ip addr show
```

## 14.3 Loopback interface

The loopback interface allows a machine to communicate with itself.

IPv4 loopback:

``` text
127.0.0.1
```

IPv6 loopback:

``` text
::1
```

Test:

``` bash
ping -c 4 127.0.0.1
```

## 14.4 Linux network configuration tools

  Tool           Purpose
  -------------- ----------------------------------------
  `ip`           Addresses, links, routes and neighbors
  `ss`           Socket information
  `ethtool`      Ethernet device settings
  `nmcli`        NetworkManager management
  `resolvectl`   systemd-resolved information
  `netplan`      Network configuration on Ubuntu
  `tcpdump`      Packet capture
  `nft`          nftables firewall management
  `ufw`          Simplified firewall management

------------------------------------------------------------------------

# 15. Linux network configuration

## 15.1 Identify the interface

``` bash
ip link show
ip addr show
```

Find the default route:

``` bash
ip route
```

## 15.2 Temporarily assign an IPv4 address

``` bash
sudo ip addr add 192.168.1.100/24 dev eth0
```

Remove it:

``` bash
sudo ip addr del 192.168.1.100/24 dev eth0
```

Bring an interface up or down:

``` bash
sudo ip link set eth0 up
sudo ip link set eth0 down
```

These changes may not persist after reboot or network manager
reconfiguration.

## 15.3 Ubuntu Netplan

Ubuntu Server commonly uses Netplan.

Find configuration:

``` bash
ls -l /etc/netplan/
```

Example configuration:

``` yaml
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: false
      addresses:
        - 192.168.1.100/24
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses:
          - 1.1.1.1
          - 8.8.8.8
```

Replace `ens33`, IP and gateway with the values appropriate for the
machine.

Validate:

``` bash
sudo netplan generate
```

Safely test:

``` bash
sudo netplan try
```

Apply:

``` bash
sudo netplan apply
```

Verify:

``` bash
ip addr
ip route
resolvectl status
```

When working remotely, use `netplan try` and retain console access where
possible to avoid losing connectivity.

## 15.4 NetworkManager

On systems using NetworkManager:

``` bash
nmcli device status
nmcli connection show
nmcli device show
```

Connect to a Wi-Fi network:

``` bash
nmcli device wifi list
nmcli device wifi connect "SSID" password "PASSWORD"
```

Do not place real passwords in shell history or shared scripts.

## 15.5 Interface details

Install ethtool:

``` bash
sudo apt install ethtool
```

Inspect:

``` bash
sudo ethtool eth0
```

Useful information:

-   Link detected.
-   Speed.
-   Duplex.
-   Auto-negotiation.
-   Supported link modes.

------------------------------------------------------------------------

# 16. Linux routing, DNS and firewalling

## 16.1 Routing

View routes:

``` bash
ip route
ip -6 route
```

Inspect route selection:

``` bash
ip route get 8.8.8.8
```

Add a temporary route:

``` bash
sudo ip route add 10.10.0.0/16 via 192.168.1.1
```

Remove:

``` bash
sudo ip route del 10.10.0.0/16
```

## 16.2 DNS configuration

Check resolver status:

``` bash
resolvectl status
```

Test name resolution:

``` bash
getent hosts example.com
dig example.com
```

Inspect resolver file:

``` bash
cat /etc/resolv.conf
```

On Ubuntu, `/etc/resolv.conf` may be a symlink managed by
`systemd-resolved`. Avoid editing it blindly.

## 16.3 Hosts file

The hosts file provides local name-to-address mappings.

Location:

``` text
/etc/hosts
```

Example:

``` text
192.168.1.101 server1.lab
192.168.1.102 server2.lab
192.168.1.103 server3.lab
```

Test:

``` bash
getent hosts server1.lab
```

The hosts file is useful for small labs, but a DNS server is more
manageable for larger networks.

## 16.4 UFW firewall

Check:

``` bash
sudo ufw status verbose
```

Allow SSH:

``` bash
sudo ufw allow 22/tcp
```

Allow HTTP and HTTPS:

``` bash
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

Enable:

``` bash
sudo ufw enable
```

Delete a rule:

``` bash
sudo ufw delete allow 80/tcp
```

Important: Allow required remote administration traffic before enabling
the firewall on a remote server.

## 16.5 nftables and iptables

Inspect nftables:

``` bash
sudo nft list ruleset
```

Inspect iptables:

``` bash
sudo iptables -L -n -v
```

Modern Linux distributions commonly use nftables as the underlying
packet-filtering framework. UFW and other tools may manage rules through
this framework.

------------------------------------------------------------------------

# 17. Network troubleshooting tools

## 17.1 ping

Test IP connectivity:

``` bash
ping -c 4 8.8.8.8
ping -c 4 example.com
```

Interpretation:

-   Replies received: ICMP communication is working.
-   Packet loss: Could indicate congestion, filtering or a path issue.
-   High latency: Could indicate congestion or a distant route.

A failed ping does not prove that a host or application is down.

## 17.2 traceroute and tracepath

Show the path toward a destination:

``` bash
traceroute example.com
tracepath example.com
```

Install traceroute on Ubuntu:

``` bash
sudo apt install traceroute
```

Some routers do not respond to traceroute probes. Missing hop responses
do not necessarily indicate a forwarding failure.

## 17.3 dig and nslookup

``` bash
dig example.com
dig +short example.com
dig @1.1.1.1 example.com
nslookup example.com
```

These help identify name-resolution issues.

## 17.4 ss

Show listening sockets:

``` bash
sudo ss -tulnp
```

Show TCP connections:

``` bash
ss -tan
```

Show a particular port:

``` bash
sudo ss -ltnp 'sport = :8080'
```

## 17.5 curl

Test HTTP:

``` bash
curl -I http://example.com
```

Test HTTPS:

``` bash
curl -Iv https://example.com
```

Show detailed connection information:

``` bash
curl -v https://example.com
```

## 17.6 nc

Test TCP connectivity:

``` bash
nc -vz 192.168.1.20 22
nc -vz 192.168.1.30 5432
```

## 17.7 tcpdump

Install:

``` bash
sudo apt install tcpdump
```

Capture traffic:

``` bash
sudo tcpdump -i eth0
```

Capture DNS:

``` bash
sudo tcpdump -i eth0 port 53
```

Capture SSH:

``` bash
sudo tcpdump -i eth0 port 22
```

Capture traffic to or from a host:

``` bash
sudo tcpdump -i eth0 host 192.168.1.20
```

Save capture:

``` bash
sudo tcpdump -i eth0 -w capture.pcap
```

Read capture:

``` bash
tcpdump -r capture.pcap
```

## 17.8 Wireshark

Wireshark is a graphical packet analyzer.

Useful display filters:

``` text
dns
tcp
udp
icmp
ip.addr == 192.168.1.10
tcp.port == 443
tcp.flags.syn == 1
```

Use it to inspect:

-   DNS requests and responses.
-   TCP handshakes.
-   Retransmissions.
-   TCP resets.
-   TLS handshakes.
-   Packet timing.

## 17.9 Useful diagnostic command sequence

When a Linux server cannot reach a destination:

``` bash
ip addr
ip route
ip neigh
ping -c 4 GATEWAY_IP
getent hosts example.com
dig example.com
nc -vz DESTINATION_IP PORT
curl -v https://example.com
ss -tulnp
```

Use the commands relevant to the suspected failure. Not every problem
requires every command.

------------------------------------------------------------------------

# 18. Practical Linux networking labs

Use two or three Ubuntu Server machines on the same home or lab network.

## Lab 1: Discover the network configuration

On each server:

``` bash
hostname
ip addr
ip route
ip link
```

Record:

-   Hostname.
-   Interface name.
-   MAC address.
-   IPv4 address.
-   Prefix length.
-   Default gateway.
-   DNS resolver.

## Lab 2: Test local connectivity

Assume:

``` text
Server A: 192.168.1.101/24
Server B: 192.168.1.102/24
Gateway:  192.168.1.1
```

From Server A:

``` bash
ping -c 4 192.168.1.102
```

Inspect neighbor entries:

``` bash
ip neigh
```

Observe how the neighbor table learns Server B's MAC address.

## Lab 3: Configure SSH

On the destination server:

``` bash
sudo apt update
sudo apt install openssh-server
sudo systemctl enable --now ssh
```

Check:

``` bash
sudo systemctl status ssh
sudo ss -ltnp 'sport = :22'
```

From the source:

``` bash
ssh username@192.168.1.102
```

## Lab 4: Test a TCP port

On Server B, start a temporary HTTP server:

``` bash
python3 -m http.server 8000 --bind 0.0.0.0
```

From Server A:

``` bash
nc -vz 192.168.1.102 8000
curl http://192.168.1.102:8000
```

Stop the server using `Ctrl+C`.

## Lab 5: Understand DNS

Run:

``` bash
dig example.com
getent hosts example.com
resolvectl status
```

Compare the DNS answer with the result from a known resolver:

``` bash
dig @1.1.1.1 example.com
```

Do not assume every resolver will return identical answers; DNS
responses can vary because of caching, geography and policy.

## Lab 6: Capture packets

On Server B:

``` bash
sudo tcpdump -i any port 8000
```

From Server A:

``` bash
curl http://192.168.1.102:8000
```

Observe the TCP connection and HTTP exchange.

## Lab 7: Configure a static IP

Use the Netplan instructions in Section 15.

After applying, verify:

``` bash
ip addr
ip route
ping -c 4 GATEWAY_IP
```

Ensure the selected address is not already in use.

## Lab 8: Configure a basic firewall

On a test server, first ensure SSH access is allowed:

``` bash
sudo ufw allow 22/tcp
sudo ufw enable
sudo ufw status verbose
```

Then test the required application port. Only allow the ports needed by
the lab.

## Lab 9: Create a local name mapping

Edit `/etc/hosts` on both machines:

``` text
192.168.1.101 server1.lab
192.168.1.102 server2.lab
```

Test:

``` bash
getent hosts server2.lab
ping -c 2 server2.lab
```

## Lab 10: Diagnose a failed service

1.  Stop the HTTP server.
2.  Run `nc -vz SERVER_IP 8000`.
3.  Observe the failure.
4.  Restart the HTTP server.
5.  Test again.
6.  Explain the difference between a refused connection and a timeout.

------------------------------------------------------------------------

# 19. Troubleshooting scenarios

## Scenario 1: Cannot reach the gateway

Possible causes:

-   Incorrect IP address.
-   Incorrect subnet mask.
-   Interface down.
-   Cable or Wi-Fi issue.
-   VLAN mismatch.
-   Gateway unavailable.
-   ARP or Layer 2 problem.

Commands:

``` bash
ip addr
ip link
ip route
ip neigh
ping -c 4 GATEWAY_IP
```

## Scenario 2: Can ping an IP but not a domain

Likely area: DNS resolution.

Commands:

``` bash
ping -c 2 1.1.1.1
dig example.com
resolvectl status
getent hosts example.com
```

Check resolver settings and DNS reachability.

## Scenario 3: DNS works but the website does not open

Check:

``` bash
dig example.com
nc -vz example.com 443
curl -Iv https://example.com
```

Investigate routing, firewall rules, TCP connectivity, TLS certificates
and the web service.

## Scenario 4: Connection refused

Possible causes:

-   No service listening on the destination port.
-   Service listening only on localhost.
-   Firewall actively rejecting traffic.
-   Wrong destination port.

Commands:

``` bash
sudo ss -ltnp
sudo systemctl status SERVICE_NAME
```

## Scenario 5: Connection timeout

Possible causes:

-   Packets dropped by firewall.
-   Missing route.
-   Destination unavailable.
-   Network path problem.
-   Incorrect address.

Commands:

``` bash
ip route get DESTINATION_IP
traceroute DESTINATION_IP
nc -vz DESTINATION_IP PORT
```

## Scenario 6: SSH is unavailable

Check:

``` bash
sudo systemctl status ssh
sudo ss -ltnp 'sport = :22'
sudo ufw status
```

Also check the remote firewall, routing and SSH configuration.

## Scenario 7: Slow network

Investigate:

-   Link speed and duplex.
-   Packet loss.
-   Latency and jitter.
-   Interface errors.
-   Congestion.
-   DNS delay.
-   Server CPU and disk performance.

Commands:

``` bash
ping -c 20 DESTINATION_IP
ip -s link
sudo ethtool eth0
ss -s
```

## Scenario 8: Intermittent connectivity

Investigate:

-   Physical cable or wireless interference.
-   Interface resets.
-   Duplicate IP addresses.
-   DHCP lease issues.
-   Switch port errors.
-   Routing changes.
-   Firewall state or connection limits.

Check logs:

``` bash
journalctl -u systemd-networkd
journalctl -u NetworkManager
dmesg | grep -i -E 'link|network|eth'
```

The relevant service depends on the Linux network manager in use.

## Scenario 9: Application listens only on localhost

Inspect:

``` bash
sudo ss -ltnp
```

If a service listens on `127.0.0.1:8080`, remote machines cannot connect
directly to it through the server's LAN IP.

The application may need to bind to an appropriate interface address,
such as `0.0.0.0`, subject to firewall and security requirements.

## Scenario 10: Duplicate IP address

Symptoms:

-   Intermittent access.
-   ARP entries changing.
-   Conflicting device connectivity.

Investigate:

``` bash
ip neigh
ip addr
```

Check DHCP reservations and static address allocation to ensure each
host has a unique address.

------------------------------------------------------------------------

# 20. Interview questions

## Beginner

1.  What is computer networking?
2.  What is the difference between LAN and WAN?
3.  What is a MAC address?
4.  What is an IP address?
5.  What is a switch?
6.  What is a router?
7.  What is a gateway?
8.  What is DNS?
9.  What is DHCP?
10. What is the OSI model?

## Intermediate

11. Explain the TCP three-way handshake.
12. What is the difference between TCP and UDP?
13. What is subnetting?
14. What is CIDR?
15. What is ARP?
16. What is the difference between a hub and a switch?
17. What is the difference between a switch and a router?
18. What is NAT?
19. What is a VLAN?
20. What is the difference between access and trunk ports?
21. What is STP?
22. What is the difference between HTTP and HTTPS?
23. What is the difference between a public and private IP?
24. What is a stateful firewall?
25. What is a default route?

## Advanced

26. Explain how a host communicates with a remote subnet.
27. Explain how a switch learns MAC addresses.
28. What happens when a switch receives a frame with an unknown
    destination MAC?
29. What is inter-VLAN routing?
30. What is the difference between static and dynamic routing?
31. Explain OSPF and BGP.
32. What is MTU and what problems can an MTU mismatch cause?
33. What is the difference between packet loss and latency?
34. How do you troubleshoot a DNS issue?
35. How do you troubleshoot a TCP connection timeout?
36. Explain the difference between connection refused and connection
    timeout.
37. How do you find which process is listening on a Linux port?
38. How do you inspect a packet using tcpdump?
39. What is the difference between nftables and iptables?
40. What happens when a Linux host sends a packet to another subnet?

## Practical interview exercises

### Exercise 1

A Linux server has:

``` text
IP: 192.168.1.10/24
Gateway: 192.168.2.1
```

What is wrong?

**Answer:** The configured gateway is outside the directly connected
`192.168.1.0/24` subnet. Unless a special on-link route or other
arrangement exists, this gateway configuration is invalid for ordinary
Ethernet routing.

### Exercise 2

A service is running, but another machine cannot connect to it. What do
you check?

**Answer:**

1.  Is the service listening?
2.  On which address is it listening?
3.  Is the destination port correct?
4.  Is the host firewall allowing traffic?
5.  Is the network path correct?
6.  Are upstream firewalls or switches blocking traffic?

### Exercise 3

You can ping `8.8.8.8` but cannot resolve `example.com`. What do you
investigate?

**Answer:** DNS resolver configuration, DNS service availability,
UDP/TCP port 53 connectivity and name-resolution logs.

### Exercise 4

Two computers are in the same subnet but cannot communicate. What do you
investigate?

**Answer:** IP configuration, subnet mask, link status, VLAN membership,
switch port status, ARP/neighbor entries and host firewall rules.

### Exercise 5

A server can connect to a remote host, but the response is slow. What do
you investigate?

**Answer:** Latency, packet loss, routing, congestion, server resource
utilization, DNS delay and application response time.

------------------------------------------------------------------------

# 21. Quick reference sheets

## 21.1 Essential Linux commands

  Requirement            Command
  ---------------------- -----------------------
  View interfaces        `ip link`
  View IP addresses      `ip addr`
  View routes            `ip route`
  Check selected route   `ip route get IP`
  View neighbor cache    `ip neigh`
  Test connectivity      `ping -c 4 IP`
  DNS lookup             `dig DOMAIN`
  Name resolution        `getent hosts DOMAIN`
  Listening sockets      `ss -tulnp`
  TCP connectivity       `nc -vz HOST PORT`
  HTTP request           `curl -v URL`
  Trace network path     `traceroute HOST`
  Capture packets        `tcpdump -i eth0`
  View link details      `ethtool eth0`
  Firewall status        `ufw status`
  Resolver status        `resolvectl status`
  Time synchronization   `timedatectl`

## 21.2 Common port reference

       Port Service
  --------- ------------
      20/21 FTP
         22 SSH
         23 Telnet
         25 SMTP
         53 DNS
      67/68 DHCP
         69 TFTP
         80 HTTP
        110 POP3
        123 NTP
        143 IMAP
    161/162 SNMP
        389 LDAP
        443 HTTPS
        445 SMB
        514 Syslog
        636 LDAPS
        993 IMAPS
        995 POP3S
       3306 MySQL
       5432 PostgreSQL
       6379 Redis

## 21.3 Important abbreviations

  Abbreviation   Meaning
  -------------- -------------------------------------
  LAN            Local Area Network
  WAN            Wide Area Network
  WLAN           Wireless Local Area Network
  NIC            Network Interface Card
  MAC            Media Access Control
  IP             Internet Protocol
  TCP            Transmission Control Protocol
  UDP            User Datagram Protocol
  DNS            Domain Name System
  DHCP           Dynamic Host Configuration Protocol
  ARP            Address Resolution Protocol
  ICMP           Internet Control Message Protocol
  NAT            Network Address Translation
  PAT            Port Address Translation
  CIDR           Classless Inter-Domain Routing
  MTU            Maximum Transmission Unit
  VLAN           Virtual Local Area Network
  STP            Spanning Tree Protocol
  VPN            Virtual Private Network
  NIC            Network Interface Card
  TLS            Transport Layer Security
  SNMP           Simple Network Management Protocol
  NTP            Network Time Protocol
  OSPF           Open Shortest Path First
  BGP            Border Gateway Protocol

------------------------------------------------------------------------

# 22. Learning plan

Suggested duration: 8 weeks, with 60--90 minutes of study and practice
per day.

  -----------------------------------------------------------------------
  Week                    Focus                   Practical outcome
  ----------------------- ----------------------- -----------------------
  1                       Networking fundamentals Explain switches,
                          and devices             routers, firewalls and
                                                  topologies

  2                       OSI, TCP/IP, Ethernet   Explain frame and
                          and MAC                 packet delivery

  3                       IPv4, IPv6 and          Calculate network
                          subnetting              ranges

  4                       Routing and protocols   Understand DNS, DHCP,
                                                  ARP, TCP and UDP

  5                       Linux interfaces and    Configure a Linux
                          configuration           network interface

  6                       Linux routes, DNS and   Configure and verify
                          firewall                host networking

  7                       Troubleshooting and     Diagnose connectivity
                          packet analysis         using Linux tools

  8                       Practical labs and      Complete a multi-host
                          revision                Linux networking lab
  -----------------------------------------------------------------------

## Weekly assessment

At the end of each week, be able to:

-   Explain the concepts without reading notes.
-   Draw the relevant network flow.
-   Run the relevant commands.
-   Interpret command output.
-   Troubleshoot one deliberately introduced fault.

------------------------------------------------------------------------

# 23. Glossary

  -----------------------------------------------------------------------
  Term                                Meaning
  ----------------------------------- -----------------------------------
  Broadcast                           One-to-all delivery within a
                                      broadcast domain

  Unicast                             One-to-one delivery

  Multicast                           One-to-selected-group delivery

  Anycast                             Same address advertised from
                                      multiple locations; routing selects
                                      a destination

  Collision domain                    Network segment where simultaneous
                                      transmissions could collide in
                                      shared-medium Ethernet

  Broadcast domain                    Network area receiving a Layer 2
                                      broadcast

  Gateway                             Entry or exit point between
                                      networks or systems

  Next hop                            Next router or device toward a
                                      destination

  Socket                              Communication endpoint identified
                                      by an address and port, along with
                                      transport protocol context

  Handshake                           Initial exchange used to establish
                                      communication

  Retransmission                      Sending data again when required

  Packet capture                      Recording network packets for
                                      analysis

  Latency                             Delay in communication

  Jitter                              Variation in delay

  Throughput                          Actual data transfer rate

  MTU                                 Maximum transmission unit

  VLAN                                Logical Layer 2 network segment

  Trunk                               Link carrying multiple VLANs

  Access port                         Switch port assigned to an access
                                      VLAN

  Route                               Instruction describing how to reach
                                      a destination network

  Resolver                            Component that obtains DNS answers
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Recommended official references

Use these references to validate details and explore topics further:

1.  **Ubuntu Server networking:**
    https://documentation.ubuntu.com/server/explanation/networking/
2.  **Linux `ip` command:**
    https://man7.org/linux/man-pages/man8/ip.8.html
3.  **Linux `ss` command:**
    https://man7.org/linux/man-pages/man8/ss.8.html
4.  **Linux `tcpdump` manual:**
    https://www.tcpdump.org/manpages/tcpdump.1.html
5.  **Wireshark documentation:** https://www.wireshark.org/docs/
6.  **RFC Editor:** https://www.rfc-editor.org/
7.  **Cisco networking learning resources:**
    https://www.cisco.com/site/us/en/learn/training-certifications/training/index.html

------------------------------------------------------------------------

# Final learning recommendation

Do not rush through subnetting, routing, switching, DNS, TCP/IP and
Linux troubleshooting. These topics form the foundation of practical
networking.

Your first milestone should be:

1.  Connect two or three Ubuntu machines to the same LAN.
2.  Identify their interfaces and MAC addresses.
3.  Configure and verify IP addresses.
4.  Test communication within the subnet.
5.  Configure SSH.
6.  Inspect routes and DNS.
7.  Test TCP ports.
8.  Capture packets with tcpdump.
9.  Configure a firewall.
10. Troubleshoot a deliberately broken connection.

Once you can explain and perform these tasks independently, you will
have a strong practical foundation in computer networking and Linux
system administration.
