---
description: >-
  Designing the OU structure, provisioning user accounts, building security
  groups, and delegating control.
---

# OU Structure, Users & Groups

Where the directory starts looking like an organization: an OU structure designed around how Group Policy and delegation will actually be applied, user accounts provisioned into it, and a security group model that follows AGDLP.

{% hint style="warning" %}
This page is a placeholder — content is added as the build progresses.
{% endhint %}

### What this page will cover

* The OU design and the reasoning — OUs exist for GPO linking and delegation, not for looking like an org chart
* Mapping Nortex Solutions onto the directory: Finance, Sales, and Operations as OUs and security groups
* Provisioning Nortex's employees as real accounts — the same users from the service desk tickets, with naming conventions and account properties
* Security groups: global groups for roles, domain local groups for resources (AGDLP)
* Building the **Tier 1 Support** role with delegation of control — just enough permission for password resets, unlocks, and group changes, without Domain Admins

**Help desk connection:** this is where the simulated becomes real — Sarah Chen's account can now actually expire and lock out, and the Tier 1 account built here is the one all round-two tickets get resolved from.
