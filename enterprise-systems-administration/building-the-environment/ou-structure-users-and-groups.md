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
* User account provisioning: naming conventions and account properties
* Security groups: global groups for roles, domain local groups for resources (AGDLP)
* Delegation of control — giving a support role just enough permission (e.g., password resets) without Domain Admins
* How this structure feeds the help desk project: real accounts that can really lock out
