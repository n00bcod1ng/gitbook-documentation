---
description: >-
  DNS configuration for the domain: forwarders, reverse lookup zones, and
  CNAME records.
---

# DNS

Active Directory lives and dies by DNS. This phase covers the DNS configuration beyond what domain promotion sets up automatically: forwarders for external resolution, reverse lookup zones, and CNAME records for friendly service names.

{% hint style="warning" %}
This page is a placeholder — content is added as the build progresses.
{% endhint %}

### What this page will cover

* How AD-integrated DNS zones replicate between the DCs
* Forwarders vs. root hints — what was chosen and why
* Reverse lookup zones for each site's subnets (IPv4 and IPv6)
* CNAME records for services, and why aliases beat hardcoding server names
* Verification: `nslookup` tests, reverse resolution, dynamic registration from clients

**Help desk connection:** "the app works by IP but not by name" and "can't reach the file server" tickets are DNS tickets — this page is where those diagnoses come from.
