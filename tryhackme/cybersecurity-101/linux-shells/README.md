# Linux Shells
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room steps back from individual commands and looks at the shell itself, the program that sits between you and the operating system, interpreting everything you type and passing it along to the kernel. Bash is the default shell on most Linux distributions, but the room also mentions alternatives like Fish (which has built in syntax highlighting) and Zsh (highly customizable, though slower).

It reviews a handful of essential commands as a refresher, `pwd`, `cd`, `ls`, `grep`, and `cat`, before moving into the real focus of the room: shell scripting. This is where things shift from running commands one at a time to writing them as a reusable script.

The room covers the anatomy of a script: the shebang line (`#!/bin/bash`), which tells the system which interpreter to use, and `chmod +x`, which makes a script file executable in the first place. From there it covers the core building blocks of any script: variables (to store and reuse values), loops (to repeat an action across a range or a list of items), conditional statements (to run code only when a certain condition is true), and comments (to document what the script is doing and why).

To tie it together, the room walks through a practical example, a locker style authentication script that checks a username, a company name, and a PIN before granting access, and closes with an exercise that searches through log files for a specific keyword using a shell script, a task that maps directly onto real security and automation work.

## Key Concepts / Commands Learned
- Shell: the program that interprets commands and passes them to the OS (Bash, Fish, Zsh)
- `pwd`, `cd`, `ls`, `grep`, `cat`: core commands for navigating and reading files
- Shebang (`#!/bin/bash`): defines which interpreter runs the script
- `chmod +x`: makes a script file executable
- Variables: store and reuse values throughout a script
- Loops (`for`, `while`): repeat an action across a range or list of items
- Conditional statements (`if`/`then`/`else`): run code based on a condition
- Comments (`#`): document what a script does without affecting execution
- Practical scripting: building an authentication style check (username, company, PIN)
- Practical scripting: searching log files for a keyword through a script

## Notes
Went into this room already having written a small script of my own (the flag search script I debugged separately), so a lot of the concepts, shebang, variables, loops, conditionals, were already familiar in practice, and this room helped fill in the theory behind why each piece works the way it does.

The distinction between running commands interactively versus writing them into a script was a useful reframe, a script is really just a sequence of the same commands I already know, wrapped with structure (variables, loops, conditionals) so it can run unattended and repeatably.

Spent time on the loop and conditional syntax specifically, since that's the part that trips people up coming from other languages, Bash's `if [ condition ]; then ... fi` and `for var in list; do ... done` structure takes a bit of getting used to compared to more modern languages.

The log searching exercise at the end felt directly relevant, since it's basically a smaller version of the kind of script a SOC analyst or sysadmin would actually use to search through log files for a specific indicator.

## Takeaways
- A script is just commands I already know, organized with variables, loops, and conditionals so they can run automatically instead of one at a time.
- Getting `for` loops right in Bash means being careful about what you're actually iterating over, a lesson I learned firsthand debugging my own script that looped over a directory name instead of the files inside it.
- Comments matter more in scripts meant to be revisited later or shared, worth building the habit now instead of skipping them.
- Log searching scripts like the one in this room are a realistic preview of the kind of small automation tooling that comes up constantly in blue team and SOC work.
