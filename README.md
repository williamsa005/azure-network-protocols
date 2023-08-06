<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this quick reference guide, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create our resources within Azure
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/ojoQRY0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Note: I check my establised resources to ensure I have properly created two seperate VMs  within one Vnet. 

  
  Create our resources in Azure:
  
1. Create a Resource Group
2. Create a Windows 10 Virtual Machine (VM)
   
   a.  While creating the VM, select the previously created Resource Group
   
   b.  While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet
   
3. Create a Linux (Ubuntu) VM

  a. While creating the VM, select the previously created Resource Group and Vnet.
</p>
<br />

<p>
<img src="https://i.imgur.com/SKfDoC9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Note: I have sent a ping request from VM1 to VM2's private IP address. I filtered Wireshark for ICMP traffic only
  
Use Remote Desktop to connect to your Windows 10 Virtual Machine:

4.  Within your Windows 10 Virtual Machine, Install Wireshark
   
5.  Open Wireshark and filter for ICMP traffic only
   
6.  Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
   
    a. Observe ping requests and replies within WireShark
    
8.  From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark.
</p>
<br />

<p>
<img src="https://i.imgur.com/lB56rYV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Note: I filtered WireShark to monitor SSH traffic. I also SSH into VM2's system via PowerShell.

9.  Back in Wireshark, filter for SSH traffic only
    
10. From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
    
    a. Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
    
    b. Exit the SSH connection by typing ‘exit’ and pressing [Enter]

</p>
<br />
