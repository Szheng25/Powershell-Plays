# Powershell-Stuff
Powershell stuff

## Domain Forest Trust enumeration using .NET classes
Declaring / setting the vbl $ForestRootDomain  
`$ForestRootDomain = 'us.local'`  
To get information regarding forect for the current domain  
`([System.DirectoryServices.ActiveDirectory.Forest]::GetForest((Net-Object System.DirectoryServices.ActiveDirectory.DirectoryContext('Forest', $ForestRootDomain)))).GetAllTrustRelationships()`  

## AMSI Bypass
Source: [S3cur3Th1sSh1t/Amsi-Bypass-Powershell](https://github.com/S3cur3Th1sSh1t/Amsi-Bypass-Powershell)


## ADModule 
Source: [samratashok/ADModule](https://github.com/samratashok/ADModule)

