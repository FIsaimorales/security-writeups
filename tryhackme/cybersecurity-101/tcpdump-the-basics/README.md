# Tcpdump: The Basics
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room moves from Wireshark's graphical interface into `tcpdump`, its command line equivalent, built on the same `libpcap` library that Wireshark uses under the hood. Where Wireshark is about clicking through a GUI to inspect traffic, `tcpdump` is about capturing and filtering that same traffic directly from the terminal, which matters a lot on servers or systems where there's no graphical interface available at all.

It starts with basic packet capture: capturing live traffic on a specified network interface, saving a capture to a file for later analysis, reading back from a previously saved capture file, limiting how many packets get captured, and controlling how the output is displayed.

The bulk of the room covers filtering expressions, which is really the core skill `tcpdump` is built around: filtering by host (source or destination), filtering by port (in either direction), filtering by protocol (TCP, UDP, ICMP, and others), and combining all of these together with logical operators, AND, OR, and NOT, to build precise filters instead of drowning in irrelevant traffic.

From there it goes into more advanced filtering: filtering by packet length, doing binary operations directly on protocol header bytes, inspecting TCP flags specifically (SYN, ACK, FIN, RST, PUSH), and comparing header bytes in hexadecimal, which is a much lower level way of working with traffic than anything covered in Wireshark so far. It closes with display customization: showing output in ASCII or hex format, displaying MAC addresses, and controlling how verbose the output is.

## Key Concepts / Commands Learned
- `tcpdump`: command line packet capture tool built on `libpcap`
- `-i`: specify the network interface to capture on
- `-w`: write captured packets to a file
- `-r`: read packets from a previously saved capture file
- `-c`: limit the number of packets captured
- `-n` / `-nn`: disable DNS/protocol name resolution for faster, rawer output
- `-q`: quick, brief output
- `-e`: display MAC addresses
- `-A`: show packet contents in ASCII
- `-X`: show packet contents in hex and ASCII together
- `-xx`: show packet contents in hex only
- Filtering by host, port, and protocol (TCP, UDP, ICMP)
- Combining filters with `and`, `or`, `not`
- Filtering by packet length
- TCP flag filtering: SYN, ACK, FIN, RST, PUSH
- Hexadecimal comparisons on header bytes

## Room Lab
The room used a terminal on the deployed machine (no GUI needed this time, since `tcpdump` is entirely command line), which made this one noticeably faster and smoother to work through than Wireshark's room, no lag from a browser video stream, just a normal terminal session.

Practiced capturing live traffic on the machine's interface with `-i`, and piping that straight into a saved file with `-w` so it could be reopened and re-analyzed without needing to re-capture. Also practiced the reverse, reading back a provided capture file with `-r` instead of capturing live, which is closer to what a lot of real investigation work looks like (analyzing a capture someone else already took).

Spent time building filters incrementally, starting simple (`tcpdump -i eth0 host 10.10.10.1`), then adding a port (`and port 80`), then combining multiple conditions with `and`/`or`/`not` to narrow results down to exactly the traffic that mattered for a given question.

The TCP flag filtering was the most technical part of the room, using the binary/hex based syntax to isolate packets with a specific flag set (like SYN packets only, to spot the start of new TCP connections), which connected directly back to the three way handshake from Networking Concepts.

## Notes
Doing this right after Wireshark made the contrast really clear: Wireshark is better for visually digging through a capture and following a full conversation, while `tcpdump` is faster for capturing traffic in the first place, especially on a remote machine over SSH where there's no GUI available at all.

The filtering syntax took some getting used to, since it reads more like plain English (`host X and port Y`) than most command line tools, which made it easier to build up complex filters step by step instead of memorizing a rigid syntax.

The TCP flag and hex level filtering was the hardest part conceptually, understanding that you're comparing raw bytes in the header rather than a named field took rereading a couple of times, but tying it back to the three way handshake (SYN, SYN ACK, ACK) from the networking rooms made it click faster than it would have cold.

Being able to capture with `-w` and then reopen the same file in Wireshark afterward (using what I learned in the previous room) felt like the two tools clicking together as a workflow, not just two separate isolated skills.

## Takeaways
- `tcpdump` is the tool to reach for when there's no GUI available (a remote server over SSH, for example), Wireshark for deeper visual analysis once you have a capture file in hand.
- Building filters incrementally (host, then port, then protocol, then combining with `and`/`or`/`not`) is a much better habit than trying to write the perfect filter in one shot.
- `-w` to capture and `-r` to reopen, ideally in Wireshark, is a workflow worth remembering, since it combines tcpdump's speed with Wireshark's easier visual analysis.
- TCP flag filtering is worth practicing more, since recognizing SYN only traffic (or unusual flag combinations) is a skill that comes up constantly in both troubleshooting and security monitoring.
