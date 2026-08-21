# Active Directory Basics
**Platform:** TryHackMe
**Path:** Cyber Security 101
**Difficulty:** Easy

## Overview
This room shifts from a single Windows machine to how Windows environments are managed at scale in a corporate setting, through Active Directory (AD), described as the backbone of identity and device management in most enterprise networks.

It starts with Windows Domains, covering centralized identity management through Domain Controllers, the servers that act as the central repository for credentials and security policy across every machine and user in the network.

From there it moves into Active Directory itself: machine accounts (computer names followed by a "$" to distinguish them from user accounts), Organizational Units (OUs, used to organize objects and apply policy), and the distinction between OUs and security groups, since both can be used to manage access but serve different purposes.

The room then covers managing users and computers within AD, including how OUs get deleted and how delegation works (granting a user specific privileges over a set of objects without making them a full Domain Administrator), plus how workstations and servers get organized into the right OU structure.

A key section covers Group Policy Objects (GPOs), collections of settings that get applied to users or computers, distributed across the network through a shared folder called SYSVOL. It also compares the two main authentication methods in AD environments: Kerberos (the default, ticket based protocol in modern Windows) and NetNTLM (the older, legacy protocol still present for compatibility).

The room closes with Trees, Forests, and Trusts, the hierarchical structures that let organizations manage multiple domains under one umbrella, and trust relationships that allow resources to be shared across domain boundaries.

## Key Concepts / Commands Learned
- Active Directory (AD): centralized identity and device management for enterprise networks
- Domain Controller: central server holding credentials and security policy
- Machine accounts: computer name followed by "$", distinct from user accounts
- Organizational Units (OUs): used to organize AD objects and apply policy
- Security groups vs. OUs: different mechanisms for managing access
- Delegation: granting limited privileges over specific OUs without full Domain Admin rights
- Group Policy Objects (GPOs): settings applied to users/computers, distributed via SYSVOL
- Kerberos: default, ticket based authentication protocol in modern Windows
- NetNTLM: legacy authentication protocol, still present for backward compatibility
- Trees, Forests, and Trusts: hierarchical multi domain structures and cross domain access

## Notes
Went from thinking about a single Windows machine to thinking about an entire network of them managed centrally, which felt like a natural next step after the three Windows Fundamentals rooms.

Spent time understanding the difference between OUs and security groups, since at first glance they can look like they do the same thing. OUs are more about organizing objects and applying policy, while security groups are specifically about controlling access to resources.

Learned about delegation as a middle ground between "regular user" and "Domain Administrator", which makes sense from a security perspective: giving someone exactly the access they need for their job, nothing more.

The comparison between Kerberos and NetNTLM stood out the most. Kerberos being ticket based (rather than sending credentials directly) is a meaningfully different security model, and understanding why NetNTLM still exists (legacy compatibility) helps explain why it keeps showing up as an attack surface in more advanced AD focused content.

## Takeaways
- AD is the natural next step after understanding a single Windows machine, since most real corporate environments are managed this way, not as isolated computers.
- Kerberos vs. NetNTLM is a distinction worth remembering well, since a lot of AD focused attacks (which I'll probably run into in more advanced rooms later) target weaknesses specifically in NetNTLM or in how Kerberos tickets are handled.
- Delegation is a good example of the principle of least privilege in practice, not just a term I'd heard before.
- GPOs and SYSVOL are worth remembering as the mechanism that pushes settings out across an entire domain, since that's a common thread that will probably come up again in later, more advanced rooms.
