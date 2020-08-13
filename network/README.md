# FAQ-Common
<details>
<summary>What is subnetmask?</summary><br><b>


A Subnet mask is a 32-bit number that masks an IP address, and divides the IP address into network address and host address. Subnet Mask is made by setting network bits to all "1"s and setting host bits to all "0"s. Within a given network, two host addresses are reserved for special purpose, and cannot be assigned to hosts. The "0" address is assigned a network address and "255" is assigned to a broadcast address, and they cannot be assigned to hosts.

**For Example**

```
| Address Class | No of Network Bits | No of Host Bits | Subnet mask     | CIDR notation |
| ------------- | ------------------ | --------------- | --------------- | ------------- |
| A             | 8                  | 24              | 255.0.0.0       | /8            |
| A             | 9                  | 23              | 255.128.0.0     | /9            |
| A             | 12                 | 20              | 255.240.0.0     | /12           |
| A             | 14                 | 18              | 255.252.0.0     | /14           |
| B             | 16                 | 16              | 255.255.0.0     | /16           |
| B             | 17                 | 15              | 255.255.128.0   | /17           |
| B             | 20                 | 12              | 255.255.240.0   | /20           |
| B             | 22                 | 10              | 255.255.252.0   | /22           |
| C             | 24                 | 8               | 255.255.255.0   | /24           |
| C             | 25                 | 7               | 255.255.255.128 | /25           |
| C             | 28                 | 4               | 255.255.255.240 | /28           |
| C             | 30                 | 2               | 255.255.255.252 | /30           |


```
</b></details>

<details>
<summary>What is an IP address and why do we need it?</summary><br><b>

A private IP address, sometimes called a local IP address, is an IP address reserved for use on a private network. These devices can’t be accessed by devices outside their own network—they’re effectively invisible, except to each other.

Private IP addresses can be either static or dynamic, but in each case, the available addresses are limited to a pool set aside specifically for being private. These addresses are different from public IP addresses in that they don’t have to be unique—other devices can use the same address provided they aren’t on the same network. This is because devices on the private network can’t communicate with outside devices, which eliminates the risk of an address conflict.

</b></details>

<details>
<summary>Explain the OSI model. What layers there are? What each layer is responsible for?</summary><br><b>

- Application: user end (HTTP is here)
- Presentation: establishes context between application-layer entities (Encryption is here)
- Session: establishes, manages and terminates the connections
- Transport: transfers variable-length data sequences from a source to a destination host (TCP & UDP are here)
- Network: transfers datagrams from one network to another (IP is here)
- Data link: provides a link between two directly connected nodes (MAC is here)
- Physical: the electrical and physical spec the data connection (Bits are here)

