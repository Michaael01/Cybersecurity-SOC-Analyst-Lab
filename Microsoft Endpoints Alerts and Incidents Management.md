# Alerts and Incidents Management
An incident is a collection of correlated alerts that tell the story of an attack. Microsoft Defender XDR automatically aggregates malicious and suspicious events found in different device, user, and mailbox units on the network. Grouping related alerts into an incident gives security leaders a comprehensive view of an attack.
1. Go to Security.microsoft and click on Incidents and alerts. The picutre shown below is the current view of incidents and alerts in my subscription which includes alerts generated other Microsoft defener subscription such as defender for cloud, Sentinel etc. but filtered to endpoint incident alerts.
_note: from the picture you can see the Incident name, sevrerity, investigation state, impacted assets, Active alerts, detection sources etc. from the incidents header_.
![GitHub Logo](https://media-hosting.imagekit.io//e6ab57b3dc4149ee/powershell%20endpoint%20incident.png?Expires=1835438079&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=Xyidj0uFEVcFhGHdwJVmA0PKbjNbTT79L0ByRm0YfGpZJbVYqj5oBfOE5jkTm-eTgT3dLrawRi-cbUtMG0UoPR1KQ8C2~2U11gxWtPRv9oO6KVGFdSbPtDzR9TVONkYW2W1HSssPKU00T6qpM9DA4YwvvG4ZXo2XE~owa-2qGL7o4cY1vyKDcHdExnks-puUhTXJs~UhQjK8ubIMLsBXyL14ONaA-PggNaA0kpdcyMesbMufrdkssYqWDn0lmS0rVz4G4tOzzPf~5719C~NoGE9Y5rf0koN1Bz1QGtNyhRD-CEquKv8zLikpD7ObsAje-ZNH2Amiv0OHSRWJ-igxTg__)
2. Click on any alert in order to know more information about the alert
3. Click on open incident page
## Investigating Alert
From the the incident page:

1. Click on manage alert on the top right corner to change the status of the incident, assign it to a user, and put a classification for example, phishing, malware, multi staged etc. and save. This will make other team member that the incident alert is being investigated by Oluwatosin.
![GitHub Logo](https://media-hosting.imagekit.io//e5f552b3fdb24779/incidents%20and%20alert.png?Expires=1835442720&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=zxhRs-xd3teZ8nwdh3I2rzc5TgYN2WwpVVAwUOYrrBw~Meuik~1bcTIBpS-2TwXp9jVhEazM36PdVKNm2usTFKqE5UTS4zZldFds0GIlsMbaIiHEYu~FzCuVmBzNWidaCHsjMVw0BbxaElPNAP23qMOvmZ6snh~01mVGnOOXgB4~ULnAbUjBuMpI4cEnFSl~Uu7cWmZuYXWH8iLsX1Ehl2cGHhb4O45XZZhB31kN8-n72i1fscyPqZ-LxckbeYbTjqQG~kxzj8C042AISKkJQbIL4aAhmnlzia~Q-WTGpeoD1ebgUjUYzur-~EX6y2wHu7JCwg~xhFHrgbkvKzyFmA__)
On the incident page we can see the evidences that will give more information about the incident alert such as the ip address and the powershell script that was aun
2. Scroll down the right side of the incident page to Evidence
![GitHub Logo](https://media-hosting.imagekit.io//11bcbb935f184b06/evidence.png?Expires=1835444315&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=FtuLcPehkGvzsjgAuImdg8mZZIvlbhBwSKDUlzTeQJG-g-3mWm9GfGsnuh3b8GeE6J-x2RxY3H7xSbE2QN7Vf~WbRyzVvM-MqqjNaAvychJvMi~eYSAv0PIzaEq8nFDDK1OEs6yGgdw8dyTANO018drbycK9ddk1dTt54O9hiElcrdEaLjIz8e9hUxl8zmNk2mwqIGUJrJCKQhbrMJ-cJhS~VQL5RsZXOgiEElkxWFhgqaC5mOZIUNOhMbIieOvzNag6k9WVFtzIFcgb-d9dd0nK2rVbaAojNP5jfrL7Rp6DUWjmsXlR7iZ3qrIcCZueV9Ftb9ngCyuR8cjGoNeENg__)

3. Scroll down to view the active alert section. This will give us additional information such as the numbers of the active alerts, devices involved in this alerts, and users.

### See in Timeline
It is important to investigate with see in timeline in order to see all what had previously happened on the device. From the top right corner of the incident page, we have manage alert, See in timeline and Tune alert
click on See in Timeline to see all the processes on the device.

#### Tune Alert

A false posive alert can be supressed from tune alert. It is also known as alert suppression. A proper settings can be made if confident that the alert is false positive so that the alert will not come over and over again. ![GitHub Logo](https://media-hosting.imagekit.io//420a115c4d9c4a8f/tune%20alert.png?Expires=1835465095&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=Lms-M9RlMZAK6ngt1KC83lCJeN9oL4WBeT0EYBr6wnh-sjJXBI~77Z3MubE1KRIXsQiC45PazL3pdE1zqH~l05SgMXhnBsl3jT0pnKLY5UCrLBQylDBYEos9dnsBJegpdaQQ5sO8h0vuuoO5b4DxHHwHYrCx4fAyiblTv~1SSbMJ3iWTydLpxYoin5rk3rOUS5s65LIF-lZ4hIAR3ECL1Py~qm~iAwSpCX3fU3WHiZmYXPc9~oaaEHYI0jIP3eMkkUC38G1v0-c7lAKL7q~FxA-6CpThDcEOVdLoELFyWpklwl7oeERacBcDFDk0wy9PyDfCOXdEbVuMweJG8Fdxig__)

#### Process Tree
The process tree console is located inside Alert Story as shown the picture below. The alert story displays all assets or entities related to the alert in a process tree view. 
- The Process tree displaysthe actual time each powershell script was ran.
- If I click on any of the powershell, it will display more information about the type of script that was ran in powershell.
- process tree give information such as the path where for example a malware is located.![GitHub Logo](https://media-hosting.imagekit.io//e6ab57b3dc4149ee/powershell%20endpoint%20incident.png?Expires=1835438079&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=Xyidj0uFEVcFhGHdwJVmA0PKbjNbTT79L0ByRm0YfGpZJbVYqj5oBfOE5jkTm-eTgT3dLrawRi-cbUtMG0UoPR1KQ8C2~2U11gxWtPRv9oO6KVGFdSbPtDzR9TVONkYW2W1HSssPKU00T6qpM9DA4YwvvG4ZXo2XE~owa-2qGL7o4cY1vyKDcHdExnks-puUhTXJs~UhQjK8ubIMLsBXyL14ONaA-PggNaA0kpdcyMesbMufrdkssYqWDn0lmS0rVz4G4tOzzPf~5719C~NoGE9Y5rf0koN1Bz1QGtNyhRD-CEquKv8zLikpD7ObsAje-ZNH2Amiv0OHSRWJ-igxTg__)

# Possible Resolution

## Missing KBs
This will allow us to check if there is any missing patches on the computer. This can be done by:
- Go to assets and click Devices
- Click on the machine that is being investigated which is win-dt7hjifjncb in my case
- Click on Missing KBs. In my case, it looks fine. ![GitHub Logo](https://media-hosting.imagekit.io//ed0d6f9c908545e7/Missing%20KBs.png?Expires=1835468257&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=t5vrqofrtiRwnznJqicwXwgdF7zktbmoE3q7QSZhelkocTY3ceR-u0E3jynuDzfDqlixkolFLC6uTm38z0krZHmBS5REylPMInlaW7ZAI1dQNWi2WOcEFWTl89lIIgqjelqQ4AU7MXepHh6kNNUTEp-0lQyVH1Zri4q4AygeQ~3JWFfJLl4EpeLU~AYdVNAwjVwM5I6h6pzHLGTvcY89nVoRAUYRV2K4oehmeiL0MFjCapPd5FmY0puegcJhLIdoUb0tLCuA~cIqD594v382psC01aJJzlESvVphAiw6l19l53Ok0uty7QrIhnhz8RSSCj0Gnary0rdxoZgKVybX7g__)

### More Actions
- As shown in the previous image, click on the three (...) from the top right corner to view more important task. such as
- Run Antivirus Scan: This action will update my Windows Defender Antivirus definitions and scna the device. you can either perform a full scan or a quick scan,
   - Wrote (investigation on the way) in the commecnt section, clicked on confirm. ![GitHub Logo](https://media-hosting.imagekit.io//3b447dd651aa49cb/scan.png?Expires=1835468936&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=cf9dqqVMqQYzvxvqPIaGFNgOc9-Kg6Ql2-dlSMisOiyXwH8DWZ0Aql8L5v6H2PBQS7g1lCtQOao1~FtaW5Nbpp3edc1KXjj5O3F89vHsyNbU2RrUqvGpvWMfOPZtylVDg5C~IhR4dQWl-dNIivPsXfmsm76K6Q~dmDPaoriWmrIZrG-AQRHlaQpTv7iho8HaDXbpWO1gUJwzHVQa-7GcqXi7LRq19P5e2FfRKmR3BOYiJqliQGj4iP7VmtyD~GXIBTMzykCVHHSkhjWZI1E-0eT-I-rT87hys68W-67nyGz7NXfd2rKJguB6cLnlBoc6NchRPlM1nuxJYKNNprQO9Q__). ![GitHub Logo](https://media-hosting.imagekit.io//279b725028ac4681/scan.png?Expires=1835469236&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=vtvDJdqd6LICsd1TeE2CU501mSQ9Has~gbMBaGNVGhWSNuj-UsEUC8g0mKAPPQoJsjhn16sP6NkLolhjlplpFVoa8Q71wprE30FqvTUe6k-0Cj54MzWa4hEoKxHbn6Low7nCF60L3ijb2nCdgIDDELhGuuck058sTl-k6eeD20ABJ88Mf-eFz5QawFqSajsqmtHX6iPl9BV1OgoVahZvawjQyXXIjeNAherQVOqn3W-tWxVSWtj~m7VBD7dkrcwkyIH~iw~Va-xvTJRD9nQcI9hbkVpT1l9hnNCLyckMaHQXdFZrsAE0GBAeF3ORKQCzsPGat5OC8YlTwVqKqh-F4A__)
- Initiate Automated Investigation: This will go to every singl bit of the device to see if any process was left behind. To be sure that the device is clean from any other threats. ![GitHub Logo](https://media-hosting.imagekit.io//b2c21021b69441d1/automated%20investigation.png?Expires=1835470165&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=XKeWJEBbp1ZuUGEjjr89a45liA7iUEPagJG~yVSvi~RxcEejlcxiRBb9T9XnFbjjf2wQjz97p-7YhY6kc1lVkzYbNrm1LlIuJQcFVj4Ro2GxqccJtjWeLU3zU~TEztNOK3f27FnXA4Q-6Uh7yCD8I1My8i3Aw7G~m8-19Oxh0fIFT7pj5Fnj~PZ8bk9g-3rJsXgP46wwJBoE8ZYr1ZBg80tBitH5uofWUVcp-2gn04t1v9SJWBABmm~865ODYU~EKTDIniBquDAz2pxJCJPgH0B4TbOWe3oKNxL8ICITpR0KIIkTwuTXr~zABU8XrGwQVQJifU29fT9~fZbMJ3GN6g__)
- Isolate Device: If some threats are still available on the device or the current threat is someone how critical that could lead to further threats to other machine on the network, I will initate a device isotion as shown below. ![GitHub Logo](https://media-hosting.imagekit.io//4f5c29359aeb4ef2/isolated.png?Expires=1835471305&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=Ko8cOZsvkaQfxlkm05OJZwQvBG6BqeGSEyA~eUda3JCsoaq-AoWnDfwFHCu-7tuHF2PwyFP2IZ80tu8uOujR-sDPUHPybsyew3e07M3~GcTfz1-KCu04WqqDPIovZqs3CaER4dXFANfqhZgXtnfdyvUQc1rQAmgfgo6XUaJsP-fWLIlps0uTEJ7ETgJBfkgBXia4OESk5rLe5vn2xC31KrOe8slX4dVwmO6CnXJf4PRCgh3Ui1mRVee0Crrp12riNouxxO4-rrPHIY0QkdLjPgmz5u7IbsQqYQSq-kth46h0MGmPZ83kwl09ThI7zcB8aHRLIPOYjPCRtsxxXSdIKQ__)
  Here is the reaction I got from my isolated device which shows the device is not longer on the network. ![GitHub Logo](https://media-hosting.imagekit.io//3a7b747169264e32/effect%20of%20isolated%20device.png?Expires=1835471527&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=H4wLBkBDQy2nkYYsPBAv3BfCUxH01M1YMCmExvNPicF6OKytuzzNedcitosU0jAFSll3feuL-x2jwmS-CYnlslmJUQSa0H8E07s5ILH0oVh19~Y6NZ21EyatOKWmGOLpnJt8iYAgB1VshChSH1V6o-lNRjvS2eAakobOp3VV7fJdorcowqcNjpNe44wdGT-wXt0PmK8SRLMVEGmq0erKM8osUa~VwEy9oLEe1KEUhfXVuej6P4RLS-n1vkdv6tztlrwBn6prxShNeIuyyWSxymRDDh~4JHCAM-ErRonU~Rtat56EQJi7nlOpKBJO6B-~iuQpu7CtJDJ~pKxv0F0Z4w__)
