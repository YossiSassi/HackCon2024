<b>Scripts|Tools|Commands used or mentioned in the demos of this talk:</B>
Enum rpc dependant services:
sc.exe enumdepend rpcss 32000 | sls 'display_name' | Measure-Object

Fix Clock Skew remotely (RPC not available):
$varDate = Get-Date; Invoke-Command -ComputerName <IP>      -ScriptBlock {set-date $using:varDate} -Authentication Negotiate
OR
Invoke-WmiMethod -ComputerName <IP> -Class win32_process    -Name Create -ArgumentList "w32tm /resync"

Named pipes C2:
https://github.com/YossiSassi/SEC-T_21-One-Liners-Powershell 

RDP MitM (one out of few..):
https://github.com/SySS-Research/Seth

Find disconnected sessions (actually, all active/disc sessions in the domain):
https://github.com/YossiSassi/Get-UserSession

PSRemoting with jobs:
Invoke-Command -ComputerName $computers -ScriptBlock {ipconfig /all} -AsJob; 
Get-Job | Wait-Job; 
Get-Job | Receive-Job -Keep > c:\ipconfig.txt

Token duplication (one option out of many):
https://github.com/PowerShellMafia/PowerSploit/blob/master/Exfiltration/Invoke-TokenManipulation.ps1

Bypass powershell defenses:
https://github.com/YossiSassi/Invisi-Shell
