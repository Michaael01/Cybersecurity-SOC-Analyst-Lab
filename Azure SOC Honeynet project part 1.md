![GitHub Logo](https://media-hosting.imagekit.io//4c0ea0bc78524599/topology.png?Expires=1835646182&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=kgzd00L-Re8gscHJb9mr80EkKwMrlFeulpokq8feV0U54UhRXT5M8U-Bq6ET5J768Qr7XcWVdvkA3qQe-p~iYfE8FXXuxOag8Fb4p8E6Mw5DAiQCQ~7MNkNTPGQ9k1ixG4RAlzWTRrOuuu4fBtyKuxHvjnEYBGeqW9rg5N~3cPLLQqFeCCv58-gB8HOCLmwSVO3FUqhawZg5qs2aRQwAqvM-n1GhKvrTZ78neYvZwakUVNngEH9VODCc9kFs-zkYTNizIjnQywUArMXvpGgW6AjANY7Ou2Z5tJdZse-UJlui7eKEzmo~9JriVsRlCAbLx-i1FiLO2tPQWTY3uNSqTw__)
# Honeynet Project Description
My topology contains Azure subscription, followed by a Resource group which is in form of cloud  folder for my resources, Vnet, created a vm and attached it to the virtual network and also make the Virtual machine enticing to attackers by turning of the firewall. Created Azure firewall NSG and will be completely open up as well as firewall from windows. By leveraging Azure Log Analytics Workspace and Azure Sentinel, SIEM, geographical IP I was able to collect, aggregate, and visualize attack data effectively. I enjoyed embarking on this project, and I hope anyone reading this appreciates will like it as well.

1. Created the ressourse group that will group all my resources
2. Created virtual network oluwatosinvm-vnet in the same region and attached to SOCRG
3. Created the virtual machine. attached the OluVM to SOCRG and VNET oluwatosinvm-vnet
4. Opened the VNET Firewall and deleted the default inbound rule for RDP that was listening on port 3389 ![GitHub Logo](https://media-hosting.imagekit.io//01a2891a15854259/remove.png?Expires=1835533577&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=f3Xik1LMNR7hlotRG3RbRdPkzul6u2-Sb4KX1hnlRF59-WhymOIJR2QofZ8u2pdcXdJxbYJp7UosMqBACBugeRBu4GJ~TPawFn6Mx2Ht-oEevXhT-k51NDEeuLpp~u1cirq-4QmhwZEkXFsOPrKzCLpiV2qOoNo59nd8zlf2glDM5J5K24yetqbBGaP80pCaJSwBbYEsepgYWrNlDORQ5kxOGrLbvIpYjp3VWyYYyY-AlzMzTChnKVir2UeMmA2KPq1lthhOJ5aY~-OkRT0r7g6NCEzHmLfQZo1jhT8d75guNHHS~SqcBbdD9WtL4Ol9v39p6X3YWiMPGGOvTvXFIQ__)

## Create Inbound Rule on Nsg
5. Created another new inbound rule by going to settings, clicked on inbound security rules
6. Click add.
7. Set Source port ranges to any (*).
8. Set destination port range to any (*).
9. Set priority to 100 because the lower the priority, the sooner the rule value get evaluated. I left the priority valuea at 100 because it will be the lowest priorty on the list as shown in the picture below. A security rule can't have the same priority and direction as an existing rule. You can't delete default security rules, but you can override them with rules that have a higher priority.Learn more https://go.microsoft.com/fwlink/?linkid=2174617 ![GitHub Logo](https://media-hosting.imagekit.io//80808ef7775348fe/nsg.png?Expires=1835534171&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=bQvRb-Q4LflFjmo3tfe7GQaevUjlAOyUQe60YJLVUw7TZSnmWzFvtUUNGqd5IcxVtgMSGWaT9lfVtoYjAOQv-YsZpFSZ7Kc~RoNeJ2KUVymFtSnzPp3k4LDVHyzeNDXNxc0tRYZD60IW1WPAb1yOYnjtoQaDGFxgJxyjUkIQ2VrksFTNXK8NpG6lq7oGcTqxBxcqudAfN810j2At3~a6Ce6dkRXtRN5SXeVyjdY9~QtSGS~ADJphdOGq5pPWmF6nmYTOZhJolfOpC5ErtcPJ5-Mw2BPYXp0~1cEGT~5H5IvJZvuZi4weRW6srEgSDm-AUnVK9oaR-tumr9aPWMTV~w__)
10. Named it DANGER_AllowAnyCustomAnyInbound in order to make the name more attractive

## Disable Internal Windows Firewall from the VM

1. Copy the public IP address from Azure vm
2. Go to the RDP, apply the IP and login credentials
3. Go to windows defender firewall with advanced security ![GitHub Logo](https://media-hosting.imagekit.io//e02e699ed644423c/firewall.png?Expires=1835547354&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=rJTC93CwiS950bT58~ToLKw5MFHxo3N-IPzMPt6YLg8HLW43GNGWz47Kf50JO3~dctyl2MjybSHk~bsworlCujH5sOI7KLdiQPqCr6tARZhKDOZQzhJpyt5~xjoqL6M6stniM61lFZoiAoLtMUUfrx7KDUkN8O34Qw61JmedpLx81fUNody3f5NSdmSVhIX852fnXSB9T0uydLWHVobiuIcx1cKC8Yj6mjtI1SIALa8ibjSukFqOdQTsHO8oEPXiZXkO-uqt3m9b11fbs~76uYLyJ9as0nfCX4PnekAtg5ejH79YhH6~NQzW7f90QljkfbGaufNb0-nwrJc795s~RA__)
4. Click windows defender firewall properties
5. Turn off firewall state for Domain Profile, Private Profile, Public Profile
6. click on Apply, then Ok. You will recieve a firewall settings notification suggesting to turn on but ignore for now.

### Ping virtual machine
1. Copied the ip address from azure machine VM
2. Go to Remote Desktop, open command prompt
3. pinged 74.234.196.195 from the command prompt. The reason is that if I can ping successfully, then the attackers can as well ping it. ![GitHub Logo](https://media-hosting.imagekit.io//5d83958fa5534b5b/ping.png?Expires=1835547999&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=AOnpTvVPzxrDzMyl-HyVWpoo43VyIjCA7m4qc8Q1EwnLdl95ijzOO4TxP9N3muE~iudylAhDCiG3jLzb3u1ZObaw2Z2mLaFSmQUjNlg0CagJRDn93oC7zA26QkvbPa0UJaWWoI3k~N9FJIdkIICEPc~vJuu3v2OJYvXRM1Q9WGIfoqWXA4CoQdi4hSyefIo3EP-NZ5w2cIz5V7~mlC~Kw9bW9jHgLXlhnEkx4hZ0B5pemICRPWJLRdVOBxJZCNRy8l1XUtFm4H7KEQn6S66PXOUSpZU8xgt~yO2EMq55bLm9MWNcstCCBkG9D-xN6xRkWVWlNY4-JZtv0grKzmCuXg__)

#### Viewing raw logs from the Virtual Machine
1. logout of the VM
2. Attempt multiple login with wrong credentials such as typing in wrong password before typing in a correct credentials ![GitHub Logo](https://media-hosting.imagekit.io//4ed17a0c8d314b0b/wrong%20attempt.png?Expires=1835549388&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=Fh7bzcbDN4QEnJKzzDc1YRGCuygxa~5V2Z7xrR4TEmVkUWMbAm7MXLS1BDjMv5OY579bcUGXOWYztwm~ba3bX7lYmxVn5S2Pi6gcChWAgxpCpLDVPCOBLCVTRyToKq2mnY3TwRBVsZcDyH-P3zdNPUeHxo5USpMx9YfaS1wN73Lvl1uu2J46wN8dXCcRbOkDi~uFhksZdDOIe-62Wj~MqFkDgartNyFLJHWWVia3Ax7BANd1yUKiq6N4-GTfvJwr6QGC--gTJMStcEqnD3~2zXV9VAPJcMIy0Nt5WhUKRKEqmaKKukbAkTLTV3ySFiVo0jijqU2z5~lR~3DlcR2-bg__)
3. Go to Event viewer, expand windows logs and click on security.
4. Click on find to search for code "4625". error code 4625 is basic a code for failed logon. So, all attempted logins from the attacker will be logged inside our Event Viewer

##### Creating a Log Repository-Log Analytics Workspace
The log resipotory will help to forward our logs to Azure
1. Went to Log Analytic Workspaces and click on create log analytics workspace called JshHoneypot and attached it to SocRG resource group
2. Go to Sentinel and refresh.
3. Select the Log analytics and click on Add. This will link log analytic workspaces to our SIEM or sentinel instance in order to access the logs in our log repository from SIEM. SIEM will help to collect and analyze data from any source, cloud or on-premise. ![GitHub Logo](https://media-hosting.imagekit.io//67f11e9d32044f0c/sentinel.png?Expires=1835553060&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=tQiUlA~MSB6JjQp8KNQdfHUAbLbVLQbvv03r9DdEPkog6Rz9d1aRp7wEPI01Vy3tfP7uTuxlTGN4QSoTv3SI8AoPdC2HcgL~xtkkhVSUABqSIo1HLvTD9gpIR04LoSH88ONnwQt5456~vPo5Ccfm2UWfPKCpP5TvZYAr-12E-hcMN8qwQ7R8oAawR5sSKkmnEfuNboKnzz~4XTQKtD4oNyLJcR1ozH3hggTI57CT6wed2Bzm4ZNard9Oq0scg6cCDyblZGcOaO1B~TqkLN7I0wbGrJAjoC~S-V76a84lkd0u9xLshHA8I2Z~jjwrQP193fWt~zrm4-J5Q8Z~keZCNg__)
4. Go to conten hub and search for windows security event
5. select windows security event and click install to install the connector. The Windows Security Events solution for Microsoft Sentinel allows you to ingest Security events from your Windows machines using the Windows Agent into Microsoft Sentinel.
6. Click on Manage
7. Select Windows Security Events AMA and click on open connector page from the lower right corner of the page.
8. Click on Create Data Collection rule. This rule is used by the virtual machine to forward log into our analytics workspaces which lets us access them inside our SIEM
9. added rule name, added my subscription, and added resources group SOCRG. click on next![GitHub Logo](https://media-hosting.imagekit.io//89ed7d87bd0b46c0/connector%20rule.png?Expires=1835556488&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=UJr~ZVKrIIqFpXnEyaeiH-JkdjsEa0seCZQ-zutscgIcdEs0Qu2g9kVZmZqzk3QkB7kDcsCvfAR9KBZSFCKZ3pYBAv1zAoL~qJdy1Ue7swlzVWbwu67NXI-9kkkl96eG5aIxSfoI-gpUCJUrg7aKdxfhqzgNvlCn5fG8V0mjy6TFZw2DJGjfL~cPQTRNzb0yLwFGkc5K89w2hrAsqHCabm2ffjLwQoBsvf3BRXR06VrOkrzfGyYeCi9i2SY7ceifCD8ddo~5Mb7iGzRmxCR87ZmgZGKJRtmESI2Ln8S-8MArtXqktn9Ya6Yi5YuxZGv3kpDcskoRKgS7JOYx7MuwxQ__)
10. Clicked on drop down on Subscription, resource group and select the Virtual machine OLUVM
11. Review and create.
12. Go to Log Analytics WOrkspace to be sure the logs are now coming in as shown below
13. Go to logs and type _SecurityEvent_ in order to view the windows log. The logs are forwarded using the Azure Monitoring Agent into the central log repository called Log Analytics Workspace  ![GitHub Logo](https://media-hosting.imagekit.io//c3c3e2efb0a843b7/sec%20event.png?Expires=1835587517&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=ZpOJX~rRKwCOga3frYGA~8hOVkyiLK00hI5Kfaln7-6qfyqknrBXkFjJkFB5of4h4d0IixvSW3mU2Uc~Cgwu1gavTNyNwjRLMtA59eda2nFDNt~lV1eOHdiTHAzx1Lqv~4McEFDOlmB3pA78~ecLWPcRogrQCDhxEF2CLQKv8YeDwp-F7zB9SA0n9y3cUGCgeQ8R4wH7jViLjVVmpHbAd4NLq7UKirPpL2Le4M3-XuRFy5MMck6PiYYCrhS1WJK0UL6KuOUb6u84XzZvUhXZrB8Yw5CWXibAN-r-cSJzFwtjtfcX7nG5IJyV3uQxEApWgm8S09xgRkONFZ804RMzpw__)

###### Querying My Log Repository with KQL
The Kql helps to filter out the informations we want to see from the our data. for example.
-  SecurityEvent
- | where Account == "\\ADMIN"
- click on # Run and it will show only the records that have that name \ADMIN.
- we can filter down with how much data to be displayed by using # PROJECT
- SecurityEvent
| where Account == "\\ADMIN"
| project TimeGenerated, Account, Computer, EventID, Activity, IpAddress
![GitHub Logo](https://media-hosting.imagekit.io//708ed038f6724e10/project.png?Expires=1835634393&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=jGBHaRoBHdg5G6H35LcDQ4Wvn9PYY1A~PbC3DEtl~06VoH5-3r~HeY85JpV1JE93CnzLHXSuSZezgextNl30YERt114ULuzWPXftFzM-FUZLSewak8TmtgcEKScZ7gw6gmpcProiGrPnWNPVDvUOvsTKQLSaj2TSpe7YLlYlBYI8trnyVRQbrX30Ynodrk0nAflfF1Ziog4kXwGHVfHbNN6x9Uybmwc41cAyoErbA5H2tGFfV5xlwQXR7OVZsqnZqSl0u4WgoRtKWvwWT4u~xZERmTInfo9V-0Ac3JXn8A6PZmzSQDgOWPAhfnr57CiCdQYcY6hrEIiQH6cIfS1lzw__)

- This will display the account with all the feeds that was projected. I can see from the ipaddress 221.0.90.67 that someone from the internet is trying to access my machine. I copied the address and looked it up by typing geolookup 221.0.90.67 to google which shows that someone from Chinais trying to access my machine.

- To check failed logon, I used kql command:
- SecurityEvent
| where EventID == 4625
| project TimeGenerated, Account, Computer, EventID, Activity, IpAddress

![GitHub Logo](https://media-hosting.imagekit.io//1b3ecfcf55664ef9/failed%20logo.png?Expires=1835634906&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=aFmjtr8xNMZFspwwpH~4rTYLLWhMjzT-rSyniPBxYfDz7M-esARKZLzl1DjjR3HauyW9GaOElyOGISMH2wZW-5lBglMX2l~g1zpxfjTOYmyEHthiQzeKo62MwjrhQ3g0W907QHfi10fSI4d~79gmALOakxWkM6dE55WvLICqxgvgYHJoe978PLUr54UYfl9Wa9UFn5HzgQpmCms0he5iB3oXT2Y4x~Gl55DToj9n4Ui0kQAUQpSG~Lsz4FUY3S5uI2BopL8FpmWxS6um697UZ1LyB7wY96IbWoGwVfYxwe5r0E6-ZM8mL8Tn9FgvI-5~fRz65eviRT4~jcLy41MlaQ__)
- This will display all failed logon attempt based on the the projected column and I was able to detect 315 failed logon attempt within a short period.
- We may want to know the time period a certain event happened for example, last 10 min by typing the command below.
- SecurityEvent
| where EventID == 4625
| where Timegenrated > ago(10)
| project TimeGenerated, Account, Computer, EventID, Activity, IpAddress

# Upload Geolocation to the SIEM
This will resolve ip address to physical location on the map. I uploaded  a geoip summarized cvs file with different address ranges in the world with latitude, longitue, cityname and courtyname. The sentinel will look into the ipaddress land of the attacker and will map it.
I uploaded by:
1. Downloaded geoip-summarized csv file from https://drive.google.com/file/d/13EfjM_4BohrmaxqXZLB5VUBIz2sv9Siz/view?usp=sharing
2. Went to Sentinel and clicked on watchlist
3. Click on New. under general, let Name = geoip, Alias = geoip and click next to open source page and browse the csv file. ![GitHub Logo](https://media-hosting.imagekit.io//24ccba8d4d9b4438/geoip.png?Expires=1835640069&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=tFagA4EfiZ7pyDvqmFRJ4FEljqRRviv8GEarX1dfUQIzbHpMuS5r5Nrj12PeOFja-ADmZJKIE1~jfpZtSCAMg63iVxegezWpJKwH7EcQny8qRgV4TJ2g~oTF2XKKO2EyMif6rYsVvEFeGFBb9pD-0OHeUJQ2feFNMan3uvflJdImXTXNuMh2UZTwppC7JA6K3hjcfYd1ltx8YT3N17exrY79kqywv9m7mAd7ZVxHVT3lj5kp~4onQCxo4QHh9pPJ7PXzyJ~c2Lel8nQzr5gRyyDuN2GOlnPYrBzi9Hz9DOpssrn~pA6OjREiUynQRImjPe4ltr1xLfNszKZLjQT1pg__)
4. On searchKey drop down, select Network
5. Click on review and create. This automatically took me to the watchlist page and will take some time to fully upload
   
## Inspecting Logs to Detect Attacker Locations
1. Go to Microsoft sentinel and open Logs
2. Query _SecuritEvent_ table
3. Type _GetWatchlist("geoip") , click Run ![GitHub Logo](https://media-hosting.imagekit.io//0be402f6d3994f29/geoip.png?Expires=1835642038&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=S3-DRMoXqZ~ne1wd0vZjSNUyTgTtooGGEnKur~DBqs436pK17DMbMOoUxSrFI586L~RccsSOdAER0cPpRVjd31MVl4pRqjDzW~GyGoWWZQ~PSksEE9d3r9d0Cflxn2Mp6Qwsv3PAxPeHxnq4EsaIyutglLuklHnBl7NE3OkMVxtG8tcFJ6DCu-UtIzkUk~1sk~N63l4Ygrrb24XeZpo5qkmkJWJF4d3xBHHP9l7IfBFBouee0naA~iaqEinvRPhjvIZTM5BqQoTBqaLEDl-MdLFLNrdtlZ8ybqjMfu2z4N0XiLZFUsQlJOOsJcxs7wye7yQDmnyfY4co1Ikgih43MA__)
- as shown in the above picture, the actual watchlist was generated into Azure. I now have the network column, the longitude, the latitude, city name, country name, unique identifier, time generate, searchKey. This will help us to know more about where the attacks are coming from.
- If I type:
-  SecurityEvent
| where EventID == 4625
- I copied one of ipaddress and pasted it in the qeury below.
- let GeoIPDB_FULL = _GetWatchlist("geoip");
- let WindowsEvents = SecurityEvent
-     | where IpAddress == "129.146.46.79"
-     | where EventID == 4625
-     | order by TimeGenerated desc
-     | evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network);
- WindowsEvents
- This will give me access to locational data and can see where the attacker is coming from and can always project to get more information about the attackers with timegenerated, the computer, Attackerip = ipadress, cityname etc. as shwon below

 ![GitHub Logo](https://media-hosting.imagekit.io//bd97f703d555485f/attacker%20ip.png?Expires=1835644310&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=U9YfoHG-cfzVNg2GlPYUCPHXzcGL51rUziVml9FNv-SAQK9otq-2dzcmRON9Q2IW9Ew~I7LFrM6iXsAA3CiSIE4FJwqD71eZ0fXmvux510wXmfznxpunshYVoipJTB1oWxt2ZwT2k3w~BJYTAOS4lNvloh031VUlULaDII2Mj92-RzT9W08qilksohGDnShRczD5kGVfBCVJsmGCXn8otyL~n-fCS~41lrpaHs5Itv0KXuVzpwD-3HyVIku9MqslncN0pRsOf9mDjmENdsrB2FCkU3rh8JW03~FzLSdQjaMwJxuz5IfOzEbjbEe217Y0EgSO2gqfQufO78dnQLepNw__)

# Creating Attack Map
1. Went to Microsoft sentinel and clicked on workbooks
2. click on Add Workbooks and click on edit
3. Removed all prepopulated elements by clicking on the (...), remove.
4. Openend the content on of this JSON FILE https://drive.google.com/file/d/1ErlVEK5cQjpGyOcu4T02xYy7F31dWuir/view?usp=drive_link and copied all.
5. Went back to my sentinel workbook page, clicked on add and from the drop down, selected add query
6. Click advanced editor, removed the contents and paste the Json script ![GitHub Logo](https://media-hosting.imagekit.io//343e835c60874a0c/json.png?Expires=1835644854&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=ls7itK2D90dlcF8RKewGlDDqmyPnfc7klXSt~oVoffQK7zFsriCh6Opa7wMYVrzhGqGWB9hh6hT1TwFPGpeuVjz-D2EQIfwmw8FDVfyBwuBJzKAdWfVhF2ia8Hp0F9KhrhqwnBapWdDVos90my2Pvn4OXNDfLMucBHHASJA5g~g0KQ5aA26RrOLe2tqiaahqbZGmlyik7vwhDqDjBXytLxkRGXqmxjJ37K7~yezTxuup-tL4ITPsQQW4ABZK5oq~uWwFcEL7FTrvTLlKGRPICZMV27OSTwx0zYd3tcBoTcXvlp0yRpil4xeMNLr-rshsIFwkWIyL-mSt3rrW2pxMjw__)
7. Click on done editing. This will automatically create the map for us.
8. Clicked on save, Name = windows Evnt Attck Map, added to the resource group  and saved.
9. I as well have the oppotunity to edit and apply settings based on how I want the map to be displayed such as colour type, metric label, country. The attack map keeps changing overtime and will as shown below, I have the attack map of my VM after 8 hours. ![GitHub Logo](https://media-hosting.imagekit.io//00b0d608e7974e0b/map%20attack.png?Expires=1835669668&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=A6fwyfHahdziBjSm5DMfynusuXiCSXu4wp7qmzccWvuxSD7wikheXZi0eYnhUTt26D32dPgGnIESgBjbV~i0OEVjSj3o5~3HFiGkR9wBKulb5LEyDPC6MBenWlNAmCEsLD6Ra6~zSXJyzDdhjfVJLT6OgaZorZydiKJtlcT1QbCXEmhqlc7hKImLK8cK1i8hz9tbfny~SGQDMb9XUjHwRLRAwamQVm0PPnUAgostFnNdA31gcW--icTL0m0Du4ZiVYJ6oeAWq9UMz2-5ToGbSW~oOCRAIBqO105qcP-9kfVrd2JZo5u3BBZG5u5oCBD6osKlMNNwVwXHgQfVce76ew__)

# Metrics Before Hardwening/Security Controls

| StartTime 2025-03-05 19:43:26
| StopTime  2025-03-06 19:43:26
- SecurityEvent Windows VM  5699
- Syslog   0
- SecurityAlert   0
- SecurityIncident   0
- AzureNetworkAnalytics   0

## Steps to Hardening
1. Security Posture Recommendation
- Configured windows server to use communication Protocols: To protect the privacy of information communicated over the Internet, your servers should use the latest version of the industry-standard cryptographic protocol, Transport Layer Security (TLS). TLS secures communications over a network by using security certificates to encrypt a connection between machines.
- Installed Guest Extension on VM: to allow Microsoft Defender for Cloud to proactively attest and monitor the boot integrity. Once installed, boot integrity will be attested via Remote Attestation. This assessment applies to Trusted Launch and Confidential Windows virtual machines.
- Enabled Azure Backups: Azure Backup is a cost-effective data protection solution native to Azure that safeguards data on Azure virtual machines. It creates recovery points stored in geo-redundant recovery vaults, allowing for the restoration of either the entire VM or specific files.If Azure Backup is not enabled, data loss may occur without the possibility of recovery, posing a significant risk to business continuity and data integrity.
- Closed management ports
2. Regulatory Compliance based on ISO 27001:2013 recommendations
  - password age set to specified number of days with 30 days
  - Audit Windows machines that allow re-use of the passwords after the specified number of unique passwords
  - Strong Password Policies: Enforcing a rigorous password policy mandates the use of complex passwords that incorporate uppercase and lowercase letters, numbers, and special characters. This approach significantly enhances security and diminishes susceptibility to brute force attacks. Geographical Restrictions: Block or restrict access based on geographical locations that do not correspond to your organization's operational areas.
  - Account Lockout Mechanisms: Implement account lockout policies that temporarily disable accounts after a set number of failed login attempts, deterring repeated brute force attempts.
3. Enabled Windows Security firewall state for Domain Profile, Private Profile, Public Profile.
4. Configured NSG to block all traffic with an exemption to administrators workstations.

![GitHub Logo](https://media-hosting.imagekit.io//e6a427c359cd460d/Hardening%20result.png?Expires=1835904953&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=EVZJKNjoXMobwoDl9Vei8~SCYPQs8YdkIrFzxVS2RVKM2jHgB0qA-Rbw7y2qHYJnNqXcZ6jfGvPPY73Xwua3Xm-jUsq-dn-4H9J31om0dzz3earJk0zWbLhwhYKdP8qYkPNcQX6Pj966BviK1TjxLJdmc~RuTj77bhe3Z4J-b6JaL4LJo6RZ5OYwumXTeTjDsSa6w5UoY1ZzXCigS1VYihSPvQwferF9P9bHaHCml9t4CaujA8cETDKWhyye0WyLKMi7fuqV9ZHw1NQAKxvTitjxcDoXCikZEm3L6WVDJHd4-qRPIm1uiDRB8zh3OxdrnDNtFmV8qh3wB3qRZO-UXQ__)

### Conclusion

The project is important in the world of cybersecurity in the cloud environment. The project took place with Microsoft Azure, ingesting multiple logs into Log Analytics Workspaces. Alert and incidents was generated with the help of microsoft sentinel that was deployed.
The project was in two faces. The first face is where the environment was left unprotected and the second phase where the a security control was put in place which later show a significant reduction in the number of brute force attacks.
Therefore, the project demonstrated the importance of continous monitoring and adaptation responses to user activities and devices in our organization.
