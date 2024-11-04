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

- In my Windows VM, I open Wireshark and start capturing packets. I filter out to see only ICMP traffic
<p>
<img width="80%" alt="Screenshot 2024-11-04 at 1 34 31 PM" src="https://github.com/user-attachments/assets/2e9705da-b058-4d48-b1a0-13dafe1ef87a">
</p>

- I retreive the private IP addresss of of Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM
<p>
  <img width="90%" alt="Screenshot 2024-11-04 at 1 42 50 PM" src="https://github.com/user-attachments/assets/db6ab769-3b01-4a61-9a1d-6944cafe4fbd">
</p>
<p>
  <img width="90%" alt="Screenshot 2024-11-04 at 1 48 05 PM" src="https://github.com/user-attachments/assets/39cce970-8695-4db1-8209-19d4a44df29c">
</p>

- Results after the ping command
<p>
  <img width="90%" alt="Screenshot 2024-11-04 at 1 49 47 PM" src="https://github.com/user-attachments/assets/11622867-3465-47cf-b3c9-b9cd655f815b">
</p>
<p>
  <img width="90%" alt="Screenshot 2024-11-04 at 1 50 54 PM" src="https://github.com/user-attachments/assets/926b90e9-f985-4a74-94f0-4ffc6f4dd5c9">
</p>

  
 

