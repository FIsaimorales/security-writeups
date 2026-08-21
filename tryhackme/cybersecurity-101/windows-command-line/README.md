# Windows Command Line
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room moves away from the Windows GUI entirely and into `cmd.exe`, the default Windows command line interpreter, covering why a CLI matters in the first place: faster execution, fewer resources used, and much easier to automate than clicking through menus.

It starts with basic system information commands, things like `ver` (OS version), `systeminfo` (a full breakdown of system specs), and `driverquery` for listing installed drivers, along with `help` and `cls` for documentation and clearing the screen.

A big section covers network troubleshooting, split into three areas: configuration (`ipconfig` and `ipconfig /all`, which shows details like DNS and DHCP status), basic troubleshooting (`ping` for connectivity and `tracert` for tracing the route to a target), and more advanced networking (`nslookup` for resolving domains to IPs, and `netstat -abon` for checking active connections and ports).

The room then covers file and disk management, split across directory operations (`cd`, `dir`, `mkdir`, `rmdir`, `tree`), file operations (`type`, `more`, `copy`, `move`, `del`/`erase`), and process management (`tasklist`, filtered queries, and `taskkill`).

It closes with system control commands: `shutdown /s` (shutdown), `shutdown /r` (restart), and `shutdown /a` (abort a scheduled shutdown or restart).

## Key Concepts / Commands Learned
- `cmd.exe`: the default Windows command line interpreter
- `ver`: display the OS version
- `systeminfo`: full system specification overview
- `driverquery`: list installed drivers
- `help` / `cls`: command documentation and clearing the screen
- `ipconfig` / `ipconfig /all`: network configuration details, including DNS and DHCP
- `ping`: test connectivity to a target
- `tracert`: trace the network route to a target
- `nslookup`: resolve a domain name to an IP address
- `netstat -abon`: view active connections and listening ports
- `cd`, `dir`, `mkdir`, `rmdir`, `tree`: directory navigation and management
- `type`, `more`, `copy`, `move`, `del` / `erase`: file operations
- `tasklist` / `taskkill`: list and terminate running processes
- `shutdown /s`, `/r`, `/a`: shut down, restart, or abort a scheduled shutdown/restart

## Notes
Went through this room right after the three Windows Fundamentals rooms, and it felt like the natural next step: everything covered there through the GUI (processes, system info, networking) has a direct command line equivalent here.

Spent time comparing these commands to their Linux counterparts from the earlier Linux Fundamentals rooms, since a lot of them map closely: `ipconfig` to `ip a`, `tasklist`/`taskkill` to `ps`/`kill`, `dir` to `ls`. Having that mental mapping made picking up the Windows syntax faster than learning it from zero.

Practiced the networking commands specifically, since `ping`, `tracert`, `nslookup`, and `netstat` all felt directly relevant to basic troubleshooting and reconnaissance, not just theory.

Also noted that `cmd.exe` is more limited than PowerShell (which appears to be a separate room), but it's still the baseline that shows up everywhere, including in a lot of older systems and scripts.

## Takeaways
- `cmd.exe` commands map closely enough to Linux equivalents that leaning on that comparison speeds up learning a lot.
- The networking commands (`ipconfig`, `ping`, `tracert`, `nslookup`, `netstat`) are the ones I'll use most often day to day, worth having memorized rather than looked up each time.
- `tasklist` and `taskkill` are the Windows equivalent of `ps` and `kill`, and knowing both sides (Linux and Windows) covers most systems I'll run into.
- This room is a good reminder that GUI knowledge and CLI knowledge are two separate skills that need practicing separately, even when they control the exact same underlying system.
