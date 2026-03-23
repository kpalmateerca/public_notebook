## Login issue: Bad Request Timestamp 40105
#### Cause: System time is out of sync, so Duo is rejecting login attempt. These attempts do not show up in Duo admin logs, but this is a Duo issue.
#### Solution: Re-sync system time with Microsoft servers.
1. Connect to PC in backstage
2. Run these commands in terminal:
`w32tm /config /update /manualpeerlist:"time.windows.com" /syncfromflags:manual
w32tm /resync'
3. Reboot PC
4. Try login again
---
