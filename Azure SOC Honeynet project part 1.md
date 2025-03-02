![GitHub Logo](https://media-hosting.imagekit.io//c1126e17a4544e46/topology.png?Expires=1835508990&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=cOaV72tA1bS~9hIb0xNR-INXVTYJHNrFWzA-dh-dzsy2C32~bEZN5zBP5G5guFIK94rFrD4DTuy9a0sZXENs9fwNMu3-aWJ2LiWISTbB~hpRZSqJFiBbFq5h8-N9pC5KBoaROIYKxKzxpnYebG0Ldmzg1BczlQ~JzzZDCj9a5EZozwrraU~fnDUzb4GqejwFohshmfQ67bVnTJq1-emF1qsCTRyWb2sek~ZtiBvEfB0fbIEPDd1g5VB6hw9YR237Y~XcvXwMXeYDnlJE82ekSFTsH~ua~ZK-N29fimBdIi3iTJf7UNeZkljdBvX0CDUciULDJ5DNFXAKP672vAX09A__)
# Honeynet Project
My topology contains Azure subscription, followed by a Resource group which is in form of cloud  folder for my resources, Vnet, created a vm and attached it to the virtual network and also make the Virtual machine enticing to attackers by turning of the firewall. Created Azure firewall NSG and will be completely open up as well as firewall from windows
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



