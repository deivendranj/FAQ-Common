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

You can read more about the OSI model in [penguintutor.com](http://www.penguintutor.com/linux/basic-network-reference)
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
<summary>Describe the following network devices and the difference between them:</summary><br><b>

  * router
  * switch
  * hub</summary><br><b>
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
</b></details>
