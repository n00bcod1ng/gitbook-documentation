# Ticket #2 – Network printer showing offline

**Reported by:** Marcus Webb – Sales **Priority:** Medium **Category:** Hardware **Status:** Closed

### Issue

User reported that the shared network printer on the 2nd floor was showing as offline on his workstation. He was unable to print a sales proposal needed for an upcoming client meeting.

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

### Troubleshooting & Resolution

The print spooler service on the affected workstation was checked remotely and confirmed to be running. A ping test to the printer's IP address returned no response, which confirmed the printer was offline on the network. Physical inspection showed that the printer had powered off unexpectedly. The printer was restarted and reconnected to the network. The stuck print queue on the user's workstation was then cleared. A test print completed successfully and confirmed that service was restored. The user was advised to contact IT if the issue happened again.

#### Step-by-step resolution summary

1. Confirmed the print spooler service was running on the user's workstation.
2. Tested connectivity to the printer's IP address with a ping check.
3. Verified that the printer was offline and powered off during physical inspection.
4. Restarted the printer and confirmed it reconnected to the network.
5. Cleared the stuck print queue on the user's workstation.
6. Completed a successful test print to verify service was restored.
