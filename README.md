# Creating_domain_in_Active_directory

## Adding Active Directory Options in Server Manager

I didn't have any Active Directory options within Server Manager. I tried to add it through Apps, but it did not work. Then, I tried the following command through PowerShell, and it worked:

```powershell
Install-WindowsFeature RSAT-AD-Tools
