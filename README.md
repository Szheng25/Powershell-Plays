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

&nbsp; Source: [samratashok/ADModule](https://github.com/samratashok/ADModule)  

&nbsp;  

## 

1. 

&nbsp;  
