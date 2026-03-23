Run this, replacing the identity with the user's AD username (don't include email domain):

`$UserGroups = Get-ADUser -Identity <username> -Properties MemberOf`

Then run this to view the list of groups:

`$UserGroups.MemberOf | ForEach-Object {($_ -split ',')[0] -replace '^CN='}`

Then run this to create an iterable list of groups for removal:

`$Groups = $UserGroups.MemberOf`

Run this to remove the user from all security and distribution groups:

`foreach ($groupDN in $Groups) { Remove-ADGroupMember -Identity $groupDN -Members <username> -Confirm:$false }`

This should keep the user in the "Domain Users" group, but it's a good idea to verify.
