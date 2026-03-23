# Calendar Permissions in PowerShell

NOTE: You need to Connect to the client's Exchange Online environment in PowerShell before running these, which may require installing some modules. Instructions for that here: https://github.com/kpalmateerca/notebook/blob/main/ServiceDeskSpecialist/ScriptsCommands/InstallExchangeModule.md

## View calendar permissions for all users:

`Get-MailboxFolderPermission -Identity "EMAIL_ADDRESS:\Calendar"`

## View calendar permissions for a single user:

`Get-MailboxFolderPermission -Identity "EMAIL_ADDRESS:\Calendar" -User "USERNAME"`

## Add calendar permissions (if user has no specific access):

`Add-MailboxFolderPermission -Identity "EMAIL_ADDRESS:\Calendar" -User "USERNAME" -AccessRights PERMISSION_LEVEL`

## Update calendar permissions (if user already has access):

`Set-MailboxFolderPermission -Identity "EMAIL_ADDRESS:\Calendar" -User "USERNAME" -AccessRights PERMISSION_LEVEL`
