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

## TLS version

1. To enumerate 'systemdefault' to see what's supported:
2. 

&nbsp;  

## AMSI Bypass

&nbsp; Source: [S3cur3Th1sSh1t/Amsi-Bypass-Powershell](https://github.com/S3cur3Th1sSh1t/Amsi-Bypass-Powershell)  

&nbsp;  

## ADModule

&nbsp; Source: [samratashok/ADModule](https://github.com/samratashok/ADModule)  

&nbsp;  
