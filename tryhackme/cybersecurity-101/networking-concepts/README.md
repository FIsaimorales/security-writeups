# Networking Concepts
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room shifts away from individual operating systems and into networking itself, the layer that connects everything covered so far (Linux, Windows) to everything else. It starts with the two big theoretical frameworks used to describe how networks function: the OSI model, a seven layer framework covering everything from physical transmission up to application level interaction, and the TCP/IP model, a simpler four layer model that maps roughly onto the OSI layers and is what actually describes how the internet works in practice.

From there it moves into IP addressing, covering IPv4 addresses as 32 bit numbers split into four octets, subnet masks (used to distinguish the network portion of an address from the host portion), and RFC 1918, which defines the three private IP ranges reserved for internal networks: `10.0.0.0` to `10.255.255.255`, `172.16.0.0` to `172.31.255.255`, and `192.168.0.0` to `192.168.255.255`.

A major section covers the transport layer protocols, TCP and UDP. TCP is reliable and connection oriented, establishing a connection through the three way handshake (SYN, SYN ACK, ACK) before any data is sent, while UDP is faster but connectionless, sending data without first confirming the other side is ready. Alongside this, the room covers port numbers, which range from 1 to 65,535 and identify which service on a machine a piece of traffic is meant for.

The room also explains data encapsulation, the process of wrapping data in protocol headers at each layer as it moves down the stack, turning application data into segments, then packets, then frames, before it actually goes out over the wire. To make all of this concrete, it uses Telnet to manually connect to a few basic TCP services (echo on port 7, daytime on port 13, and HTTP on port 80), which makes the abstract idea of "connecting to a port" into something hands on. It closes with the Linux commands used to check your own network configuration: `ifconfig`, `ip address show`, or the shorthand `ip a s`.

## Key Concepts / Commands Learned
- OSI model: seven layer framework describing network communication
- TCP/IP model: simplified four layer model used in practice on the internet
- IPv4 addressing: 32 bit addresses split into four octets
- Subnet masks: distinguish the network portion of an address from the host portion
- RFC 1918 private IP ranges: `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`
- TCP: reliable, connection oriented, three way handshake (SYN, SYN ACK, ACK)
- UDP: fast, connectionless, no handshake
- Ports: numbered 1 to 65,535, identify a specific service on a host
- Data encapsulation: data to segment to packet to frame as it moves down the stack
- `telnet`: manually connect to a TCP service/port (tested against echo, daytime, HTTP)
- `ifconfig` / `ip address show` / `ip a s`: check network configuration on Linux

## Notes
This room felt like the missing piece connecting everything from the earlier Linux and Windows rooms, since all of that (SSH, `ipconfig`/`ip a`, `netstat`) relies on networking concepts that hadn't been explained from the ground up yet.

Spent time really understanding the three way handshake, since it's one of those concepts that's easy to recite but harder to actually picture happening. Walking through SYN, SYN ACK, ACK step by step made TCP's reliability guarantee click in a way that just reading the term "connection oriented" hadn't.

Practiced using Telnet to connect directly to specific ports (7, 13, 80) on a target, which was the most hands on part of the room. Seeing raw HTTP responses come back after manually typing a request made the idea of "a port is just a door to a specific service" much more concrete than it sounds on paper.

Also spent time on the private IP ranges from RFC 1918, since recognizing a `192.168.x.x` or `10.x.x.x` address on sight (and knowing it's internal, not reachable from the public internet) feels like a basic skill that's going to come up constantly going forward.

## Takeaways
- Networking is the connective tissue behind everything covered so far, worth treating this room as a foundation rather than just another checkbox.
- The TCP three way handshake and UDP's lack of one is a distinction that explains a lot of why some protocols (DNS, video streaming) use UDP while others (HTTP, SSH) use TCP.
- Recognizing private IP ranges on sight (`10.x`, `172.16-31.x`, `192.168.x`) is a small thing that will save time reading network output later.
- Manually talking to a service with Telnet (rather than just using a browser or a purpose built client) is a good habit, it strips away abstraction and shows what's actually being sent over the wire.

## Images

[<img src="https://cdn-images.tryhackme.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/5f04259cf9bf5b57aed2c476-1719848845717.svg" />)
