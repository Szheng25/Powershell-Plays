# Powershell-Stuff

&nbsp; Powershell stuff  

&nbsp;  

## Domain Forest Trust enumeration using .NET classes

1. Run as a domain member on the workstation  

2. To get information regarding forest for the current domain:  
`[System.DirectoryServices.ActiveDirectory.Forest]::GetCurrentForest()`  
&nbsp;&nbsp;&nbsp;&nbsp;- *'GlobalCatalogs' can be appended to get global catalog*  
&nbsp;&nbsp;&nbsp;&nbsp;- *'Forest' can be replaced with 'Domain' to get domain info*  
&nbsp;&nbsp;&nbsp;&nbsp;- *The previous replacement and appending 'GetAllTrustRelationships()' gives trust relaitonship info for the domain*  

3. Declaring / setting the vbl $ForestRootDomain:  
`$ForestRootDomain = '<>'`  

4. To get information regarding forest for the current domain:  
`([System.DirectoryServices.ActiveDirectory.Forest]::GetForest((New-Object System.DirectoryServices.ActiveDirectory.DirectoryContext('Forest', $ForestRootDomain)))).GetAllTrustRelationships()`

&nbsp;  

## AMSI Bypass

1. Source 1: [S3cur3Th1sSh1t/Amsi-Bypass-Powershell](https://github.com/S3cur3Th1sSh1t/Amsi-Bypass-Powershell)  

2. Source 2: [reigningshells/powershell-bypasses.ps1](https://gist.github.com/reigningshells/a255fcca07465befbcbf4be9cdf67560)  
&nbsp;&nbsp;&nbsp;&nbsp;- *This works*  

3. Source 3: [NullPtrStack/amsi-bypass](https://nullptrstack.github.io/amsi-bypass/)  
&nbsp;&nbsp;&nbsp;&nbsp;- *Test with the bypass in this one*

&nbsp;  

## TLS version

1. To enumerate 'systemdefault' to see what's supported:  
`[enum]::getvalues('net.securityprotocoltype')`  

2. To set to TLS1.2 (or greater):  
`[Net.ServicePointmanager]::SecurityProtocol = 'Tls12'`  
&nbsp;&nbsp;&nbsp;&nbsp;- *can replace 'Tls12' with a greater version*  

&nbsp;  

## ADModule

1. Clone or download ADModule: [samratashok/ADModule](https://github.com/samratashok/ADModule)  
&nbsp;&nbsp;&nbsp;&nbsp;- *can also just download the 2 needed files*  

2. `Import-Module \<absolute or relative path>\Microsoft.ActiveDirectory.Management.dll -Verbose`  

3. `Import-Module \<absolute or relative path>\ActiveDirectory\ActiveDirectory.psd1 -Verbose`  
&nbsp;&nbsp;&nbsp;&nbsp;- *If the execution policy fails, do `Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Unrestricted` and then do step 2 onward*  
&nbsp;&nbsp;&nbsp;&nbsp;- *Can also do `Unblock-File <file_path>`*  

5. `Get-Command -Module ActiveDirectory` *won't work* and `Get-ADDomain` *will work*  

6. `iwr -Uri "https://github.com/samratashok/admodule/archive/master.zip" -Outfile ADModule.zip`  

7. `Expand-archive .\ADModule.zip`  

8. `cd .\ADModule-master\ActiveDirectory`

9. `import-Module ActiveDirectory.psd1`

10. `Get-Command -Module ActiveDirectoryn   get-`  

&nbsp;  

## 

1. 

&nbsp;  
