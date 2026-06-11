# Ticket #3 – Outlook Repeatedly Prompting for Sign-In

**Reported by:** Marcus Webb – Sales **Priority:** Medium **Category:** Software **Status:** Closed

#### Issue

User reported that Outlook kept prompting him to sign in every few minutes, interrupting his workflow. He entered his credentials multiple times, but the prompt continued to return, leaving him unable to send or receive emails reliably.

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

#### Troubleshooting & Resolution

The first step was confirming the scope of the issue. Webmail (OWA) access was working normally, which ruled out an account lockout or password problem and isolated the issue to the Outlook desktop client. The user's account status was verified in Active Directory and confirmed healthy, with no password expiry. Windows Credential Manager on the user's workstation was then inspected, where multiple stale cached Outlook credential entries were found. All cached Office credentials were cleared and Outlook was restarted. The sign-in prompt appeared once, the user authenticated successfully, and after 30 minutes of monitoring no further prompts occurred. Mail flow was confirmed to be fully restored.



**Step-by-step resolution summary**

1. Confirmed webmail (OWA) was working — isolated the issue to the Outlook desktop client.
2. Verified the user's account status in Active Directory was healthy.
3. Inspected Windows Credential Manager and found stale cached Outlook credentials.
4. Cleared all cached Office/Outlook credential entries.
5. Restarted Outlook and had the user re-authenticate once.
6. Monitored for 30 minutes and confirmed mail flow with no recurring prompts.



