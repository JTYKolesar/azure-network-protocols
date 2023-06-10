<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
This tutorial goes over how to observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Setup 2 Virtual Machines within Azure:
  - Virtual Machine #1 (Windows 10)
  - Virtual Machine #2 (Linux Ubuntu) -- using same Resource Group and Vnet as VM1
- Use Remote Desktop (RDP) to VM1 and install Wireshark.
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<h3>Creating 2 Virtual Machines</h3>

- In the Search Box at the top header, type and select "Virtual machines".
  - If "Virtual machines" is already listed on the front page, then you can simply click on it, rather than manually searching.
- Click "Create", then select "Azure virtual machine".
<p align="center">
<img src="https://i.imgur.com/tiC5aA4.jpg" height="80%" width="80%" alt="Step 1-1"/>
</p>

- Name your Virtual Machine anyway you want (this example uses **VM1**).
  - Resource Group is automatically given a name when naming the Virtual Machine, but you can change it if you wish (this example uses **VM1_group**).
- Change the Region that best suites your location (this example uses **(US) West US 3**).
- Change the Image to a Windows OS (this example uses **Windows 10 Pro, version 22H2 - x64 Gen2**).
- Make sure the Size is adequate enough to run this server (this example uses **Standard_E2s_v3 - 2 vcpus, 16 GiB memory**).
- Create a username and password of your choice (this example uses **winuser**).
- Skip everything else and click "Review + create".
  - IF there is a Licensing Checkbox at the end, make sure that is CHECKED!
- If Validation passed, click "Create".
<p align="center">
<img src="" height="100%" width="100%" alt="Step 1-2"/>
</p>

_Essentially repeat the same steps from creating the other virtual machine, but using Ubuntu (linux):_
- Set the Resource Group to the same as VM1 (this example uses **VM1_group**).
- Name your Virtual Machine anyway you want (this example uses **VM2**).
- Change Image to Ubuntu Linux (this example uses **Ubuntu Server 20.04 LTS - x64 Gen2**)
- Keep the size the same as the Windows VM (this example uses **Standard_E2s_v3 - 2 vcpus, 16 GiB memory**).
- Change the Authentication type to "Password", and create any username (this example uses the username **linuser**).
- Once done, press "Next:" until you reach "Networking" (or simply click the Networking tab".
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- Make sure that the Virtual Network is set as the same as Windows VM (this example uses **VM1-vnet**).
- Set the Public IP to whatever it has automatically assigned to (you might have to confirm the selection).
- Then press "Review + create".
- If Validation passed, click "Create".
<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

<h3>Connecting to VM1 and Installing Wireshark</h3>

- From Azure Portal, go to VM1's Overview page and copy the Public IP address.
- Press the Windows Key/Button, then type in "Remote Desktop Connection" (RDP).
- Input the IP into RDP and click "Connect" (this example uses **20.171.65.41**).
- Enter the login credentials for VM1, then click "OK" (this example uses **winuser**).
- When the Certificate Error prompt appears, just click "Yes".
- As it boots up, you can disable all privacy settings when prompted, then hit "Accept".
<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- On VM1, open Microsoft Edge (or any internet browser), then go to the Wireshark download page.
  - You can simply Google Search it, or copy the link shown.
- Click on "Windows Intel Installer" to start downloading the executable.
- Once downloaded, click "Open file" to run the .exe file (you can also find this inside your Downloads folder within Windows Explorer)
<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- The installation prompt will appear, hit "Next".
- When the installation prompt appears, leave everything by default and keep pressing "Next" until you start Installing.
- If any agreement prompts appear during installation, just agree to them and click install (without checkmarking anything).
- After all installations are complete, click "Finish".
<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

<h3>Observe ICMP Traffic using Wireshark</h3>

_Note: The 'ping' tool within Command Prompt (cmd) / PowerShell uses protocol ICMPv4._
- Minimize the virtual machine to the Azure Portal.
- Go to VM2's Overview page and copy the PRIVATE IP address (this example uses **10.0.0.5**).
- Return to VM2, press the Windows Key/Button and seach for "CMD" or "PowerShell".
- Type in `ping -t <Private IP address>` (this example would use command **ping 10.0.0.5**).
  - On Wireshark, you should be able to see the results of the sent and received packets.
<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.

<br />
