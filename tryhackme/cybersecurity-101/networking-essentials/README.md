# Networking Essentials
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room builds directly on Networking Concepts, moving from the theoretical models (OSI, TCP/IP) into the protocols that actually keep a real network running day to day, assuming that foundation is already in place.

It starts with DHCP (Dynamic Host Configuration Protocol), which automates the process of handing a device its network settings, IP address, subnet mask, gateway, and DNS servers, instead of configuring each one manually. This happens through a four step process known by the acronym DORA: Discover, Offer, Request, Acknowledge.

From there it covers ARP (Address Resolution Protocol), which maps IP addresses to MAC addresses so devices on the same local network can actually find and talk to each other, through a simple request and reply exchange. Alongside that is ICMP (Internet Control Message Protocol), the protocol behind two of the most commonly used diagnostic tools: ping, for testing basic connectivity, and traceroute, which maps the path packets take to a destination by manipulating the TTL (Time to Live) value.

The room also introduces routing protocols, the mechanisms routers use to determine the best path for data to travel across a network, covering OSPF, EIGRP, BGP, and RIP by name, without necessarily going deep into configuring any of them at this stage. It closes with NAT (Network Address Translation), which explains how many devices on a private network can all share a single public IP address to reach the internet, something that connects directly back to the private IP ranges covered in Networking Concepts.

## Key Concepts / Commands Learned
- DHCP: automatic network configuration through the DORA process (Discover, Offer, Request, Acknowledge)
- ARP: maps IP addresses to MAC addresses on a local network
- ICMP: protocol behind network diagnostic tools
- `ping`: tests basic connectivity to a target
- Traceroute: maps the path to a destination using TTL manipulation
- Routing protocols: OSPF, EIGRP, BGP, RIP, mechanisms routers use to pick the best path
- NAT (Network Address Translation): lets multiple private devices share one public IP

## Notes
Went into this room right after Networking Concepts, and it felt like a natural continuation, the previous room explained the models and addressing scheme, this one explains the protocols that actually make a network self configuring and functional day to day.

Spent time on DHCP's DORA process specifically, since it explains something that happens automatically and invisibly every time a device joins a network, useful to finally understand step by step instead of just knowing "the router hands out IPs".

ARP was another concept that clicked better once broken down, understanding that IP addresses and MAC addresses are two different layers of addressing, and that something has to translate between them locally, filled a gap that the OSI model from the previous room only described abstractly.

The routing protocols section (OSPF, EIGRP, BGP, RIP) was more of a names and concepts overview than hands on practice, noted these to come back to in more depth later, since they seem like the kind of topic that gets much more detailed in network engineering or more advanced security paths.

NAT was the easiest to connect to prior knowledge, since it directly explains why every device on my home network has a private IP but they all appear as one public IP to the outside internet, tying back to the RFC 1918 ranges from Networking Concepts.

## Takeaways
- DHCP (DORA) and ARP are two protocols worth having memorized well, since they explain fundamental "how does a device even get on the network and start talking" behavior that shows up everywhere.
- Ping and traceroute are simple tools, but understanding what's happening underneath (ICMP, TTL) makes their output much more meaningful than just running them blindly.
- The routing protocols (OSPF, EIGRP, BGP, RIP) are noted for later, this room only scratched the surface and they'll likely need dedicated study outside of TryHackMe fundamentals.
- NAT closes the loop on private vs. public IP addressing that started in Networking Concepts, good to have both rooms fresh in mind together.
