# Networking Core Protocols
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room is the third in the networking series, following Networking Concepts and Networking Essentials, and assumes that foundation is already solid, the OSI and TCP/IP models, Ethernet, IP, and TCP. Where the previous rooms explained how devices find and reach each other, this one covers the application layer protocols that actually carry meaningful data once a connection exists.

It starts with DNS (Domain Name System), which maps human readable domain names to IP addresses, operating over UDP port 53. It covers the main record types: A (IPv4 addresses), AAAA (IPv6 addresses), CNAME (aliases), and MX (mail routing). Related to DNS is WHOIS, a protocol used to look up domain registration details, who owns a domain, when it was created, and when it expires.

The room then covers HTTP and HTTPS, the protocols behind basically all web browsing, running on TCP ports 80 and 443 respectively, along with the common HTTP methods: GET, POST, PUT, and DELETE. From there it moves into FTP (File Transfer Protocol), used specifically for transferring files over TCP port 21, with commands like USER, PASS, RETR (download), and STOR (upload).

The room closes with email protocols. SMTP (Simple Mail Transfer Protocol), used for sending mail over TCP port 25, with commands like HELO/EHLO, MAIL FROM, RCPT TO, and DATA. POP3 (Post Office Protocol), used for retrieving mail over TCP port 110, with USER authentication, LIST, RETR, and DELE. And IMAP (Internet Message Access Protocol), a more modern mail retrieval protocol over TCP port 143, which keeps mail synchronized on the server across multiple devices instead of just downloading and deleting it.

## Key Concepts / Commands Learned
- DNS: maps domain names to IP addresses, UDP port 53
- DNS record types: A, AAAA, CNAME, MX
- WHOIS: looks up domain registration and ownership details
- HTTP / HTTPS: web protocols, TCP ports 80 and 443
- HTTP methods: GET, POST, PUT, DELETE
- FTP: file transfer protocol, TCP port 21
- FTP commands: USER, PASS, RETR, STOR
- SMTP: mail sending protocol, TCP port 25
- SMTP commands: HELO/EHLO, MAIL FROM, RCPT TO, DATA
- POP3: mail retrieval protocol, TCP port 110
- POP3 commands: USER, LIST, RETR, DELE
- IMAP: mail retrieval and sync protocol, TCP port 143

## Notes
This room felt like the point where networking stopped being abstract and started overlapping directly with things I already interact with daily, browsing (HTTP/HTTPS), downloading files (FTP), and email (SMTP/POP3/IMAP), just now with a name and a port number attached to each one.

Spent time memorizing the port numbers alongside each protocol, since that pairing (DNS to 53, HTTP to 80, FTP to 21, SMTP to 25, and so on) is going to matter a lot once tools like Nmap start showing open ports and I need to recognize what service is likely running behind each one.

The difference between POP3 and IMAP stood out as a good example of a design tradeoff, POP3 is simpler (download and often delete), IMAP is more complex but keeps everything synced across devices, which explains why most modern email clients default to IMAP.

Practicing the raw commands for FTP, SMTP, and POP3 (rather than just using a GUI client) connected back to the Telnet exercise from Networking Concepts, manually typing protocol commands makes it obvious that a lot of "magic" client software is just automating a fairly simple conversation.

## Takeaways
- Knowing protocol to port number pairings cold (DNS 53, HTTP 80, HTTPS 443, FTP 21, SMTP 25, POP3 110, IMAP 143) is going to pay off immediately once scanning tools like Nmap enter the picture.
- DNS record types (A, AAAA, CNAME, MX) come up constantly, worth having these memorized rather than looked up each time.
- Manually issuing protocol commands (FTP, SMTP) instead of relying on a client is a good habit to keep, it builds a much more concrete understanding than reading about the protocol alone.
- This room is the first one that felt directly tied to the next step, Offensive Security Intro, since a lot of basic web attacks start with understanding exactly what HTTP is doing under the hood.
