---
description: >-
  A multi-site Active Directory and Windows Server environment built from
  scratch in a home lab: domain controllers per site, DHCP, DNS, OU design,
  security groups, file shares, and Group Policy enforcement.
---

# Enterprise Systems Administration

This project is a ground-up build of a multi-site Active Directory environment in my home lab. The goal isn't just to click through wizards — it's to design and operate the kind of infrastructure a real multi-site organization runs on, and to document the reasoning behind each design decision.

It's also not a standalone lab. This is the infrastructure behind **Nortex Solutions**, the same fictional ~50-person company my [Self-Hosted IT Service Desk](../self-hosted-it-service-desk/README.md) supports. Its three departments — Finance, Sales, and Operations — become real OUs and security groups, its employees become real AD accounts, and the three sites become Nortex locations. Once this environment exists, the service desk stops handling simulated issues and starts handling real ones: an actual password-expiry lockout driven by Group Policy, a real new-hire provisioning request, a share-access denial caused by group membership. **Build the infrastructure, then operate a help desk on top of it.**

When that second round of tickets arrives, I'll be working them the way a real help desk does: from a delegated **Tier 1 Support** account with just enough rights for password resets, unlocks, and group changes on the right OUs — not from Domain Admins.

{% hint style="info" %}
This project is currently in progress. Pages in this section are being filled in as each build phase is completed.
{% endhint %}

### Lab Environment

* **Hypervisor:** VirtualBox on a 32GB RAM host machine
* **Operating systems:** Windows Server evaluation ISOs
* **Topology:** three sites, with domain controllers per site and one read-only domain controller (RODC)

### Build Phases

1. [Lab Setup & Topology](building-the-environment/lab-setup-and-topology.md) — host, VMs, and the three-site network design
2. [AD DS Forest & Domain](building-the-environment/ad-ds-forest-and-domain.md) — forest/domain build, DCs per site, the RODC
3. [DHCP](building-the-environment/dhcp.md) — IPv4 and IPv6 scopes, reservations, failover
4. [DNS](building-the-environment/dns.md) — forwarders, reverse zones, CNAMEs
5. [OU Structure, Users & Groups](building-the-environment/ou-structure-users-and-groups.md) — OU design, accounts, security groups, delegation of control
6. [File Shares & Permissions](building-the-environment/file-shares-and-permissions.md) — share and NTFS permissions
7. [Group Policy](building-the-environment/group-policy.md) — account policies, auditing, workstation security, restricted groups

A [Lessons Learned](lessons-learned.md) page will collect the decisions, mistakes, and takeaways from the build.
