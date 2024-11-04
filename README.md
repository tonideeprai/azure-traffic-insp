<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Inspecting Traffic Between Azure Virtual Machines</h1>
This lab shows how I observe the traffic of virtual machines in the same network environment via Azure. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
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
  <img width="90%" alt="Screenshot 2024-11-04 at 1 34 31 PM" src="https://github.com/user-attachments/assets/2e9705da-b058-4d48-b1a0-13dafe1ef87a">
</p>

- I retreive the private IP addresss of of Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM
  <p>
  <img width="90%" alt="Screenshot 2024-11-04 at 1 42 50 PM" src="https://github.com/user-attachments/assets/db6ab769-3b01-4a61-9a1d-6944cafe4fbd">
  </p>
  <p>
  <img width="90%" alt="Screenshot 2024-11-04 at 1 48 05 PM" src="https://github.com/user-attachments/assets/39cce970-8695-4db1-8209-19d4a44df29c">
</p>

- After entering the ping command
  <p>
  <img width="90%" alt="Screenshot 2024-11-04 at 1 49 47 PM" src="https://github.com/user-attachments/assets/11622867-3465-47cf-b3c9-b9cd655f815b"></p>
    <p>
  <img width="90%" alt="Screenshot 2024-11-04 at 1 50 54 PM" src="https://github.com/user-attachments/assets/926b90e9-f985-4a74-94f0-4ffc6f4dd5c9">
  </p>
<hr>
<h3>Observe SSH Traffic</h3>

- Filtering out only SSH traffic in Wireshark
  <p><img width="90%" alt="Screenshot 2024-11-04 at 2 03 14 PM" src="https://github.com/user-attachments/assets/026cd58f-338d-4a15-9601-3260d0fbb188">
</p>

- Connecting to the Ubuntu machine via its Private IP address in Powershell using SSH protocol
   <p><img width="90%" alt="Screenshot 2024-11-04 at 2 14 01 PM" src="https://github.com/user-attachments/assets/f7b1f634-5910-4b75-983b-f15ccac87afa">
  </p>
   <p><img width="90%" alt="Screenshot 2024-11-04 at 2 15 37 PM" src="https://github.com/user-attachments/assets/12a76104-dea6-44bb-b781-dfcc9f14ee41">
  </p>

- Checking VM's ID and host name
  <p><img width="90%" alt="Screenshot 2024-11-04 at 2 21 14 PM" src="https://github.com/user-attachments/assets/a5a37704-b756-443a-a921-7578f19e4e0f">
  </p>

 - Inspecting the captured packets and their data
    <p><img width="90%" alt="Screenshot 2024-11-04 at 2 22 48 PM" src="https://github.com/user-attachments/assets/5d0d7c21-eeb3-46e7-89dd-c9e0140c4149">
  </p>

- Exiting the VM
  <p><img width="90%" alt="Screenshot 2024-11-04 at 2 26 16 PM" src="https://github.com/user-attachments/assets/84c7552a-711d-439b-a53f-01810198dc08">
</p>

- Inspecting the traffic in TCP port 22 (SSH common port)
  <p><img width="90%" alt="Screenshot 2024-11-04 at 2 30 48 PM" src="https://github.com/user-attachments/assets/eb6b79ba-ec6f-4bad-bf93-fe84d41c33d4">
  </p>
<hr>
<h3>Observe DHCP Traffic</h3>

- Filtering out only DHCP traffic in Wireshark
  <p><img width="90%" alt="Screenshot 2024-11-04 at 2 34 37 PM" src="https://github.com/user-attachments/assets/5f6d3c21-e31e-4677-ae01-0794c9e3d217">
  </p>

- Writing a .bat file in Notepad to renew and release the ip address
  <p><img width="90%" alt="Screenshot 2024-11-04 at 2 42 12 PM" src="https://github.com/user-attachments/assets/d6465790-1ade-4c12-8a5a-4efcc35e2233">
</p>

- Running the .bat file in Powershell (run as Administrator)
- The .bat file will refresh your VM
  <p><img width="90%" alt="Screenshot 2024-11-04 at 2 48 11 PM" src="https://github.com/user-attachments/assets/5c8a6a3f-b621-46d1-ad99-67547de350ca">
</p>

- After running the file
  <p><img width="90%" alt="Screenshot 2024-11-04 at 3 55 29 PM" src="https://github.com/user-attachments/assets/98725487-a552-42ab-829d-9da6c6123f5b">
</p>

- Observing the packets captured
  <p><img width="90%" alt="Screenshot 2024-11-04 at 3 58 42 PM" src="https://github.com/user-attachments/assets/32e524c8-b573-4a1d-ba91-671f141c1663">
</p>
<hr>
<h3>Observe DNS Traffic</h3>

- Filtering out only DNS traffic in Wireshark
  <p><img width="90%" alt="Screenshot 2024-11-04 at 4 02 44 PM" src="https://github.com/user-attachments/assets/6beabeb5-c317-4274-846a-df569fcd51ce">
</p>

- Using `nslookup` command in Powershell to "look up" a website's IP address
  <p><img width="90%" alt="Screenshot 2024-11-04 at 4 10 06 PM" src="https://github.com/user-attachments/assets/ee1cee7f-7442-48eb-bf32-a44b2bf09387">
  </p>
  <p><img width="90%" alt="Screenshot 2024-11-04 at 4 10 42 PM" src="https://github.com/user-attachments/assets/a3dfb1da-3b84-479c-851e-f31475ffe730">
  </p>

- Observing packets captured in Wireshark
  <p><img width="90%" alt="Screenshot 2024-11-04 at 4 12 41 PM" src="https://github.com/user-attachments/assets/1faa5e0f-e8b2-4ce4-ba02-bf0a78babae3">
</p>
<hr>
<h3>Observe RDP Traffic</h3>

- Filtering out RDP traffic (TCP port 3389) in Wireshark
  <p><img width="90%" alt="Screenshot 2024-11-04 at 4 16 21 PM" src="https://github.com/user-attachments/assets/202a8a5f-7712-4412-911d-fa6b5c5ce904">
  </p>

- Observing the traffic
- RDP Protocol is constantly "listening"
  <p><img width="90%" alt="Screenshot 2024-11-04 at 4 17 56 PM" src="https://github.com/user-attachments/assets/b57771ef-471e-4e67-8893-63fbbcea1f00">
</p>
  
  
  
 

