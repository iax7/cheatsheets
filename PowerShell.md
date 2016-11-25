# WebAccess (Windows 2012)
1. Install-WindowsFeature WindowsPowerShellWebAccess
1. Install-WindowsFeature Web-Mgmt-Console
1. get-help *pswa*
1. Install-PswaWebApplication [-UseTestCertificate]
1. Add-PswaAuthorizationRule -RuleName Admin -ComputerName win2012 -UserName 'Administrator' -CAdd-PswaAuthorizationRule -RuleName Admin -ComputerName win2012 -UserName 'Administrator' -CAdd-PswaAuthorizationRule -RuleName Admin -ComputerName win2012 -UserName 'localhost\Administrator' -ConfigurationName *

https://server/pswa

No crear este permiso en producción
Add-PswaAuthorizationRule * * *