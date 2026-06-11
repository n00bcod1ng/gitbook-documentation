---
description: >-
  Department file shares secured with share and NTFS permissions, granted
  through domain local groups.
---

# File Shares & Permissions

Shared storage with permissions done properly: access granted through domain local groups (never directly to users), and a clear understanding of how share permissions and NTFS permissions combine.

{% hint style="warning" %}
This page is a placeholder — content is added as the build progresses.
{% endhint %}

### What this page will cover

* The file share layout — shares for Finance, Sales, and Operations, plus any common areas
* Share permissions vs. NTFS permissions, and which layer does the real work
* Mapping the AGDLP group model onto each share
* Testing access as different Nortex users: confirming who can read, write, and who gets denied

**Help desk connection:** "access denied on the department share" is one of the most common real help desk tickets there is — this page builds the system that generates (and explains) those tickets.
