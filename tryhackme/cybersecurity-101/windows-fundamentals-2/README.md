# Windows Fundamentals 2
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room builds directly on Windows Fundamentals 1, moving from the basic GUI and filesystem concepts into the deeper administrative tools that Windows provides for configuring and troubleshooting a system.

It starts with MSConfig (System Configuration), which acts as a launching point for a lot of what the room covers, spread across five tabs: General, Boot, Services, Startup, and Tools. From there, it revisits User Account Control (UAC), this time going into its four configurable privilege elevation levels, adjustable through a slider in the settings.

A big part of the room is Computer Management, a console that bundles together several important tools: Task Scheduler (for automating tasks), Event Viewer (for reviewing system logs), Shared Folders, Device Manager (for hardware configuration), and the Services console. Each of these gets covered individually as a piece of the bigger picture of "how do you administer a Windows machine."

The room also introduces System Information, which gives a full inventory of hardware resources, installed components, and the software environment (including environment variables), and Resource Monitor, which tracks live performance data across CPU, disk, network, and memory, down to the process level.

It closes with the Command Prompt, covering a handful of everyday commands (whoami, hostname, ipconfig, netstat) and a first look at the Registry Editor (regedt32.exe), which handles low level OS settings, the Windows equivalent of digging into system internals.

## Key Concepts / Commands Learned
- MSConfig (System Configuration): General, Boot, Services, Startup, and Tools tabs
- UAC privilege elevation levels: four configurable levels via a slider
- Computer Management console: bundles several admin tools together
- Task Scheduler: automate tasks to run on a schedule or trigger
- Event Viewer: review system, security, and application logs
- Device Manager: view and configure installed hardware
- Services console: manage background services (start, stop, disable)
- System Information: hardware, software environment, and environment variables overview
- Resource Monitor: live CPU, disk, network, and memory usage per process
- `whoami`: shows the currently logged in user
- `hostname`: shows the machine's hostname
- `ipconfig`: displays network configuration
- `netstat`: displays active network connections
- Registry Editor (`regedt32.exe`): low level OS configuration database

## Notes
Spent time going through MSConfig tab by tab, since it works as an entry point to a lot of the other tools covered later in the room. Understanding it first made the rest of the material easier to place in context.

Went deeper into UAC than in the previous room, this time looking at the actual privilege levels available through the slider rather than just the concept of elevation prompts. Helped connect back to what I learned about Administrator vs Standard accounts in Windows Fundamentals 1.

Worked through Computer Management piece by piece: Task Scheduler for automation, Event Viewer for logs (which feels directly relevant to blue team work), Device Manager for hardware, and Services for background processes. Also practiced a few basic Command Prompt commands (whoami, hostname, ipconfig, netstat) that map closely to Linux equivalents I already knew (whoami, hostname, ip a, netstat), which made them easy to pick up.

Got a first, surface level look at the Registry Editor. Didn't go deep into editing it yet, just enough to understand it exists and what kind of settings live there.

## Takeaways
- MSConfig is worth remembering as a starting point when exploring an unfamiliar Windows machine, since it links out to most of the other tools covered here.
- Event Viewer stood out as the most directly useful tool for a future blue team/SOC role, since log review is central to that kind of work.
- A lot of the Command Prompt commands have close Linux equivalents (whoami, hostname, netstat), which is a good pattern to keep leaning on going forward: map new OS concepts to what I already know from Linux Fundamentals instead of learning everything from scratch.
- The Registry Editor is something I'll need to revisit in more depth later, this room only scratched the surface.
