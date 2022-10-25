Configuring Password Policies from default
`secedit /export /cfg c:\secpol.cfg (gc C:\secpol.cfg).replace("PasswordHistorySize = 0", "PasswordHistorySize = 5") | Out-File C:\secpol.cfg (gc C:\secpol.cfg).replace("MinimumPasswordAge = 0", "MinimumPasswordAge = 2") | Out-File C:\secpol.cfg (gc C:\secpol.cfg).replace("MaximumPasswordAge = 0", "MaximumPasswordAge = 60") | Out-File C:\secpol.cfg (gc C:\secpol.cfg).replace("MinimumPasswordLength = 0", "MinimumPasswordLength = 14") | Out-File C:\secpol.cfg (gc C:\secpol.cfg).replace("PasswordComplexity = 0", "PasswordComplexity = 1") | Out-File C:\secpol.cfg secedit /configure /db c:\windows\security\local.sdb /cfg c:\secpol.cfg /areas SECURITYPOLICY rm -force c:\secpol.cfg -confirm:$fal`

Changing User passwords
`$passwd = Read-Host -AsSecureString Set-LocalUser -Name orvus -Password $passwd`

Updating Windows
`Install-Module PSWindowsUpdate Get-WindowsUpdate`

Auditing Policy

`auditpol /set /category:"System","Account Management","Account Logon","Logon/Logoff","Policy Change" /failure:enable /success:enable   

`auditpol /set /category:"DS Access","Object Access" /failure:enable`