![alt text](https://github.com/deivendranj/FAQ-Common/blob/master/images/Picture1.jpg?raw=true)
</b></details>

<details>
<summary>What delivery schemes are you familiar with?</summary><br><b>

Unitcast: One to one communication where there is one sender and one receiver.

Broadcast: Sending a message to everyone in the network. The address ff:ff:ff:ff:ff:ff is used for broadcasting.
           Two common protocols which use broadcast are ARP and DHCP.

Multicast: Sending a message to a group of subscribers. It can be one-to-many or many-to-many.
</b></details>

<details>
<summary>What is CSMA/CD? Is it used in modern ethernet networks?</summary><br><b>

CSMA/CD stands for Carrier Sense Multiple Access / Collision Detection.
Its primarily focus it to manage access to shared medium/bus where only one host can transmit at a given point of time.

CSMA/CD algorithm:

1. Before sending a frame, it checks whether another host already transmitting a frame.
2. If no one transmitting, it starts transmitting the frame.
3. If two hosts transmitted at the same time, we have a collision.
4. Both hosts stop sending the frame and they send to everyone a 'jam signal' notifying everyone that a collision occurred
5. They are waiting for a random time before sending again
6. Once each host waited for a random time, they try to send the frame again and so the
</b></details>

<details>
<summary>Describe the following network devices and the difference between them: </summary><br><b>

  * router
  * switch
  * hub
</b></details>

<details>
<summary>How does a router works?</summary><br><b>

A router is a physical or virtual appliance that passes information between two or more packet-switched computer networks. A router inspects a given data packet's destination Internet Protocol address (IP address), calculates the best way for it to reach its destination and then forwards it accordingly.


</b></details>

<details>
<summary>What is NAT?</summary><br><b>

 Network Address Translation (NAT) is a process in which one or more local IP address is translated into one or more Global IP address and vice versa in order to provide Internet access to the local hosts. 


</b></details>

<details>
<summary>What is a proxy? How does it works? What do we need it for?</summary><br><b>

A proxy server acts as a gateway between you and the internet. It’s an intermediary server separating end users from the websites they browse.

If you’re using a proxy server, internet traffic flows through the proxy server on its way to the address you requested. The request then comes back through that same proxy server (there are exceptions to this rule), and then the proxy server forwards the data received from the website to you.

roxy servers provide varying levels of functionality, security, and privacy depending on your use case, needs, or company policy.


</b></details>

<details>
<summary>What is TCP? How does it works? What is the 3 way handshake?</summary><br><b>

TCP 3-way handshake or three-way handshake is a process which is used in a TCP/IP network to make a connection between server and client.

A three-way handshake is primarily used to create a TCP socket connection. It works when:

- A client node sends a SYN data packet over an IP network to a server on the same or an external network. The objective of this packet is to ask/infer if the server is open for new connections.
- The target server must have open ports that can accept and initiate new connections. When the server receives the SYN packet from the client node, it responds and returns a confirmation receipt – the ACK packet or SYN/ACK packet.
- The client node receives the SYN/ACK from the server and responds with an ACK packet.
![alt text](https://www.guru99.com/images/1/092119_0753_TCP3WayHand1.png)
</b></details>

<details>
<summary>How does SSL handshake work?</summary><br><b>
For SSL/TLS negotiation to take place, the system administrator must prepare the minimum of 2 files: Private Key and Certificate. When requesting from a Certificate Authority such as Trust Services, an additional file must be created. This file is called Certificate Signing Request, generated from the Private Key. The process for generating the files are dependent on the software that will be using the files for encryption. For a list of the server softwares DigiCert has, look at: DigiCert CSR Generation.

Note that although certificates requested from Certificate Authorities such as DigICert are inherently trusted by most clients, additional certificates called Intermediate Certificate Authority Certificates and Certificate Authority Root Certificates may need to be installed on the server. This is again server software dependent. There is usually no need to install the Intermediate and Root CA files on the client applications or browsers.

Once the files are ready and correctly installed, just start the SSL/TLS negotiation by using the secured protocol.  On browser applications it is usually https://www.digicert.com. Remember to use your secured website address. Above is just a sample address.

![alt text](https://github.com/deivendranj/FAQ-Common/blob/master/images/Picture2.jpg?raw=true)

</b></details>

<details>
<summary>What is the difference between TCP and UDP?</summary><br><b>
	
TCP establishes a connection between the client and the server to guarantee the order of the packages, on the other hand, UDP does not establish a connection between client and server and doesn't handle package order. This makes UDP more lightweight than TCP and a perfect candidate for services like streaming.

![alt text](https://www.homenethowto.com/wp-content/uploads/table-tcp-udp.png)
</b></details>

<details>
<summary>What TCP/IP protocols are you familiar with?</summary><br><b>
</b></details>

<details>
<summary>Explain "default gateway"</summary><br><b>

A default gateway serves as an access point or IP router that a networked computer uses to send information to a computer in another network or the internet.
</b></details>

<details>
<summary>What is ARP? How does it works?</summary><br><b>

ARP stands for Address Resolution Protocol. When you try to ping an IP address on your local network, say 192.168.1.1, your system has to turn the IP address 192.168.1.1 into a MAC address. This involves using ARP to resolve the address, hence its name.

Systems keep an ARP look-up table where they store information about what IP addresses are associated with what MAC addresses. When trying to send a packet to an IP address, the system will first consult this table to see if it already knows the MAC address. If there is a value cached, ARP is not used.
</b></details>

<details>
<summary>What is TTL?</summary><br><b>

Time to live (TTL) refers to the amount of time or “hops” that a packet is set to exist inside a network before being discarded by a router. TTL is also used in other contexts including CDN caching and DNS caching.

When a packet of information is created and sent out across the Internet, there is a risk that it will continue to pass from router to router indefinitely. To mitigate this possibility, packets are designed with an expiration called a time-to-live or hop limit. Packet TTL can also be useful in determining how long a packet has been in circulation, and allow the sender to receive information about a packet’s path through the Internet.

Each packet has a place where it stores a numerical value determining how much longer it should continue to move through the network. Every time a router receives a packet, it subtracts one from the TTL count and then passes it onto the next location in the network. If at any point the TTL count is equal to zero after the subtraction, the router will discard the packet and send an ICMP message back to the originating host.

The commonly used network commands ping and traceroute both utilize TTL. When using the traceroute command, a stream of packets with increasingly higher sequential TTLs are sent across the Internet towards a destination. Because each step along the connection is the last stop for one of the packets, each location will return an ICMP message to the sender after discarding the packet. The time it takes for the ICMP message to return to the sender is then used to determine how long it takes to get to each successive hop along the network.

![alt_text](https://www.cloudflare.com/img/learning/cdn/glossary/ttl/icmp-traceroute-diagram.png)
</b></details>

<details>
<summary>What is DHCP? How does it works?</summary><br><b>

Dynamic Host Configuration Protocol (DHCP) is a network management protocol used to automate the process of configuring devices on IP networks, thus allowing them to use network services such as DNS, NTP, and any communication protocol based on UDP or TCP. A DHCP server dynamically assigns an IP address and other network configuration parameters to each device on a network so they can communicate with other IP networks. DHCP is an enhancement of an older protocol called BOOTP. DHCP is an important part of the DDI solution (DNS-DHCP-IPAM).

![alt_text](https://bluecatnetworks.com/wp-content/uploads/2020/05/How-does-DHCP-work-1024x428.png)
</b></details>

<details>
<summary>What is SSL tunneling? How does it works?</summary><br><b>
	
SSL Tunneling involves a client that requires an SSL connection to a backend service or secure server via a proxy server. This proxy server opens the connection between the client and the backend service and copies the data to both sides without any direct interference in the SSL connection.
	
![alt_text](http://2.bp.blogspot.com/-08V2nH2GClU/VjpSnA1kl1I/AAAAAAAABOk/jtTzIzhcvRE/s400/image2.png)
</b></details>

<details>
<summary>What is a socket? Where can you see the list of sockets in your system?</summary><br><b>
	A socket is one endpoint of a two-way communication link between two programs running on the network. A socket is bound to a port number so that the TCP layer can identify the application that data is destined to be sent to. An endpoint is a combination of an IP address and a port number
</b></details>

<details>
<summary>What is IPv6? Why should we consider using it if we have IPv4?</summary><br><b>
	Internet Protocol version 6 is the most recent version of the Internet Protocol, the communications protocol that provides an identification and location system for computers on networks and routes traffic across the Internet
</b></details>

<details>
<summary>What is VLAN?</summary><br><b>
	A virtual LAN is any broadcast domain that is partitioned and isolated in a computer network at the data link layer. LAN is the abbreviation for local area network and in this context virtual refers to a physical object recreated and altered by additional logic
</b></details>

<details>
<summary>What is MTU?</summary><br><b>
	In computer networking, the maximum transmission unit (MTU) is the size of the largest protocol data unit (PDU) that can be communicated in a single network layer transaction.[1] The MTU relates to, but is not identical to the maximum frame size that can be transported on the data link layer, e.g. Ethernet frame.

Larger MTU is associated with reduced overhead. Smaller MTU values can reduce network delay. In many cases, MTU is dependent on underlying network capabilities and must be adjusted manually or automatically so as to not exceed these capabilities. MTU parameters may appear in association with a communications interface or standard. Some systems may decide MTU at connect time.
</b></details>

<details>
<summary>What happens if you send a packet that is bigger than the MTU?</summary><br><b>
	In computer networking, the maximum transmission unit (MTU) is the size of the largest protocol data unit (PDU) that can be communicated in a single network layer transaction.[1] The MTU relates to, but is not identical to the maximum frame size that can be transported on the data link layer, e.g. Ethernet frame.

Larger MTU is associated with reduced overhead. Smaller MTU values can reduce network delay. In many cases, MTU is dependent on underlying network capabilities and must be adjusted manually or automatically so as to not exceed these capabilities. MTU parameters may appear in association with a communications interface or standard. Some systems may decide MTU at connect time.
</b></details>

<details>
<summary>True or False?. Ping is using UDP because it doesn't care about reliable connection</summary><br><b>
</b></details>

<details>
<summary>What is SDN?</summary><br><b>
	Software-defined networking technology is an approach to network management that enables dynamic, programmatically efficient network configuration in order to improve network performance and monitoring, making it more like cloud computing than traditional network management. 
</b></details>

<details>
<summary>What is ICMP? What is it used for?</summary><br><b>
	The Internet Control Message Protocol is an internet layer protocol used by network devices to diagnose network communication issues. ICMP is mainly used to determine whether or not data is reaching its intended destination in a timely manner. Commonly, the ICMP protocol is used on network devices, such as routers.
	
![alt_text](https://cdn.slidesharecdn.com/ss_thumbnails/internetcontrolmessageprotocol-121115085749-phpapp01-thumbnail-4.jpg?cb=1352969905)
</b></details>

<details>
<summary>What is NAT? How does it works?</summary><br><b>
	It enables private IP networks that use unregistered IP addresses to connect to the Internet. NAT operates on a router, usually connecting two networks together, and translates the private (not globally unique) addresses in the internal network into legal addresses, before packets are forwarded to another network
</b></details>

<details>
<summary>Which factors affect network performances</summary><br><b>
	* the number of devices on the network
	* the bandwidth of the transmission medium
	* the type of network traffic
	* network latency
	* the number of transmission errors
</b></details>

<details>
<summary>What the terms "Data Plane" and "Control Plane" refer?</summary><br><b>

The exact meaning is usually depends on the context but overall data plane refers to all the functions that forward packets and/or frames from one interface to another while control plane refers to all the functions that make use of routing protocols.

There is also "Management Plane" which refers to monitoring and management functions.
</b></details>

<a name="network-advanced"></a>
#### :star: Advanced

<details>
<summary>Explain Spanning Tree Protocol (STP)</summary><br><b>
	Spanning Tree Protocol (STP) is a link management protocol that provides path redundancy while preventing undesirable loops in the network. When it comes to ethernet networks, only one active path can exist between two stations in order for them to function properly. Loops occur in networks for a variety of reason
</b></details>

<details>
<summary>What is link aggregation? Why is it used?</summary><br><b>

Link aggregation is a way of bundling a bunch of individual (Ethernet) links together so they act like a single logical link. ... Another important reason for using link aggregation is to provide fast and transparent recovery in case one of the individual links fails

Within the IEEE specification the Link Aggregation Control Protocol (LACP) provides a method to control the bundling of several physical ports together to form a single logical channel. LACP allows a network device to negotiate an automatic bundling of links by sending LACP packets to the peer (directly connected device that also implements LACP). LACP works by sending frames (LACPDUs) down all links that have the protocol enabled. If it finds a device on the other end of the link that also has LACP enabled, it will also independently send frames along the same links enabling the two units to detect multiple links between themselves and then combine them into a single logical link.

LACP can be configured in one of two modes: active or passive. In active mode it will always send frames along the configured links. In passive mode however, it acts as "speak when spoken to", and therefore can be used as a way of controlling accidental loops (as long as the other device is in active mode).

Some claim that the most important feature of link aggregation is link failover. With link failover, traffic from a failed link can be switched over to working links in the aggregation. For security purposes, data is transmitted over the usual link and the other link in the aggregation sits idle or can transmit data from another physical link. If the first link goes down, a signal is sent to the second link to take over data transmission. In this situation, the second link can be set to either continue taking on data from both streams at a slower transmission rate or it can be set to prioritize which data has a higher priority.

</b></details>

<details>
<summary>What is Asymmetric Routing? How do deal with it?</summary><br><b>

Asymmetric routing is when a packet takes one path to the destination and takes another path when returning to the source. For example, review the following diagram. Packets from A to B take one route and packets from B to A take another route.

![alt_text](https://networkqna.com/wp-content/uploads/2016/10/asymmetric.jpg)

Solution:-
The solution to this problem is to adjust the placement of the firewalls or internal routing such that traffic in both directions flows through the same firewall, even if incoming traffic enters the network through a different router than the router that handled the matching outgoing traffic
</b></details>

<details>
<summary>What overlay (tunnel) protocols are you familiar with?</summary><br><b>

Overlays are logical tunnels. A logical connection between two devices, in our case, two Silver Peak appliances. created for different traffic types and policies (such as VoIP. A protocol optimized for the transmission of voice through the Internet or other packet-switched networks.).

</b></details>

<details>
<summary>What is GRE? How does it works?</summary><br><b>
	
Generic Routing Encapsulation (GRE) is a tunneling protocol developed by Cisco Systems that can encapsulate a wide variety of network layer protocols inside virtual point-to-point links or point-to-multipoint links over an Internet Protocol network

![alt_text](https://www.9tut.com/images/ccna_self_study/GRE_Tunnel/GRE_Tunnel.jpg)
</b></details>

<details>
<summary>What is VXLAN? How does it works?</summary><br><b>

Virtual Extensible LAN is a network virtualization technology that attempts to address the scalability problems associated with large cloud computing deployment.
VXLAN is the most commonly used protocol to create overlay networks enabling the use of a virtual network of switches, routers, firewalls & load balancers
It provides a way to extend Layer 2 segments over the underlying shared network infrastructure so that tenant workloads can be placed across physical pods in the data center. Higher scalability to address more Layer 2 segments. VXLAN uses a 24-bit segment ID, the VXLAN network identifier (VNID).

![alt_text](https://blogs.vmware.com/vsphere/files/2013/05/New-Learning-3.jpg)
</b></details>

<details>
<summary>What is SNAT?</summary><br><b>

Network Address Translation (NAT) occurs when one of the IP addresses in an IP packet header is changed. 

A Secure Network Address Translation (SNAT) is an object that maps the source client IP address in a request to a translation address defined on the BIG-IP device. ... For example, when the BIG-IP system receives a new connection from source IP address 192.168

In a SNAT, the destination IP address is maintained and the source IP address is changed. Most commonly, a SNAT allows a host on the “inside” of the NAT, in an RFC 1918 IP address space, to initiate a connection to a host on the “outside” of the NAT. A DNAT, by way of contrast, occurs when the destination address is changed and the source IP address is maintained. A DNAT allows a host on the “outside” to connect to a host on the “inside”. In both cases, the NAT has to maintain a connection table which tells the NAT where to route returning packets. An important difference between a SNAT and a DNAT is that a SNAT allows multiple hosts on the “inside” to get to any host on the “outside”. By way of contrast, a DNAT allows any host on the “outside” to get to a single host on the “inside”

![alt_text](http://www.commercialventvac.com/finao/DNATs-and-SNATs_html_106dc8c2.gif)
</b></details>

<details>
<summary>Explain OSPF</summary><br><b>

Open shortest path first (OSPF) is a link-state routing protocol which is used to find the best path between the source and the destination router using its own shortest path first (SPF) algorithm. A link-state routing protocol is a protocol which uses the concept of triggered updates, i.e., if there is a change observed in the learned routing table then the updates are triggered only, not like the distance-vector routing protocol where the routing table are exchanged at a period of time.

Open shortest path first (OSPF) is developed by Internet Engineering Task Force (IETF) as one of the Interior Gateway Protocol (IGP), i.e., the protocol which aims at moving the packet within a large autonomous system or routing domain. It is a network layer protocol which works on the protocol number 89 and uses AD value 110. OSPF uses multicast address 224.0.0.5 for normal communication and 224.0.0.6 for update to designated router(DR)/Backup Designated Router (BDR).

![alt_text](https://media.geeksforgeeks.org/wp-content/uploads/rrf.png)

Open shortest path first (OSPF) is a link-state routing protocol which is used to find the best path between the source and the destination router using its own SPF algorithm

Backbone router – The area 0 is known as backbone area and the routers in area 0 are known as backbone routers. If the routers exists partially in the area 0then also it is a backbone router.
Internal router – An internal router is a router which have all of its interfaces in a single area.
Area Boundary Router (ABR) – The router which connects backbone area with another area is called Area Boundary Router. It belongs to more than one area. The ABRs therefore maintain multiple link-state databases that describe both the backbone topology and the topology of the other areas.
4.Area Summary Border Router (ASBR) – When an OSPF router is connected to a different protocol like EIGRP, or Border Gateway Protocol, or any other routing protocol then it is known as AS. The router which connects two different AS (in which one of the interface is operating OSPF) is known as Area Summary Border Router. These routers perform redistribution. ASBRs run both OSPF and another routing protocol, such as RIP or BGP. ASBRs advertise the exchanged external routing information throughout their AS.

</b></details>

<details>
<summary>Explain Spine & Leaf</summary><br><b>
	
A spine-leaf architecture is an increasingly popular data center network topology that consists of two switching layers—a spine and leaf. The leaf layer consists of access switches that aggregate traffic from servers—typically affixed top of rack (ToR) or end of rack (EoR)—and connect directly into the spine or network core. Spine switches interconnect all of the leaf switches in a full-mesh topology

![alt_text](https://www.arubanetworks.com/wp-content/uploads/PoV_Spine-Leaf-Architecture.jpg)

Other common differences in spine-leaf topologies include:

The removal of Spanning Tree Protocol (STP)
Increased use of fixed port switches over modular models for the network backbone
More cabling to purchase and manage, given the higher interconnection count
A scale-out vs. scale-up of infrastructure
</b></details>

<details>
<summary>What is Network Congestion? What can cause it?</summary><br><b>

Network congestion in data networking and queueing theory is the reduced quality of service that occurs when a network node or link is carrying more data than it can handle. Typical effects include queueing delay, packet loss or the blocking of new connections. A consequence of congestion is that an incremental increase in offered load leads either only to a small increase or even a decrease in network throughput.

Too many hosts in broadcast domain. ...
Broadcast Storms. ...
Low Bandwidth. ...
Adding Retransmitting Hubs. ...
Multicasting. ...
Outdated Hardware. ...
Bad Configuration Management. ...
Rogue Adapter Broadcasts
</b></details>

<details>
<summary>What can you tell me about UDP packet format? What about TCP packet format? How is it different?</summary><br><b>

![alt_text](https://skminhaj.files.wordpress.com/2016/02/92926-tcp_udp_headers.jpg)
</b></details>

<details>
<summary>What is the exponential backoff algorithm? Where is it used?</summary><br><b>

Exponential backoff is an algorithm that uses feedback to multiplicatively decrease the rate of some process, in order to gradually find an acceptable rate

</b></details>

<details>
<summary>What is EIGRP and difference between OSPF</summary><br><b>

Enhanced Interior Gateway Routing Protocol (EIGRP) is an advanced distance-vector routing protocol that is used on a computer network for automating routing decisions and configuration. The protocol was designed by Cisco Systems as a proprietary protocol, available only on Cisco routers

EIGRP (Enhanced Interior Gateway Routing Protocol) is a Cisco-based distance vector protocol which works on DUAL (Diffusing Update Algorithm). It is used for sharing the information from one to the neighbouring routers which exist within the same area. Although, it is a complex protocol but we can configure and run it easily in small and large networks. It was devised to overcome the shortcomings of the classical distance vector routing protocols like IGRP and RIP which were hard to scale according to the needs of the network.

</b></details>

<details>
<summary>Explain BGP</summary><br><b>

Border Gateway Protocol (BGP) is used to Exchange routing information for the internet and is the protocol used between ISP which are different ASes. The protocol can connect together any internetwork of autonomous system using an arbitrary topology.

OSPF is a IGP , an Interior Gateway Protocol, much like EIGRP, OSPF, IS-IS, RIP. BGP is a EGP, Exterior Gateway Protocol . And there is only one EGP, that is BGP.

</b></details>

<details>
<summary>Explain Routing Protocols</summary><br><b>

![alt_text](https://www.ciscopress.com/content/images/chap3_9781587133237/elementLinks/03fig09.jpg)

</b></details>

<details>
<summary>What is DNS?</summary><br><b>

The Domain Name System is a hierarchical and decentralized naming system for computers, services, or other resources connected to the Internet or a private network. It associates various information with domain names assigned to each of the participating entities

</b></details>

<details>
<summary>What happens when you type amazon.com in the browser?</summary><br><b>

In general the process is as follows:

The user types an address in the web browser (some_site.com)
The operating system gets a request from the browser to translate the address the user entered
A query created to check a local entry of the address exists in the system. In case it doesn't, the request is forwarded to the DNS resolver
The Resolver is a server, usually configured by your ISP when you connect to the internet, that responsible for resolving your query by contacting other DNS servers
The Resolver contacts the root nameserver (aka as .)
The root nameserver responds with the address of the relevant Top Level Domain DNS server (if your address ends with org then the org TLD)
The Resolver then contacts the TLD DNS and TLD DNS responds with the IP address that matches the address the user typed in the browser
The Resolver passes this information to the browser
The user is happy :D

![alt_text](https://github.com/deivendranj/FAQ-Common/blob/master/images/Picture5.png?raw=true)

</b></details>


<details>
<summary>Explain the resolution sequence of: www.site.com</summary><br><b>

It's resolved in this order:

1) .
2) .com
3) site.com
4) www.site.com
</b></details>

<details>
<summary>What types of DNS records are there?</summary><br><b>

  * A
  * PTR
  * MX
  * AAAA
</b></details>

<details>
<summary>What is a A record?</summary><br><b>

A (Address) Maps a host name to an IP address. When a computer has multiple adapter cards and IP addresses, it should have multiple address records.
</b></details>

<details>
<summary>What is a AAAA record?</summary><br><b>
	
An AAAA Record performs the same function as an A Record, but for an IPv6 Address.
</b></details>

<details>
<summary>What is a PTR record?</summary><br><b>

While an A record points a domain name to an IP address, a PTR record does the opposite and resolves the IP address to a domain name.
</b></details>

<details>
<summary>What is a MX record?</summary><br><b>
MX (Mail Exchange) Specifies a mail exchange server for the domain, which allows mail to be delivered to the correct mail servers in the domain.
</b></details>

<details>
<summary>Is DNS using TCP or UDP?</summary><br><b>
DNS uses UDP port 53 for resolving queries either regular or reverse. DNS uses TCP for zone transfer. 
</b></details>

<details>
<summary>What is Round Robin DNS?</summary><br><b>
</b></details>

<details>
<summary>What is DNS Record TTL? Why do we need it?</summary><br><b>
</b></details>

<details>
<summary>What is a zone? What types of zones are there?</summary><br><b>
</b></details>

<details>
<summary>Explain IPsec briefly</summary><br><b>

In computing, Internet Protocol Security (IPsec) is a secure network protocol suite that authenticates and encrypts the packets of data to provide secure encrypted communication between two computers over an Internet Protocol network. It is used in virtual private networks (VPNs).

IPsec includes protocols for establishing mutual authentication between agents at the beginning of a session and negotiation of cryptographic keys to use during the session. IPsec can protect data flows between a pair of hosts (host-to-host), between a pair of security gateways (network-to-network), or between a security gateway and a host (network-to-host).[1] IPsec uses cryptographic security services to protect communications over Internet Protocol (IP) networks. It supports network-level peer authentication, data-origin authentication, data integrity, data confidentiality (encryption), and replay protection.

The initial IPv4 suite was developed with few security provisions. As a part of the IPv4 enhancement, IPsec is a layer 3 OSI model or internet layer end-to-end security scheme. In contrast, while some other Internet security systems in widespread use operate above layer 3, such as Transport Layer Security (TLS) that operates at the Transport Layer and Secure Shell (SSH) that operates at the Application layer, IPsec can automatically secure applications at the IP layer.

</b></details>

<details>
<summary>Explain VPN and types?</summary><br><b>

VPN stands for Virtual Private Network (VPN), that allows a user to connect to a private network over the Internet securely and privately. VPN creates an encrypted connection that is called VPN tunnel, and all Internet traffic and communication is passed through this secure tunnel.
Virtual Private Network (VPN) is basically of 2 types:

Remote Access VPN:

Remote Access VPN permits a user to connect to a private network and access all its services and resources remotely. The connection between the user and the private network occurs through the Internet and the connection is secure and private. Remote Access VPN is useful for home users and business users both.
An employee of a company, while he/she is out of station, uses a VPN to connect to his/her company’s private network and remotely access files and resources on the private network. Private users or home users of VPN, primarily use VPN services to bypass regional restrictions on the Internet and access blocked websites. Users aware of Internet security also use VPN services to enhance their Internet security and privacy.

Site to Site VPN:

A Site-to-Site VPN is also called as Router-to-Router VPN and is commonly used in the large companies. Companies or organizations, with branch offices in different locations, use Site-to-site VPN to connect the network of one office location to the network at another office location.

Types of Virtual Private Network (VPN) Protocols:

Internet Protocol Security (IPSec):
Layer 2 Tunneling Protocol (L2TP):
Point–to–Point Tunneling Protocol (PPTP):
OpenVPN - OpenVPN is an open source VPN that is commonly used for creating Point-to-Point and Site-to-Site connections. It uses a traditional security protocol based on SSL and TLS protocol.

</b></details>

<details>
<summary>UNDERSTANDING VPN IPSEC TUNNEL MODE AND IPSEC TRANSPORT MODE - WHAT'S THE DIFFERENCE?</summary><br><b>

IPSec’s protocol objective is to provide security services for IP packets such as encrypting sensitive data, authentication, protection against replay and data confidentiality.

As outlined in our IPSec protocol article, Encapsulating Security Payload (ESP) and Authentication Header (AH) are the two IPSec security protocols used to provide these security services.  Analysing  the ESP and AH protocols is out of this article’s scope, however you can turn to our IPSec article where you’ll find an in-depth analysis and packet diagrams to help make the concept clear.

 
UNDERSTANDING IPSEC MODES –TUNNEL MODE & TRANSPORT MODE

IPSec can be configured to operate in two different modes, Tunnel and Transport mode. Use of each mode depends on the requirements and implementation of IPSec.

 
IPSEC TUNNEL MODE

IPSec tunnel mode is the default mode. With tunnel mode, the entire original IP packet is protected by IPSec. This means IPSec wraps the original packet, encrypts it, adds a new IP header and sends it to the other side of the VPN tunnel (IPSec peer).

Tunnel mode is most commonly used between gateways (Cisco routers or ASA firewalls), or at an end-station to a gateway, the gateway acting as a proxy for the hosts behind it.

Tunnel mode is used to encrypt traffic between secure IPSec Gateways, for example two Cisco routers connected over the Internet via IPSec VPN. Configuration and setup of this topology is extensively covered in our Site-to-Site IPSec VPN article. In this example, each router acts as an IPSec Gateway for their LAN, providing secure connectivity to the remote network:

![alt_text](http://www.firewall.cx/images/stories/ipsec-modes-transport-tunnel-5.gif)

IPSEC TRANSPORT MODE

IPSec Transport mode is used for end-to-end communications, for example, for communication between a client and a server or between a workstation and a gateway (if the gateway is being treated as a host).  A good example would be an encrypted Telnet or Remote Desktop session from a workstation to a server.

![alt_text](http://www.firewall.cx/images/stories/ipsec-modes-transport-tunnel-6.gif)

</b></details>

<details>
<summary>What is loadbalancing and how is it done on application layer?</summary><br><b>

Load balancing is defined as the methodical and efficient distribution of network or application traffic across multiple servers in a server farm. Each load balancer sits between client devices and backend servers, receiving and then distributing incoming requests to any available server capable of fulfilling them

</b></details>

<details>
<summary>What are the different types of DNS loadbalancing?</summary><br><b>

DNS load balancing is the practice of configuring a domain in the Domain Name System (DNS) such that client requests to the domain are distributed across a group of server machines. A domain can correspond to a website, a mail system, a print server, or another service that is made accessible via the Internet.

Backup server: A clone instance of a domain is created to serve as a secondary DNS. The primary DNS may redirect traffic to this server at runtime.

Round robin DNS-based load sharing: DNS requests are rotated and shared across multiple domain server instances. Although mainly a load sharing algorithm, this also facilitates load balancing with DNS.

Dynamic DNS load balancing: DNS requests are routed between domain servers with the best available resources and minimal load.

</b></details>

<details>
<summary>BGP states/Attributes</summary><br><b>

In order to make decisions in its operations with peers, a BGP peer uses a simple finite state machine (FSM) that consists of six states: Idle; Connect; Active; OpenSent; OpenConfirm; and Established. For each peer-to-peer session, a BGP implementation maintains a state variable that tracks which of these six states the session is in. The BGP defines the messages that each peer should exchange in order to change the session from one state to another. 

The first state is the "Idle" state. In the "Idle" state, BGP initializes all resources, refuses all inbound BGP connection attempts and initiates a TCP connection to the peer.
The second state is "Connect". In the "Connect" state, the router waits for the TCP connection to complete and transitions to the "OpenSent" state if successful. 
If unsuccessful, it starts the ConnectRetry timer and transitions to the "Active" state upon expiration. 
In the "Active" state, the router resets the ConnectRetry timer to zero and returns to the "Connect" state. 
In the "OpenSent" state, the router sends an Open message and waits for one in return in order to transition to the "OpenConfirm" state. Keepalive messages are exchanged and, upon successful receipt, the router is placed into the "Established" state. 
In the "Established" state, the router can send/receive: Keepalive; Update; and Notification messages to/from its peer.

![alt_text](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/BGP_FSM.svg/220px-BGP_FSM.svg.png)

BGP Path Attributes:

When your BGP speaker receives a BGP prefix, there are going to be many path attributes tagged to it, and we know that these are going to be critical when it comes to BGP doing things like choosing a very best path to a destination. Interestingly, not all of these path attributes are created equal.

All BGP path attributes fall into one of four main categories. Note that this list also provides example attributes in each category. Do not be too concerned with these specific attribute values now, as you will understand many of them fully when you complete this blog series.

* Well-Known Mandatory (for example:  Origin, AS Path, and Next Hop)
* Well-Known Discretionary (for example: Local Preference)
* Optional Transitive (for example: Community)
* Optional Non-Transitive (for example: Cluster List)

</b></details>

<details>
<summary>What is IP fragmentation?</summary><br><b>

IP fragmentation is an Internet Protocol (IP) process that breaks packets into smaller pieces (fragments), so that the resulting pieces can pass through a link with a smaller maximum transmission unit (MTU) than the original packet size. The fragments are reassembled by the receiving host.

![alt_text](https://upload.wikimedia.org/wikipedia/commons/thumb/8/80/PDU_Fragmentaion_-_en.png/400px-PDU_Fragmentaion_-_en.png)

Fragmentation is necessary for data transmission, as every network has a unique limit for the size of datagrams that it can process. This limit is known as the maximum transmission unit (MTU).

</b></details>

<details>
<summary>What is DNS Recursive, Iterative</summary><br><b>


![alt_text](https://www.omnisecu.com/images/tcpip/recursive-iterative-dns-query.jpg)
	
</b></details>
