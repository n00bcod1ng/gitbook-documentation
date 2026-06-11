---
description: >-
  Building the AD DS forest and domain: domain controllers per site, AD Sites
  and Services, and a read-only domain controller.
---

# AD DS Forest & Domain

The core of the environment: a new forest and domain, domain controllers placed per site, and a read-only domain controller (RODC) for the site where physical security would be weakest in a real deployment.

{% hint style="warning" %}
This page is a placeholder — content is added as the build progresses.
{% endhint %}

### What this page will cover

* Forest and domain design decisions (naming, functional levels) and the reasoning
* Promoting the first domain controller
* Configuring AD Sites and Services: Nortex's three sites, their subnets, and site links
* Adding additional DCs per site and verifying replication
* Deploying the RODC — what it does and doesn't cache, and why a branch site gets one
* Verification steps: replication health, SYSVOL, DNS registration

**Help desk connection:** these are the domain controllers that real account lockouts and sign-in failures authenticate against — the round-two versions of the service desk's account tickets get resolved here.
