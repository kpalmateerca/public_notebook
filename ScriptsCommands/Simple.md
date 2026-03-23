# Force AD sync:

Requires admin, runs a delta sync:

`Start-ADSyncSyncCycle -PolicyType Delta`

# System file checker:

**Microsoft KB article:** https://support.microsoft.com/en-us/topic/use-the-system-file-checker-tool-to-repair-missing-or-corrupted-system-files-79aa86cb-ca52-166a-92a3-966e85d4094e

**Requires admin, downloads repair files (try to run this first):**

`dism.exe /online /cleanup-image /restorehealth`

**Requires admin, checks system files for errors, follow prompts to repair:**

`sfc /scannow`

# Last password reset date:

`Get-ADUser -Identity ADUSERNAME -Properties PasswordLastSet | Select-Object Name, PasswordLastSet`

# View default domain password policy:

`Get-ADDefaultDomainPasswordPolicy`

# Get a list of the users in an AD group:

`Get-ADGroupMember -Identity "GROUPNAME" | Select-Object Name`

# Get a list of rules on a user's mailbox:

`Get-InboxRule -Mailbox EMAIL_ADDRESS`

# View details of rules on a user's mailbox:

`Get-InboxRule -Mailbox EMAIL_ADDRESS | Format-List`

# Get list of users in a shared mailbox:

`Get-MailboxPermission -Identity "MAILBOX_NAME" | Where-Object { $_.User -notlike "NT AUTHORITY\SELF" } | Select-Object User, AccessRights | Export-Csv "C:\FILENAME.csv" -NoTypeInformation`
