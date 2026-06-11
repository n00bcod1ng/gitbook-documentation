---
description: >-
  The goal of this project was to deploy a fully functional IT service desk
  environment using Peppermint, a containerized ticketing system.
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Self-Hosted IT Service Desk

Deploy Peppermint on an Ubuntu server and expose the web app on port `3000`.

This setup is suitable for testing and lab use. For production, place Peppermint behind HTTPS and keep the database private.

### Prerequisites

* A Linode account
* An Ubuntu 24.04 server
* SSH access to the server
* Docker and the Peppermint container stack on the host

{% hint style="warning" %}
Do not expose PostgreSQL on port `5432` to the public internet unless you have a specific requirement and additional controls in place.
{% endhint %}

### Step 1: Create the server

Create a new Linode compute instance for the deployment.

1. Create a new cloud instance in Linode.
2. Select **Ubuntu 24.04 LTS**.
3. Choose a plan that fits your test workload.
4. Set a strong initial password or add an SSH key.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Create the Ubuntu host for the Peppermint deployment.</p></figcaption></figure>

### Step 2: Lock down inbound access

Start with a deny-by-default firewall policy. Then allow only the traffic you need.

1. Create a Linode Cloud Firewall.
2. Set the default inbound policy to **Drop**.
3. Allow SSH on port `22` from your own public IP only.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>Create the firewall before exposing the server.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>Restrict SSH access to a trusted source address.</p></figcaption></figure>

### Step 3: Verify the Peppermint containers

After connecting over SSH, confirm that the Peppermint stack is running.

```bash
docker ps
```

Check that:

* The Peppermint web app listens on port `3000`
* PostgreSQL listens on port `5432`
* All required containers show a healthy running state

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p>Use `docker ps` to confirm the application and database containers are running.</p></figcaption></figure>

### Step 4: Allow browser access to the app

If the firewall drops all inbound traffic, the web interface stays unreachable until you open the app port.

1. Return to the Linode Firewall.
2. Add a custom **TCP** rule for port `3000`.
3. Allow the source range required for your users.

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption><p>Open port `3000` so users can reach the Peppermint web app.</p></figcaption></figure>

{% hint style="info" %}
For a public test instance, allowing `All IPv4` and `All IPv6` on port `3000` is acceptable. For production, place the app behind a reverse proxy and expose only ports `80` and `443`.
{% endhint %}

### Step 5: Verify the web interface

Open the Peppermint app in a browser using your server hostname or IP address.

```
http://your-server-or-hostname:3000
```

If the page loads, the deployment is reachable and ready for sign-in.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>Confirm that the Peppermint login page opens in the browser.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption><p>Successful access confirms that the application is ready for use.</p></figcaption></figure>

### Troubleshooting

If the app does not load:

* Run `docker ps` to confirm the containers are still running.
* Recheck the firewall rule for port `3000`.
* Confirm you are using the correct server IP or hostname.
* Keep port `5432` private unless you explicitly need remote database access.

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p>Use the running service state and port bindings to troubleshoot access issues.</p></figcaption></figure>
