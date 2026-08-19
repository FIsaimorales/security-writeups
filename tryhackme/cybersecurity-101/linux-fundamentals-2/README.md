# Linux Fundamentals 2

**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview

The room covers connecting to a remote Linux machine via SSH (Secure Shell), which is the standard way to access and control systems securely over a network.
From there, it moves into command flags and switches — understanding how arguments change a command's behavior, and using man pages to look up what those options do.
The bulk of the room is filesystem operations: creating empty files with touch, creating directories with mkdir, copying files and folders with cp, moving or renaming them with mv, and removing files and directories with rm (including rm -R for recursive deletion).
It also introduces file, which identifies what type of file you're looking at regardless of its extension.

Another key topic is file permissions — reading the owner/group/other structure and the read/write/execute notation shown by ls -lh, which is foundational for understanding access control on Linux systems.
The room also touches on important system directories like /etc, /var, /root, and /tmp, and how to switch between user accounts using su.

## Key Concepts / Commands Learned

- `ssh` — connect securely to a remote machine over an encrypted channel
- Command flags/switches — arguments that modify a command's behavior (learned via `man` pages)
- `man` — access built-in documentation for any command
- `touch` — create empty/blank files
- `mkdir` — create new directories
- `cp` — copy files or folders
- `mv` — move or rename files and folders
- `rm` / `rm -R` — remove files (and directories, recursively)
- `file` — identify a file's actual type, regardless of extension
- `ls -lh` — list files with permissions in human-readable format
- File permissions — owner/group/other structure with read/write/execute notation
- `su` — switch between user accounts
- Key system directories: `/etc`, `/var`, `/root`, `/tmp`

## Notes

Practiced connecting to a remote machine via SSH using provided credentials.

Spent time interpreting the output of `ls -lh`, breaking down the
permission string (`-rwxr-xr--`) into owner, group, and other
permissions, and understanding how read/write/execute apply differently to
files vs. directories. Also practiced using `man` to look up flags for
commands instead of memorizing them, which seems like a more sustainable
habit going forward.

Explored key system directories (`/etc`, `/var`, `/root`, `/tmp`) to get a
sense of what lives where on a typical Linux filesystem, and practiced
switching users with `su` to understand how access control plays out in
practice.

## Takeaways

- SSH is the baseline for interacting with almost any remote Linux system
  in a security context.
- Reading permissions correctly (owner/group/other + rwx).
- `man` is more useful than trying to memorize every flag — better to build
  the habit of checking it than to guess.
- Knowing key directories (`/etc`, `/var`, `/tmp`, `/root`) in advance
  makes navigating unfamiliar machines much faster.
