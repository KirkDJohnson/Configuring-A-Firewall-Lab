<h1>Configuring a Firewall Lab</h1>



<h2>Description</h2> Text
<br />


<h2>Languages and Utilities Used</h2>

- <b>pfSense</b> 
- <b>Windows CMD</b>
- <b>Linux Terminal</b>
- <b>Sever Manager</b>
- <b>Active Directory Domain Services</b>
- <b>Splunk Enterprise and Universal Forwarder</b>
- </b>Splunk Search Processing Language (SPL)</b> 
- <b>Crowbar and Atomic Red Team</b> 

<h2>Environments Used </h2>

- <b>Oracle Virtual Box for all Virtual Machines</b>
- <b>Windows 10 </b>
- <b>Linux Ubuntu Server </b>
<h2>Lab Overview</h2>

The first step for in this lab for this to work was to create a NAT Network so the virutal machines would be on the same network.<br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/c48c1de8-6faa-4056-a14f-cf20353bbadb" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
Next, with the pfSense VM (virtual machine), I configured the first adapted to be a bridged connection so it would recieve the an IP on the same netowork as my host computer and the second to act as the WAN (wide area network) and adapter two on for the LAN (local area network).<br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/50021238-49ce-4768-bcb8-508c8cf3696c" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/bc159ec4-699e-4862-a2c0-0f532acce7ec" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
Once the the networking within Virtual Box was done, I isntalled and configured pfSense making to sure to attach the right adapter to the correct correct network. <br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/646041ca-8a09-4dc0-ba4e-d6960c64a867" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/affdc6b1-9782-43ba-a47f-48fb4966ccd3" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
With a clean Windows 10 install, I configured it to also be on the NAT network with pfSense so it can access the admin page and test the rules.<br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/11936464-3cb1-4ed5-af58-12f8ff3662a7" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/c125b776-bce3-4efb-adf4-db8c3e3fc689" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
Upon putting in the IP on my localhost, I was brought to the pfSense page where I begun condifguring the firewall. An important note: for this lab to work because I have a type 2 hypervisor, my LAN and WAN were both RFC 1918 ( private IP address ranges) which made me uncheck the box of blocking private networks from entering via WAN which is not something to do in a production environment, but necessary here.<br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/7d43c4c7-d701-4b19-ab72-ecba6a7578a2" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/f008d521-7db1-4b2f-8a66-0764f56068b1" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/326bd4ff-1535-4867-8d93-0bfcf9878a03" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
With the base firewall, not installed and configured, I installed two packages on the firewall, Suricata which can perform as an Intrusion Detection/[Prevention system and Zeek as a lightweight traffic analyzer, <br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/45ef1629-abed-4779-8f1b-c4c9102a427f" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/cba55531-8228-4151-83b4-2efada5dd3de" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/472a6cf5-b20b-445f-8849-403c10deb8d5" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
Next begun the process of making some basic firewall rules allowing traffic within the LAN and blocking many unsecure protocol and ports in the WAN such as Remote Desktop protocol, Telent, and Server Message Blcok SMB. The protocols I are either unsecure in that transfer data in plain text, or are common targets for attackers, unnecessarily increasing the attack surface. <br/>
<img src="" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
To test the firewall rules, I tried to access the site <br/>
<img src="" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
Text<br/>
<img src="" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
Text<br/>
<img src="" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />


<h2>Thoughts</h2>
txt
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
