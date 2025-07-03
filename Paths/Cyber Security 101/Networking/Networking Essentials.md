Link: https://tryhackme.com/room/networkingessentials (Premium Room)

![image](https://github.com/user-attachments/assets/f59ce9d3-e508-4b1a-86e3-14f8faff572e)

Explore networking protocols from automatic configuration to routing packets to the destination.

**Module 1: Introduction**

Have you ever wondered how your computer can dynamically configure its network settings when you turn it on or connect it to a new network? Have you ever wanted to know how many devices and countries your packets passed through before reaching their destination? Are you curious how all your home devices can access the Internet even though your ISP gives you a single IP address?

If you want to know the answers to these questions, among others, then this room is for you.

This room is the second room in a series of four rooms about computer networking:


- [Networking Concepts](https://tryhackme.com/room/networkingconcepts)
  
- Networking Essentials (this room)

- [Networking Core Protocols](https://tryhackme.com/room/networkingcoreprotocols)

- [Networking Secure Protocols](https://tryhackme.com/room/networkingsecureprotocols)

Learning Prerequisites

To benefit from this room, we recommend that you know the following:

- ISO OSI model and layers

- TCP/IP model and layers

- Ethernet, IP, and TCP protocols

In other words, starting this room after [Networking Concepts](https://tryhackme.com/room/networkingconcepts) is the recommended approach.

Learning Objectives

The objective of this room is to teach you about various standard protocols and technologies that glue things together:

- Dynamic Host Configuration Protocol (DHCP)

- Address Resolution Protocol (ARP)

- Network Address Translation (NAT)

- Internet Control Message Protocol (ICMP)

- Ping

- Traceroute

**Answer the questions below**

_Get your notepad ready, and let’s begin._

Answer: `No answer needed`

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 2: DHCP: Give Me My Network Settings**

You went to your favourite coffee shop, grabbed your favourite hot drink, and opened your laptop. Your laptop connected to the shop’s WiFi and automatically configured the network, so you could now work on a new TryHackMe room. You didn’t type a single IP address, yet your device is all set up. Let’s see how this happened.

Whenever we want to access a network, at the very least, we need to configure the following:

- IP address along with subnet mask

- Router (or gateway)

- DNS server

Whenever we connect our device to a new network, the above configurations must be set according to the new network. Manually configuring these settings is a good option, especially for servers. Servers are not expected to switch networks; you don’t carry your domain controller and connect it to the coffee shop WiFi. Moreover, other devices need to connect to the servers and expect to find them at specific IP addresses.

Having an automated way to configure connected devices has many advantages. First, it would save us from manually configuring the network; this is extremely important, especially for mobile devices. Secondly, it saves us from address conflicts, i.e., when two devices are configured with the same IP address. An IP address conflict would prevent the involved hosts from using the network resources; this applies to local resources and the Internet. The solution lies in using Dynamic Host Configuration Protocol (DHCP). DHCP is an application-level protocol that relies on UDP; the server listens on UDP port 67, and the client sends from UDP port 68. Your smartphone and laptop are configured to use DHCP by default.

![image](https://github.com/user-attachments/assets/ac3c26e5-69f2-4d93-8d19-7d7149eec787)

DHCP follows four steps: Discover, Offer, Request, and Acknowledge (DORA):

- _**DHCP Discover**_: The client broadcasts a DHCPDISCOVER message seeking the local DHCP server if one exists.

- _**DHCP Offer**_: The server responds with a DHCPOFFER message with an IP address available for the client to accept.

- _**DHCP Request**_: The client responds with a DHCPREQUEST message to indicate that it has accepted the offered IP.

- _**DHCP Acknowledge**_: The server responds with a DHCPACK message to confirm that the offered IP address is now assigned to this client.

![image](https://github.com/user-attachments/assets/b8a05fab-9edd-49bb-a374-00768bd08d66)

The following packet capture shows the four steps explained above. In this example, the client gets the address 192.168.66.133.

```        
user@TryHackMe$ tshark -r DHCP-G5000.pcap -n
    1   0.000000      0.0.0.0 → 255.255.255.255 DHCP 342 DHCP Discover - Transaction ID 0xfb92d53f
    2   0.013904 192.168.66.1 → 192.168.66.133 DHCP 376 DHCP Offer    - Transaction ID 0xfb92d53f
    3   4.115318      0.0.0.0 → 255.255.255.255 DHCP 342 DHCP Request  - Transaction ID 0xfb92d53f
    4   4.228117 192.168.66.1 → 192.168.66.133 DHCP 376 DHCP ACK      - Transaction ID 0xfb92d53f
```

In the DHCP packet exchange, we can notice the following:

- The client starts without any IP network configuration. It only has a MAC address. In the first and third packets, DHCP Discover and DHCP Request, the client searching for a DHCP server still has no IP network configuration and has not yet used the DHCP server’s offered IP address. Therefore, it sends packets from the IP address 0.0.0.0 to the broadcast IP address 255.255.255.255.

- As for the link layer, in the first and third packets, the client sends to the broadcast MAC address, ff:ff:ff:ff:ff:ff (not shown in the output above). The DHCP server offers an available IP address along with the network configuration in the DHCP offer. It uses the client’s destination MAC address. (It used the proposed IP address in this example system.)

At the end of the DHCP process, our device would have received all the configuration needed to access the network or even the Internet. In particular, we expect that the DHCP server has provided us with the following:

- The leased IP address to access network resources

- The gateway to route our packets outside the local network

- A DNS server to resolve domain names (more on this later)

**Answer the questions below**

_How many steps does DHCP use to provide network configuration?_

Answer: `4`

_What is the destination IP address that a client uses when it sends a DHCP Discover packet?_

Answer: `255.255.255.255`

_What is the source IP address a client uses when trying to get IP network configuration over DHCP?_

Answer: `0.0.0.0`

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 3: ARP: Bridging Layer 3 Addressing to Layer 2 Addressing**

