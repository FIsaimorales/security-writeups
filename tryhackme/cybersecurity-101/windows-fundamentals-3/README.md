# Windows Fundamentals 3
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room wraps up the Windows Fundamentals series by moving into security specific features, after the previous two rooms covered the general interface, filesystem, and administrative tools.

It starts with Windows Updates, including "Patch Tuesday" (the second Tuesday of each month, when Microsoft releases most of its patches) and how update scheduling works. From there it covers the Windows Security dashboard, a color coded interface that gives an overview of the system's overall security posture across several categories.

Each category in that dashboard gets its own section: Virus and Threat Protection (Microsoft Defender, including quick, full, custom, and offline scan types), Firewall and Network Protection (the three network profiles: domain, private, and public, each with its own customizable rules), and App and Browser Control (SmartScreen, which uses reputation based checks and exploit prevention to block malicious files and sites before they run).

The room also introduces Device Security, covering Core Isolation, which uses Hyper V virtualization to protect core system processes, and memory integrity features that prevent malicious code from injecting into trusted processes. Related to that is the Trusted Platform Module (TPM), a dedicated security chip used for cryptographic operations and secure key storage.

From there it covers BitLocker, full disk encryption that typically relies on TPM (or a USB startup key on systems without TPM 1.2+), and closes with the Volume Shadow Copy Service (VSS), which coordinates backups and recovery points without needing to take applications offline while it works.

## Key Concepts / Commands Learned
- Windows Updates and Patch Tuesday (second Tuesday of each month)
- Windows Security dashboard: color coded overview of system security status
- Microsoft Defender: quick, full, custom, and offline scan types
- Firewall and Network Protection: domain, private, and public network profiles
- App and Browser Control: SmartScreen reputation based protection
- Core Isolation: Hyper V based protection for core system processes
- Memory integrity: prevents malicious code injection into trusted processes
- Trusted Platform Module (TPM): dedicated chip for cryptographic operations
- BitLocker: full disk encryption, tied to TPM or a USB startup key
- Volume Shadow Copy Service (VSS): backup and recovery coordination without taking apps offline

## Notes
Went through the Windows Security dashboard section by section, since it's the main place a regular user would actually check their system's protection status. Understanding what each color and category means made it clear this isn't just a GUI, it's tying together several underlying security mechanisms.

Spent extra time on Defender's scan types, since knowing when to use a quick scan versus a full or offline scan feels directly useful, not just theoretical. Also went through the three firewall network profiles and why Windows treats a public network (like a coffee shop) very differently from a private or domain one.

Learned about Core Isolation and memory integrity, and how they lean on Hyper V (virtualization) to protect the OS core from tampering, even if something malicious manages to run with elevated privileges. Connected this with TPM, which handles the cryptographic side of things like BitLocker.

Covered BitLocker's dependency on TPM, and what happens on older hardware without it (a USB startup key instead). Closed out with Volume Shadow Copy Service, which explained something I'd seen before (like Windows "previous versions" of a file) without understanding what was actually happening behind it.

## Takeaways
- The Windows Security dashboard is a good first stop when
