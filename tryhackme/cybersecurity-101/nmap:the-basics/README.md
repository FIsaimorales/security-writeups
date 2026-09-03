# Nmap: The Basics
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room closes out the networking tool trio (Wireshark, Tcpdump, Nmap) and moves from passively observing traffic to actively probing a target. Nmap is the standard tool for network scanning, and this room assumes the TCP/IP and protocol knowledge from the earlier networking rooms is already solid, since scanning is really just applying that knowledge against a real target.

It starts with host discovery, figuring out what devices are actually alive on a network before scanning anything in detail, and how to specify a target: a single IP, an IP range, a subnet in CIDR notation, or a hostname.

The bulk of the room covers port scanning techniques. The TCP Connect scan (`-sT`) completes the full three way handshake with each port, the most straightforward but also the most detectable method. The SYN scan (`-sS`), often called a stealth scan, only sends the initial SYN and never completes the handshake, making it faster and quieter. UDP scanning (`-sU`) covers connectionless protocols, which need a different approach since there's no handshake to probe in the first place.

From there it moves into service and version detection: OS detection (`-O`), which fingerprints the target's operating system based on how it responds to certain probes, service version detection (`-sV`), which tries to identify exactly what software and version is running behind an open port, and aggressive scanning (`-A`), which bundles several of these detection methods together in one command. It also covers `-Pn`, which forces a scan to run even against a target that appears offline to a basic ping check, useful since some hosts are configured to not respond to pings at all.

The room also covers output and reporting: saving results in normal format (`-oN`), XML (`-oX`), a grepable format (`-oG`), or all three at once (`-oA`), plus verbosity flags (`-v`, `-vv`) and a debug mode (`-d`) for troubleshooting a scan itself. It closes with scan optimization: fast mode (`-F`, which only checks the 100 most common ports), specifying custom port ranges (`-p`), and the timing templates (`T0` through `T5`), which trade off speed against stealth, plus other options for controlling parallelism and scan rate.

## Key Concepts / Commands Learned
- Nmap: standard tool for active network and port scanning
- Host discovery: identifying live devices before scanning in detail
- Target specification: single IP, IP range, CIDR subnet, or hostname
- `-sT`: TCP Connect scan, completes the full three way handshake
- `-sS`: SYN (stealth) scan, sends SYN only, never completes the handshake
- `-sU`: UDP scan, for connectionless protocols
- `-O`: OS detection/fingerprinting
- `-sV`: service version detection
- `-A`: aggressive scan, combines multiple detection methods
- `-Pn`: force a scan even if the host appears offline to ping
- `-oN` / `-oX` / `-oG` / `-oA`: output formats (normal, XML, grepable, all)
- `-v` / `-vv`: verbosity levels
- `-d`: debug mode
- `-F`: fast scan, top 100 common ports only
- `-p`: specify a custom port or port range
- `T0`-`T5`: timing templates, speed vs. stealth tradeoff

## Room Lab

Started with a basic scan against the target's IP with no flags to see Nmap's default behavior (a TCP Connect scan against the 1,000 most common ports), then rebuilt the same scan more deliberately using `-sS` for a faster SYN scan and comparing the results and the time it took.

Practiced adding `-sV` and `-O` to the same target to pull service versions and attempt OS fingerprinting, which connected directly back to the port to protocol mapping learned in Networking Core Protocols, seeing an open port 22 actually get labeled "OpenSSH" by version detection made that connection concrete instead of just theoretical.

Ran an `-A` aggressive scan to see everything bundled together in one command, then compared its output and runtime against the more targeted scans from earlier in the room, to get a feel for when a quick, narrow scan makes more sense than throwing everything at a target at once.

Also practiced saving scan results with `-oN` and `-oA` so they could be reopened and referenced later without needing to rerun the scan, which is a habit worth carrying into every future scan against a real target.

## Notes
This room felt like the payoff for the whole networking series, ports, protocols, and TCP/UDP were all things I'd read about and seen in Wireshark and Tcpdump, but scanning a live target and watching Nmap map out exactly what's running where made all of it click together into one skill.

The difference between `-sT` and `-sS` was worth sitting with, since it's a good first example of a tradeoff that comes up constantly in offensive work: complete correctness and simplicity versus speed and stealth.

Timing templates (`T0`-`T5`) were interesting conceptually even without a real reason to go slower than default in a lab environment, worth remembering that in a real engagement, scan speed can be a meaningful decision, not just a
