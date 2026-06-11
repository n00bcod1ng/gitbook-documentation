# Project Context

This file gives background on the projects documented on this site so that pages stay accurate and consistent. Read it before writing or editing any project content.

## Site owner

Emmanuel Prada-Florez — Bachelor of IT (Honours), Networking and IT Security, Ontario Tech University. The site is a hands-on portfolio aimed at help desk / IT support roles. Tone: first person, practical, focused on real deployments and the reasoning behind decisions. Currently working toward CompTIA Security+ and CCNA.

## Project 1: Self-Hosted IT Service Desk (complete, documented)

A Dockerized **Peppermint v0.5.5** ticketing system running on a hardened Ubuntu cloud server.

### Simulated environment
- Fictional company: **Nortex Solutions** (~50 employees, 3 departments: Finance, Sales, Operations)
- Standard stack: Windows 11 laptops, Microsoft 365, VPN, shared network printers
- Five simulated employees: Sarah Chen (Finance), Marcus Webb (Sales), James Okafor, Lisa Patel, David Kim
- Peppermint v0.5.5 has **no native labels/categories**, so two workarounds were used:
  - Category prefixes in ticket titles: `[Hardware]`, `[Software]`, `[Account & Access]`, `[Network & Connectivity]`, `[New Employee Setup]`
  - Three department "clients" (Nortex Solutions – Finance / Sales / Operations) to group tickets by business unit

### Ticket queue (5 tickets, full lifecycle documented)
1. **[Account & Access]** Sarah Chen — locked out after password expiry. High priority. Resolved via simulated ADUC admin password reset, "must change at next logon", user educated on complexity policy. 15 min.
2. **[Hardware]** Marcus Webb — 2nd-floor network printer offline. Medium priority. Resolved via simulated physical restart and print queue clearing.
3. **[Software]** Marcus Webb — Outlook repeated sign-in loop.
4. **[New Employee Setup]** New hire laptop provisioning (treated as a **service request**, not an incident — ITIL distinction is a documented lesson).
5. **[Network & Connectivity]** Sarah Chen — VPN disconnecting every ~10 minutes when remote.

Each ticket page follows a fixed format: metadata line → Issue → screenshots → Resolution, with internal troubleshooting notes (never written as public replies).

### Knowledge base
- KB-001 and KB-002: technician-facing articles derived from resolved tickets
- KB-003: end-user-facing guide (deliberately written in plain language — writing for two audiences is a documented lesson)

### Key documented lessons (see Lessons Learned page)
- Working around tool limitations (prefixes + clients)
- Internal notes vs. public replies
- Incidents vs. service requests (ITIL)
- Documentation converts directly into KB articles
- Future improvement: put the service desk behind HTTPS via reverse proxy + TLS

## Project 2: Enterprise Systems Administration (planned rebuild — do not document as complete)

A rebuild of a multi-site Active Directory environment, inspired by coursework but built from scratch at home:

- **VirtualBox** on a 32GB RAM machine, Windows Server evaluation ISOs
- Multi-site design (three sites), domain controllers per site, one RODC
- Scope: AD DS forest/domain, DHCP (IPv4 + IPv6 scopes, reservations, failover), DNS (forwarders, reverse zones, CNAMEs), OU structure, users and security groups (global + domain local), delegation of control, file shares with NTFS/share permissions, Group Policy (account policies, auditing, workstation security, restricted groups)
- **Important:** this is original lab work described in Emmanuel's own words. Never reference, reproduce, or link course assignment documents.

### Portfolio narrative (important)
The two projects are intentionally linked: **"I built the infrastructure, then operated a help desk on top of it."** The target audience is help desk hiring managers, so the framing is always **help desk first** — the AD build exists to make the support skills credible, not the other way around. Lead with ticket handling, troubleshooting reasoning, and user communication; let the sysadmin depth be the supporting evidence.

How the connection is made concrete:

- **Nortex continuity:** the AD environment *is* Nortex Solutions' infrastructure. Finance, Sales, and Operations become real OUs and security groups; the five simulated employees become real AD accounts; the three sites are Nortex locations. One company, one continuous story across both projects.
- **Round-two ticket queue:** once the environment exists, re-run ticket scenarios against real infrastructure — a real password-expiry lockout driven by the GPO password policy, real new-hire provisioning (account, groups, home folder, GPOs), plus new tickets the build naturally generates (share access denied, GPO not applying, drive mapping failures). Document the before/after explicitly: "Ticket #1 was simulated; this one is real."
- **Tier 1 delegated account:** create a Tier 1 Support role with delegated rights (password resets, unlocks, group membership on specific OUs) and resolve tickets from that account, never Domain Admins. Demonstrates least privilege and how a real help desk operates.
- **Cross-link both directions:** every build-phase page ends with a short "Help desk connection" note explaining what tickets that system enables; ticket pages link back to the infrastructure page that explains the system involved.

## Project 3: Enterprise Network Security (listed on homepage)

Multi-zone pfSense network (LAN, DMZ, WAN) with OpenVPN, internal PKI, HAProxy, and hardened web servers.

## Writing rules for this site
- First person, Emmanuel's voice; confident but factual — no inflated claims
- Show reasoning, not just steps ("why" matters as much as "how")
- Distinguish simulated elements honestly (e.g., "simulated ADUC reset") until the real AD environment exists
- Follow skill.md for GitBook syntax and SUMMARY.md for structure
- Never include school assignment documents, course codes as the framing, or personal job-application details
