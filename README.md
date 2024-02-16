<b>Scripts, tools and commands used or mentioned in the demos of this talk:</B>
<br>
Enum rpc dependant services:

sc.exe enumdepend rpcss 32000 | sls 'display_name' | Measure-Object

<br>
Fix Clock Skew remotely (RPC not available):

$varDate = Get-Date; Invoke-Command -ComputerName 10.0.0.20      -ScriptBlock {set-date $using:varDate} -Authentication Negotiate

OR

Invoke-WmiMethod -ComputerName 10.0.0.20 -Class win32_process    -Name Create -ArgumentList "w32tm /resync"

<br>
Named pipes C2:

https://github.com/YossiSassi/SEC-T_21-One-Liners-Powershell 

<br>
RDP MitM (one out of few..):

https://github.com/SySS-Research/Seth

<br>
Find disconnected sessions (actually, all active/disc sessions in the domain):

https://github.com/YossiSassi/Get-UserSession

<br>
PSRemoting with jobs:

Invoke-Command -ComputerName $computers -ScriptBlock {ipconfig /all} -AsJob; 

Get-Job | Wait-Job; 

Get-Job | Receive-Job -Keep > c:\ipconfig.txt

<br>
Token duplication (one option out of many):

https://github.com/PowerShellMafia/PowerSploit/blob/master/Exfiltration/Invoke-TokenManipulation.ps1

<br>
Bypass powershell defenses:

https://github.com/YossiSassi/Invisi-Shell
