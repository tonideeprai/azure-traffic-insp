<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Inspecting Traffic Between Azure Virtual Machines</h1>
This lab shows how I observe the traffic of virtual machines in the same network environment via Azure. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 Pro (21H2)
- Ubuntu Server 20.04

<h2>The Set-Up</h2>

Within Azure, I created two virtual machines in the same virtual network/resouce group. One Windows (Windows 10) and one Linux (Ubuntu).

The Windows VM has <a href="https://www.wireshark.org/">Wireshark</a> installed and will use Command Line/Powershell to communicate with the Linux machine.

<h2>Actions and Observations</h2>
<h3>Observe ICMP Traffic</h3>
<p>
  
</p>
