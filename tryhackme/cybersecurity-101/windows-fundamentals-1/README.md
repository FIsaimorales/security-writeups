# Windows Fundamentals 1
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room shifts focus away from Linux and into Windows, which is still the most widely used operating system worldwide, largely due to its graphical interface and accessibility for non-technical users.

It starts with a look at Windows editions, the evolution of the OS over the years, and specifically the difference between Home and Pro versions, including features like BitLocker (full-disk encryption) that are exclusive to Pro.

From there it covers the desktop environment itself: the Start Menu, Search Box, Task View, Taskbar, and Notification Area, along with basic customization options, the kind of GUI navigation that's second nature to most users but worth understanding deliberately from a systems perspective.

A key technical section covers the filesystem, tracing the shift from the older FAT filesystem to NTFS, and NTFS's more advanced features like journaling, file compression, permission management, and Alternate Data Streams (ADS), the last of which is particularly relevant in a security context, since ADS can be used to hide data.

The room also digs into the `C:\Windows\System32` folder, where critical OS files live, and introduces the `%windir%` environment variable as a way to reference the system directory. It then moves into user accounts, profiles, and permissions, the difference between Administrator and Standard user accounts, and how to manage them through `lusrmgr.msc` (Local Users and Groups).

Closely related is User Account Control (UAC), which functions similarly to `sudo` on Linux, a permission-elevation gate rather than a full admin login. The room wraps up with Settings and Control Panel (the two main interfaces for configuring the system) and Task Manager, used for monitoring and managing running processes, accessible via `Ctrl+Shift+Esc`.

## Key Concepts / Commands Learned
- Windows editions: Home vs. Pro, and Pro-exclusive features like BitLocker
- Desktop environment: Start Menu, Search Box, Task View, Taskbar, Notification Area
- NTFS: modern Windows filesystem; journaling, compression, permissions
- Alternate Data Streams (ADS): a lesser-known NTFS feature that can hide data
- `C:\Windows\System32`: core folder holding critical OS files
- `%windir%`: environment variable pointing to the Windows system directory
- Administrator vs. Standard user accounts
- `lusrmgr.msc`: Local Users and Groups management console
- User Account Control (UAC): Windows' privilege-elevation mechanism (conceptually similar to `sudo`)
- Control Panel and Settings: the two main system configuration interfaces
- Task Manager (`Ctrl+Shift+Esc`): process monitoring and management

## Notes
Went through the Windows GUI more deliberately than usual: things like the Taskbar or Start Menu are easy to take for granted, but mapping them out explicitly helped connect them to what's actually happening at the OS level underneath.

Spent time understanding NTFS vs. the older FAT filesystem, especially permissions and Alternate Data Streams: ADS stood out since it's a feature that can be used to hide files/data behind a legitimate file, which has obvious relevance for later, more security-focused rooms.

Practiced navigating to `C:\Windows\System32` and using `%windir%`, which felt like the Windows equivalent of exploring `/etc`, `/var`, etc. on Linux: same idea of knowing where the important system files live, different syntax.

Worked through the difference between Administrator and Standard accounts, and how UAC acts as a middle ground: not a full permission switch like logging in as a different user, but a per-action elevation prompt. Drawing the comparison to `sudo` on Linux made the concept click faster.

## Takeaways
- A lot of Windows concepts have a direct Linux equivalent (UAC ↔ `sudo`, System32 ↔ `/etc`), which makes cross-referencing what I already learned in the Linux Fundamentals rooms a good way to retain this faster.
- NTFS permissions and Alternate Data Streams are worth remembering specifically, ADS in particular seems like something that'll come back around in more offensive-focused content later.
- Knowing the difference between Administrator and Standard accounts (and how UAC mediates between them) is foundational for understanding privilege escalation on Windows down the line.
- Even "basic" GUI knowledge (Control Panel vs. Settings, Task Manager) matters in a security context, a lot of initial triage on a Windows machine happens through these same interfaces.
