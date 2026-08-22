# Windows PowerShell
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room follows Windows Command Line and covers PowerShell, a much more powerful shell than `cmd.exe`. PowerShell is described as a cross platform task automation solution, combining a command line shell, a scripting language, and a configuration management framework all in one.

The core difference from `cmd.exe` is right at the foundation: PowerShell is object oriented. Instead of every command output being plain text, cmdlets return .NET objects with actual properties and methods attached to them, which changes how you work with the data that comes back from a command.

Cmdlets follow a consistent Verb-Noun naming pattern (like `Get-Content` or `Set-Location`), which makes commands far more predictable and discoverable than the more arbitrary naming in `cmd.exe`. The room covers a wide set of cmdlets grouped by purpose: file system navigation and management (`Get-ChildItem`, `Set-Location`, `New-Item`, `Remove-Item`, `Get-Content`), command discovery (`Get-Command`, `Get-Help`, `Get-Alias`), and data manipulation (`Where-Object`, `Sort-Object`, `Select-Object`).

It also goes into system information cmdlets, `Get-ComputerInfo`, `Get-NetIPConfiguration`, `Get-LocalUser`, `Get-Process`, `Get-Service`, `Get-NetTCPConnection`, and `Get-FileHash`, which cover a lot of the same ground as the Windows Command Line room, but with richer, structured output. It closes with piping objects between cmdlets, comparison operators (`-eq`, `-ne`, `-gt`, `-ge`, `-lt`, `-le`), and a first look at scripting and remote execution with `Invoke-Command`.

## Key Concepts / Commands Learned
- PowerShell: object oriented shell and scripting language, not just a text based CLI
- Verb-Noun cmdlet naming convention (e.g. `Get-Content`, `Set-Location`)
- `Get-ChildItem`, `Set-Location`, `New-Item`, `Remove-Item`, `Get-Content`: filesystem navigation and management
- `Get-Command`, `Get-Help`, `Get-Alias`: discovering and learning cmdlets
- `Where-Object`, `Sort-Object`, `Select-Object`: filtering and shaping object output
- `Get-ComputerInfo`, `Get-NetIPConfiguration`, `Get-LocalUser`, `Get-Process`, `Get-Service`, `Get-NetTCPConnection`, `Get-FileHash`: system and network information
- Piping objects between cmdlets (not just text, like in `cmd.exe`)
- Comparison operators: `-eq`, `-ne`, `-gt`, `-ge`, `-lt`, `-le`
- `Invoke-Command`: run commands or scripts against remote computers

## Notes
Coming right after the Windows Command Line room made the contrast obvious fast. `cmd.exe` outputs raw text you'd have to parse yourself, while PowerShell hands back structured objects you can filter, sort, and select fields from directly, closer to working with a small database than a flat terminal.

Spent time getting used to the Verb-Noun pattern, and once it clicked, guessing a cmdlet name (like `Get-Process` for something process related) started working more often than not, which says a lot about how consistent the naming is compared to `cmd.exe` or even some Linux tools.

Practiced piping between cmdlets combined with `Where-Object` and `Sort-Object`, filtering something like a process list down to just what matters, which felt like a small taste of what makes PowerShell popular for both administration and, from what I understand, offensive tooling later on.

Got a first look at `Invoke-Command` for running things remotely, and at comparison operators, which look odd at first coming from `==`/`>`/`<` in other languages, but make sense once you know PowerShell reserves `<` and `>` for redirection.

## Takeaways
- The object oriented nature of PowerShell is the single biggest thing to internalize early, everything else (piping, filtering, sorting) builds on that idea.
- The Verb-Noun convention makes cmdlets genuinely guessable, worth leaning on `Get-Command` and `Get-Help` instead of memorizing everything upfront.
- A lot of the system information cmdlets here overlap conceptually with what I already covered in Windows Command Line, useful to compare both approaches side by side.
- `Invoke-Command` is worth flagging for later, since remote execution in PowerShell is something that comes up constantly in both blue team and red team contexts down the line.
