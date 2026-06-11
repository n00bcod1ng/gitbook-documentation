---
description: >-
  DHCP for a multi-site network: IPv4 and IPv6 scopes, reservations, and
  failover between domain controllers.
---

# DHCP

Address management across three sites: scopes per subnet, reservations for devices that need stable addresses, and failover so a single DHCP server outage doesn't take a site offline.

{% hint style="warning" %}
This page is a placeholder — content is added as the build progresses.
{% endhint %}

### What this page will cover

* IPv4 scopes per site: ranges, exclusions, and lease durations
* IPv6 scope configuration
* Reservations — which devices get them and why
* DHCP failover configuration between servers, and the failover mode chosen
* Scope options (DNS servers, gateway) and how they interact with site design
* Testing: lease acquisition from each site, failover behavior when a server goes down

**Help desk connection:** "no network connection" and IP conflict tickets start here — understanding scopes and reservations is what separates guessing from diagnosing.
