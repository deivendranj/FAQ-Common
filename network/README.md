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
</b></details>

<details>
<summary>What is Asymmetric Routing? How do deal with it?</summary><br><b>
</b></details>

<details>
<summary>What overlay (tunnel) protocols are you familiar with?</summary><br><b>
</b></details>

<details>
<summary>What is GRE? How does it works?</summary><br><b>
</b></details>

<details>
<summary>What is VXLAN? How does it works?</summary><br><b>
</b></details>

<details>
<summary>What is SNAT?</summary><br><b>
</b></details>

<details>
<summary>Explain OSPF</summary><br><b>
</b></details>

<details>
<summary>Explain Spine & Leaf</summary><br><b>
</b></details>

<details>
<summary>What is Network Congestion? What can cause it?</summary><br><b>
</b></details>

<details>
<summary>What can you tell me about UDP packet format? What about TCP packet format? How is it different?</summary><br><b>
</b></details>

<details>
<summary>What is the exponential backoff algorithm? Where is it used?</summary><br><b>
</b></details>

<details>
<summary>Using Hamming code, what would be the code word for the following data word 100111010001101?</summary><br><b>

00110011110100011101
</b></details>

