<h1>Configuring a Firewall Lab</h1>



<h2>Description</h2> 
In this lab, I created two Virtual Machines (VMs): one with the pfSense ISO image and one clean Windows 10 host. I created a NAT network and assigned both the Windows and pfSense VMs to it. However, I configured adapter one on the pfSense VM as a bridged connection to be on the same network as my host computer, and adapter two for the NAT network, corresponding to the WAN (Wide Area Network) and LAN (Local Area Network). I then installed and configured the pfSense VM, and accessed the admin web portal from the Windows 10 VM. This is where the majority of the lab was focused. It's important to note that, because this is a lab environment, I had to allow RFC 1918 addresses (private IPs) into the WAN, since both my LAN and WAN interfaces used private IPs. This setup is not recommended in a production environment. I installed Suricata and Zeek packages on the firewall for enhanced logs and network visibility. Lastly, I configured a basic block list of insecure and common ports and protocols that attackers often leverage for initial access and persistence. To ensure the rules I configured were effective, I attempted to access a website using HTTP. The connection was blocked as expected, but when I disabled that firewall rule and revisited the site, it loaded correctly. This was an excellent hands-on lab for SOC analysts to learn how firewalls operate and to configure basic rules.

<br />


<h2>Languages and Utilities Used</h2>

- <b>pfSense</b> 
- <b>Windows CMD</b>
- <b>Linux Terminal</b>
<h2>Environments Used </h2>

- <b>Oracle Virtual Box for all Virtual Machines</b>
- <b>Windows 10 </b>
- <b>Linux Server </b>
<h2>Lab Overview</h2>

The first step in this lab to ensure connectivity between VMs and my host machine by creating a NAT Network so the virutal machines would be on the same network.<br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/c48c1de8-6faa-4056-a14f-cf20353bbadb" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
Next, with the pfSense VM (virtual machine), I configured the first adapter to be a bridged connection so it would recieve an IP on the same network as my host computer and the second adapter with Nat Network for the respecticve LAN and WAN netowrks.
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/50021238-49ce-4768-bcb8-508c8cf3696c" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/bc159ec4-699e-4862-a2c0-0f532acce7ec" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
Once the network configuration within Virtual Box was done, I installed and configured pfSense making to sure to attach the right adapter to the correct correct network. <br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/646041ca-8a09-4dc0-ba4e-d6960c64a867" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/affdc6b1-9782-43ba-a47f-48fb4966ccd3" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/45af91ad-df8d-45b7-a00d-8b9105b007b9" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
With a clean Windows 10 install, I configured it to also be on the NAT network with pfSense so it can access the admin page and test the rules.<br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/11936464-3cb1-4ed5-af58-12f8ff3662a7" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/c125b776-bce3-4efb-adf4-db8c3e3fc689" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
Upon entering my default gateway IP into a web browser which is the LAN of the fireall, I was brought to the pfSense page where I begun configuring the firewall. An important note: for this lab to work because I have a type 2 hypervisor, my LAN and WAN were both RFC 1918 (private IP address ranges) which made me uncheck the box of blocking private networks from entering via WAN which is not something to do in a production environment, but necessary here.<br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/7d43c4c7-d701-4b19-ab72-ecba6a7578a2" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/f008d521-7db1-4b2f-8a66-0764f56068b1" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/326bd4ff-1535-4867-8d93-0bfcf9878a03" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
With the firewall now installed and configured, I installed two packages on the firewall, Suricata which can perform as an Intrusion Detection/[Prevention system and Zeek as a lightweight traffic analyzer. <br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/45ef1629-abed-4779-8f1b-c4c9102a427f" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/cba55531-8228-4151-83b4-2efada5dd3de" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/472a6cf5-b20b-445f-8849-403c10deb8d5" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
Next begun the process of making some basic firewall rules allowing traffic within the LAN and blocking many unsecure protocols and ports in the WAN such as Remote Desktop protocol, Telent, and Server Message Block SMB. The protocols either transfer data in plain text, or are common targets for attackers, unnecessarily increasing the attack surface. <br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/0f492cb0-5c32-4c75-a478-e688c2c3eb1a" height="100%" width="100%" alt="pfSense Lab"/>
<img src="" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />
To test the firewall rules, I tried to access a website using http. The connection was blocked and the site did not load. However, when I went back to my firewall rules and disabled that rule, I was able to connect to the site confirming the rules to be working properly.<br/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/c4d060e7-32d1-4d55-857b-e806084d6653" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/9a7bf8c7-c3d5-4bbb-abb5-ab77396dfb99" height="100%" width="100%" alt="pfSense Lab"/>
<img src="https://github.com/KirkDJohnson/Configuring-A-Firewall-Lab/assets/164972007/8d9e6bd3-47c5-497e-9b5e-32bac03a91fc" height="100%" width="100%" alt="pfSense Lab"/>
<br />
<br />

<h2>Thoughts</h2>
This hands-on lab was highly insightful as it allowed for experimentation and self learning, unlike CTF walkthrough labs. I had some prior experience with networking principles from previous labs, particularly the Active Directory Splunk lab, so the initial assignment of IP subnetting was straightforward. Additionally, the pfSense installation went smoothly; I understood that both LAN and WAN needed to be private IPs, which made this lab somewhat different from a production environment. However, configuring the rules and packages was highly beneficial. Despite my basic knowledge of firewalls from working with Cisco labs, installing and configuring one on a Windows host and observing the real-time impact of blocking HTTP traffic was very enlightening. This lab provided valuable experience, which is primarily used by security engineers, but it is also important for SOC analysts to understand how firewalls operate.<br />

