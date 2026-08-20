# Linux Fundamentals 3
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
The room continues from Linux Fundamentals 2, moving into terminal text editors, mainly `nano`, for creating and editing files directly from the command line without leaving the terminal.

It then covers general utilities that come up constantly in a security context: `wget` for downloading files from the command line, and spinning up a quick web server with `python3 -m http.server` to transfer files between machines.

A big chunk of the room is dedicated to processes, using `ps` and `ps aux` to see what's running (your own processes vs. every user's), `top` for real-time monitoring, and `kill` with a process ID (PID) to stop something that's misbehaving. It also covers running commands in the background with `&` and bringing them back to the foreground with `fg`, plus a first look at `systemctl` for starting, stopping, and enabling system services.

The room also introduces automation through `cron`, using `crontab -e` to view and edit scheduled tasks, and understanding the cron syntax (minute/hour/day/month/weekday) as well as special strings like `@reboot`, which runs a job once at system startup instead of on a recurring schedule.

Package management is another key topic: how Ubuntu/Debian systems install and verify software with `apt`, and why external repositories need to be trusted first via GPG keys before software from them will install, the room walks through this conceptually using Sublime Text as an example (though it's not meant to actually succeed on the deployed instance, since TryHackMe machines don't have internet access).

Finally, the room closes with logs, navigating `/var/log`, and using `cat` to read through log files (like `access.log`) to pull out useful information such as IP addresses and requested resources, which is a core skill for basic incident investigation.

## Key Concepts / Commands Learned
- `nano` — terminal-based text editor for creating/editing files
- `wget` — download files directly from the command line
- `python3 -m http.server` — quickly spin up a local web server to serve/transfer files
- `ps` / `ps aux` — view running processes (own vs. all users)
- `top` — real-time process/resource monitoring
- `kill <PID>` — terminate a process by its process ID
- `&` — run a command in the background
- `fg` — bring a backgrounded process back to the foreground
- `systemctl` — manage system services (start, stop, enable)
- `crontab -e` / `crontab -l` — edit or list scheduled cron jobs
- Cron syntax — minute/hour/day/month/weekday fields, plus special strings like `@reboot`
- `apt` / GPG keys — installing packages and trusting external repositories
- `/var/log` — key system directory for log files
- `cat` — reading log file contents (e.g. `access.log`) to extract info

## Notes
Practiced editing files directly in the terminal with `nano` instead of relying on a GUI editor, useful since most remote/server environments won't have one available.

Worked through process management: listing processes with `ps aux`, identifying a specific one by name or PID, and killing it. Also practiced backgrounding a long-running command with `&` and bringing it back with `fg`, which clarified how the shell handles job control.

Spent time on cron syntax, breaking down a real crontab entry field by field (minute, hour, day of month, month, day of week) to figure out exactly when a job runs, and learning that `@reboot` is a special case that isn't tied to a specific time at all, just to system startup. Also ran into a good reminder that on these lab machines, the low-privilege user often can't view or run `sudo`, so scheduled jobs belonging to other users need a different approach to inspect.

Went through the package management example conceptually, downloading a GPG key and adding a custom `apt` repository, understanding *why* this matters (verifying software integrity) even without being able to complete it live on an internet-less lab machine.

Finished by digging through `/var/log` files with `cat` to pull out specific details like IP addresses from access logs, which felt like a small preview of log analysis in a real investigation.

## Takeaways
- Process management (`ps`, `top`, `kill`, `&`/`fg`) is something I'll use in almost every lab from here on worth getting fast at.
- Cron syntax is easy to misread at a glance; better to break it down field by field than guess.
- Not every user on a box has `sudo`, when something isn't in "your" crontab or files, it might belong to another user entirely.
- GPG keys exist to verify that downloaded software actually came from who it claims to, a concept that'll matter a lot more once I get into more offensive-focused rooms.
- Logs in `/var/log` are a goldmine of information even with basic tools like `cat,no fancy tooling needed to start pulling out useful details.
