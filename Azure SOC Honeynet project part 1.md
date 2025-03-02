![GitHub Logo](https://media-hosting.imagekit.io//c1126e17a4544e46/topology.png?Expires=1835508990&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=cOaV72tA1bS~9hIb0xNR-INXVTYJHNrFWzA-dh-dzsy2C32~bEZN5zBP5G5guFIK94rFrD4DTuy9a0sZXENs9fwNMu3-aWJ2LiWISTbB~hpRZSqJFiBbFq5h8-N9pC5KBoaROIYKxKzxpnYebG0Ldmzg1BczlQ~JzzZDCj9a5EZozwrraU~fnDUzb4GqejwFohshmfQ67bVnTJq1-emF1qsCTRyWb2sek~ZtiBvEfB0fbIEPDd1g5VB6hw9YR237Y~XcvXwMXeYDnlJE82ekSFTsH~ua~ZK-N29fimBdIi3iTJf7UNeZkljdBvX0CDUciULDJ5DNFXAKP672vAX09A__)
# Honeynet Project
My topology contains Azure subscription, followed by a Resource group which is in form of cloud  folder for my resources, Vnet, created a vm and attached it to the virtual network and also make the Virtual machine enticing to attackers by turning of the firewall. Created Azure firewall NSG and will be completely open up as well as firewall from windows
1. Created the ressourse group that will group all my resources
2. Created virtual network oluwatosinvm-vnet in the same region and attached to SOCRG
3. Created the virtual machine. attached the vVM to SOCRG and VNET oluwatosinvm-vnet
4. Opened the VNET Firewall and deleted the default inbound rule for RDP that was listening on port 3389 ![GitHub Logo](https://media-hosting.imagekit.io//01a2891a15854259/remove.png?Expires=1835533577&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=f3Xik1LMNR7hlotRG3RbRdPkzul6u2-Sb4KX1hnlRF59-WhymOIJR2QofZ8u2pdcXdJxbYJp7UosMqBACBugeRBu4GJ~TPawFn6Mx2Ht-oEevXhT-k51NDEeuLpp~u1cirq-4QmhwZEkXFsOPrKzCLpiV2qOoNo59nd8zlf2glDM5J5K24yetqbBGaP80pCaJSwBbYEsepgYWrNlDORQ5kxOGrLbvIpYjp3VWyYYyY-AlzMzTChnKVir2UeMmA2KPq1lthhOJ5aY~-OkRT0r7g6NCEzHmLfQZo1jhT8d75guNHHS~SqcBbdD9WtL4Ol9v39p6X3YWiMPGGOvTvXFIQ__)

## Create Inbound Rule on Nsg
5. Created another new inbound rule by going to settings, clicked on inbound security rules
6. Click add.
7. Set Source port ranges to any (*).
8. Set destination port range to any (*).
9. Set priority to 100 because the lower the priority, the sooner the rule value get evaluated. I left the priority valuea at 100 because it will be the lowest priorty on the list as shown in the picture below.![GitHub Logo](https://media-hosting.imagekit.io//80808ef7775348fe/nsg.png?Expires=1835534171&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=bQvRb-Q4LflFjmo3tfe7GQaevUjlAOyUQe60YJLVUw7TZSnmWzFvtUUNGqd5IcxVtgMSGWaT9lfVtoYjAOQv-YsZpFSZ7Kc~RoNeJ2KUVymFtSnzPp3k4LDVHyzeNDXNxc0tRYZD60IW1WPAb1yOYnjtoQaDGFxgJxyjUkIQ2VrksFTNXK8NpG6lq7oGcTqxBxcqudAfN810j2At3~a6Ce6dkRXtRN5SXeVyjdY9~QtSGS~ADJphdOGq5pPWmF6nmYTOZhJolfOpC5ErtcPJ5-Mw2BPYXp0~1cEGT~5H5IvJZvuZi4weRW6srEgSDm-AUnVK9oaR-tumr9aPWMTV~w__)
10. Named it DANGER_AllowAnyCustomAnyInbound in order to make the name more attractive

## Disable Internal Windows Firewall from the VM

