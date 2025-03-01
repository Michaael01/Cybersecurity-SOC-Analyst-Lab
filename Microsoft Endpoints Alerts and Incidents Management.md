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



