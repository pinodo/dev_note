<!-- HEADER -->
<div align="center">
  <h1 align="center">1. Internet Network</h1>
</div>

# How Internet Works?
```
Client sends a packet to the server through a bunch of nodes
```

# IP
> Role
> 1. Transport data to designated IP address
> 2. Transport data by transportation unit which is called packet

> Limitation
> 1. Connection Problem - even if there's no end-point, IP sends packets
> 2. Unreliability - missing, unordered sequence
> 3. Addressing

# TCP / UDP
<h3>IP Stack Layers</h3>
> * Application layer - HTTP / FTP
> * Transportation layer - TCP, VDP
> * Internet - IP
> * Network Interface

```
> Protocol Layer
Application       - Web Browser / Network Game
                  - Socket Library <- (1) Program writes a message
OS                - TCP <- (2) A message is transported thru socket library (3) TCP info is created, contains a message data
                  - IP <- (4) IP packet is created, contains TCP data
Network Interface - LAN Driver / LAN Devices <- (5) A packet is contained in a LAN card 
Server            - (6) With an Ethernet frame, a packet is sent to the server             
```

<h3>TCP/IP packet info</h3>
> IP packet (Start IP, End IP, etc,.)
> 
> U
> 
> TCP segment (Start PORT, End PORT, Control Transportation, Order, Auth info, etc,.)
> 
> U
> 
> Data

<h3>TCP Features</h3>
> 1. Connectivity-oriented - TCP 3-way handshake (virtual connection)
> 2. Guarantee data transportation
> 3. Guarantee the order
> 4. Reliable
> 5. Mostly used

<h3>UDP Features</h3>
> 1. Same as IP (+PORT +checksum)
> 2. Simple, Fast

> PORT - Seperates processes in a same IP
> 
> PORT Number
> * 0 ~ 65535: Available
> * 0 ~ 1023: Well-known port, recommend not to use
> * FTP: 20, 21
> * TELNET: 23
> * HTTP: 80
> * HTTPS: 443
> 
> DNS - Transfer domain name to IP address / Phonebook