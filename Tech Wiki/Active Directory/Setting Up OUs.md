Tags: [[Active Directory]] [[Organizational Units]] 

## Setting OUs with PowerShell

```PowerShell
New-ADOrganizationalUnit -Name "Sub Domain Name" -Path "OU= OU name, DC= DCName, DC= com or local or net "
```
#### Get the Name of your Domain Controller

```Powershell
Get-ADDomainController -Filter *
```


#### Create a User in Powershell

```PowerShell
New-ADUser -Name "John Doe" -SamAccountName "John.Doe" -UserPrincipalName "John.Doe@galaxydynamics.local" -Path "OU=Users,DC=galaxydynamics,DC=local" -AccountPassword (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force) -Enabled $true
```

#### Move User to OU
```PowerShell
Move-ADObject -Identity "CN=John.Doe,OU=Users,DC=galaxydynamics,DC=local" -TargetPath "OU=Developers,OU=IT Department,DC=galaxydynamics,DC=local"
```