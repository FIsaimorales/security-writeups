# Wireshark: The Basics
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room is the first hands on tool room after finishing the four part networking series, and it makes sense as the next step, since everything about protocols, ports, and TCP/UDP covered in those rooms is exactly what shows up in a packet capture. Wireshark is described as an open source, cross platform network packet analyzer, used for sniffing and investigating network traffic in detail.

It starts with a tool overview: the main use cases (network troubleshooting, spotting security anomalies, and digging into protocol details), the layout of Wireshark's interface (five main sections used for investigating packets), how to load a pcap file (several different ways to open a capture), packet coloring rules (temporary and permanent, used to visually flag patterns like errors or specific protocols), the controls for capturing live traffic, and basic file operations like merging multiple pcap files together and checking a file's properties.

The room then moves into packet dissection, breaking down a single packet layer by layer, matching directly onto the OSI model from Networking Concepts: frame and physical layer info, MAC addressing at the Data Link layer, IP addressing at the Network layer, TCP or UDP details at the Transport layer, and finally the application layer protocol itself (HTTP, FTP, SMB), down to the actual payload data being carried.

From there it covers packet navigation: identifying packets by number, jumping straight to a specific one with "Go to Packet," searching for packets by content, marking or commenting on packets to flag them for later, exporting specific packets or objects found inside them, customizing the time format shown, and using Expert Info, a feature that flags likely anomalies automatically.

The room closes with packet filtering: applying display filters to isolate specific values, filtering by conversation to see only packets between two specific hosts, colorizing a conversation without filtering it out entirely, building a filter before applying it, adding custom columns to the packet list for easier analysis, and following TCP, UDP, or HTTP streams to reconstruct an entire exchange (like a full file download or a login request) instead of reading it packet by packet.

## Key Concepts / Commands Learned
- Wireshark: open source, cross platform network packet analyzer
- Loading and merging pcap files
- Packet coloring rules: temporary and permanent, used to flag patterns visually
- Packet dissection: frame, MAC (Data Link), IP (Network), TCP/UDP (Transport), application layer (HTTP, FTP, SMB), payload
- Packet navigation: "Go to Packet," search by content, marking/commenting, exporting packets and objects
- Expert Info: automatic anomaly flagging
- Display filters: isolate packets by specific values
- Conversation filtering and colorizing
- Custom columns in the packet list
- Following TCP/UDP/HTTP streams: reconstructing a full exchange instead of packet by packet

## Room Lab
The practical part of this room used a Windows VM accessed through TryHackMe's browser split view, with Wireshark and two pcap files already loaded: `http1.pcapng`, used to follow along with the walkthrough steps, and `Exercise.pcapng`, used to answer the room's questions independently.

Worked through opening `http1.pcapng` and practicing the interface itself first: identifying the five main panel areas, applying a temporary color filter to highlight a specific type of packet, and checking the file's properties (capture duration, number of packets, and so on) before touching any actual analysis.

Moved into packet dissection on a single packet, expanding each layer in the packet details pane one at a time (Frame, Ethernet/MAC, IP, TCP, and finally HTTP) to see how the same piece of data gets described differently depending on which layer you're looking at, directly connecting back to the OSI model from Networking Concepts.

For the navigation and filtering tasks, practiced applying a display filter to isolate traffic from a single conversation, then right clicking a TCP stream and using "Follow > TCP Stream" to reconstruct an entire HTTP request and response as readable text, instead of piecing it together packet by packet. This ended up being the most useful single skill from the room, since it turns a wall of individual packets into something closer to just reading a webpage's raw request and response.

Finished by applying what I'd practiced on `http1.pcapng` to `Exercise.pcapng` to answer the room's actual questions, using filters and stream following to track down the specific values being asked for.

## Notes
Coming right after the networking series made a big difference, seeing an actual TCP three way handshake in the packet list, rather than just reading about SYN/SYN ACK/ACK, made the concept concrete in a way the reading alone hadn't.

The five panel layout took a bit to get comfortable with at first (packet list, packet details, bytes pane, filter bar, and the toolbar), but once I understood which pane to look at for what, moving between them got much faster.

Following a TCP or HTTP stream was the standout feature of the whole room. Being able to right click a packet and instantly see the full readable conversation, instead of manually reconstructing it from dozens of individual packets, made it obvious why Wireshark is considered essential rather than optional for this kind of work.

The browser based VM access itself was rough, noticeably laggy compared to a native app, which made even simple clicking and scrolling slower than it should be. Worth looking into a smoother way to access these GUI focused rooms going forward, since the friction was more about the delivery method than the tool itself.

## Takeaways
- Display filters and "Follow Stream" are the two features I'll reach for constantly going forward, worth practicing until they're second nature instead of looked up each time.
- Seeing packet dissection layer by layer made the OSI model finally feel concrete instead of theoretical, a good example of how a hands on tool room can cement material from an earlier, more abstract room.
- Expert Info is worth remembering as a first stop when looking at an unfamiliar capture, since it can point directly at anomalies instead of scrolling through everything manually.
- The GUI performance issue with the browser split view is a delivery problem, not a knowledge gap, worth solving separately (RDP client, better connection) so it doesn't slow down learning in future GUI heavy rooms like this one.
