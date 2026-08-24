# Networking Secure Protocols
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room is the fourth and final part of the networking series, and it directly answers a question that comes up naturally after Networking Core Protocols: most of those protocols (HTTP, FTP, SMTP, POP3, IMAP) send data in plaintext, so how does any of this get secured in practice?

It starts with TLS (Transport Layer Security), the cryptographic protocol that provides confidentiality and integrity for network communication. It covers TLS certificates, Certificate Authorities (the entities that vouch for a certificate's legitimacy), and the evolution from the older SSL to modern TLS 1.3.

From there it shows HTTPS as a concrete example, HTTP with TLS layered on top, contrasting plaintext HTTP on port 80 with encrypted HTTPS on port 443, and walking through the extra TLS handshake steps that happen before any actual data gets exchanged.

The room then revisits the email protocols from Networking Core Protocols and shows their secure counterparts: SMTPS (port 465 or 587), POP3S (port 995), and IMAPS (port 993), all of which protect login credentials and message content that would otherwise travel in the clear.

It also covers SSH (Secure Shell) on port 22, which replaces the older, insecure Telnet (port 23), supporting password based login as well as public key and two factor authentication, plus X11 forwarding for remote graphical applications. Closely related is file transfer: SFTP (file transfer over SSH, port 22) and FTPS (FTP secured with TLS, port 990).

It closes with VPNs (Virtual Private Networks), which create an encrypted tunnel for remote network access, hiding the user's real IP address and protecting traffic from inspection by an ISP or anyone else on the network path, the exact mechanism behind the TryHackMe VPN connection used to reach target machines.

## Key Concepts / Commands Learned
- TLS: cryptographic protocol providing confidentiality and integrity for network traffic
- TLS certificates and Certificate Authorities
- SSL to TLS 1.3: evolution of the protocol
- HTTPS: HTTP secured with TLS, TCP port 443, vs. plaintext HTTP on port 80
- TLS handshake: extra steps before data is exchanged over HTTPS
- SMTPS (port 465/587), POP3S (port 995), IMAPS (port 993): secure versions of the core email protocols
- SSH: secure remote access, TCP port 22, replaces Telnet (port 23)
- SSH authentication: password, public key, two factor
- X11 forwarding: remote graphical applications over SSH
- SFTP: file transfer over SSH, port 22
- FTPS: FTP secured with TLS, port 990
- VPN: encrypted tunnel for remote network access, hides IP, protects traffic from inspection

## Room Lab
The practical part of this room used Wireshark to look at a capture of encrypted HTTPS traffic. On its own, TLS traffic just shows up as encrypted noise, so the first step was loading a TLS key into Wireshark (under Preferences, Protocols, TLS, pointing it to the (Pre)-Master-Secret log filename) so it could decrypt the traffic and show the actual HTTP requests underneath, instead of just encrypted packets.

Once the traffic was readable, the next step was filtering down to find a specific HTTP POST request related to a login action, since POST requests are how form data (like a username and password) typically gets sent to a server, as opposed to GET requests, which just retrieve data.

After finding the right POST request in the packet list, the flag was inside the packet details at the bottom of Wireshark, expanding the HTTP layer of that packet to see the actual form data submitted in the request body, which is where the login credentials (and the flag) were visible in plaintext, now that the TLS decryption key made that possible.

<img width="1275" height="732" alt="image" src="https://github.com/user-attachments/assets/a850e38a-b45f-471a-a2d5-88139c600a9c" />

## Notes
This room felt like it closed the loop that Networking Core Protocols opened, every plaintext protocol covered there (HTTP, FTP, SMTP, POP3, IMAP) got its secure counterpart explained here, which made the whole four part networking series feel like it actually finished somewhere instead of just accumulating more protocol names.

Spent time on the TLS handshake specifically, since it's the mechanism behind almost everything secure online, and connecting it to HTTPS made the padlock icon in a browser mean something concrete instead of just "this is safe" at a glance.

SSH was the most directly useful part of this room for me personally, since I already used it to connect to TryHackMe target machines in earlier rooms without fully understanding what was happening underneath, seeing it formally explained (replacing Telnet, supporting key based auth) connected practice to theory.

The VPN section was the best payoff of the whole room, since it's literally explaining the exact technology I used to connect through WSL earlier, the encrypted tunnel, hiding my real traffic, all matched up with what I'd already set up and used hands on.

## Takeaways
- Every plaintext protocol from Core Protocols has a secure version worth pairing mentally: HTTP with HTTPS, FTP with SFTP/FTPS, SMTP/POP3/IMAP with their S versions.
- The TLS handshake is worth understanding at a conceptual level, it explains why establishing a secure connection takes a few extra steps compared to plaintext.
- SSH is something I'd already used without fully understanding, this room was a good reminder to go back and connect hands on experience to the theory behind it.
- Finishing this room means the whole networking series (Concepts, Essentials, Core Protocols, Secure Protocols) is done, next stop is the hands on tools (Wireshark, TCPDump, Nmap) before Offensive Security Intro.
