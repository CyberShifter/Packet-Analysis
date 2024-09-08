# Wireshark Packet Analysis

---

## Overview

In this project, I will be capturing and analyzing network packets over a Telnet session to demonstrate my understanding of traffic analysis and network protocols. This will showcase my ability to set up virtual machines, configure network settings, and utilize tools like Wireshark and PuTTY to capture and analyze traffic between systems.

---

### Tools and Software

For this project, I will be using the following tools and software:

1. **Oracle VirtualBox**: A powerful open-source hypervisor that allows me to run multiple virtual machines on my host system. I will be using VirtualBox to host both my Windows and Ubuntu virtual machines (VMs).
2. **Windows 10**: This will serve as one of my virtual machines (VM) within VirtualBox, running as an ISO image.
3. **Ubuntu**: Another VM running within VirtualBox, also using an ISO image. Ubuntu will be the target system for Telnet communication.
4. **Wireshark**: A widely used network protocol analyzer. I will use Wireshark to capture and inspect network packets transmitted between the Windows and Ubuntu VMs.
5. **PuTTY**: A terminal emulator that will allow me to initiate a Telnet session from my Windows VM to my Ubuntu VM for remote access and testing.

---

### Detailed Steps for Packet Analysis

#### 1. Initializing Virtual Machines

I begin by launching Oracle VirtualBox, where I have set up two virtual machines: one running **Windows 10** and the other running **Ubuntu**. 

![1](https://imgur.com/MnAcRLX.png)

---

#### 2. Configuring Network Interfaces on Ubuntu

After launching both VMs, I move over to the **Ubuntu VM** and check its network settings. Here, I have two network interfaces: 
- `enp0s3` (NAT connection) – connected to my physical host machine.
- `enp0s8` (Internet lab connection) – which is not yet connected.

The NAT connection (`enp0s3`) allows communication between the VM and the host machine, while the `enp0s8` interface will be configured for communication between the Ubuntu and Windows VMs.

![2](https://imgur.com/uM4fsMW.png)

The `enp0s3` interface is connected to my host machine, while `enp0s8` will be used for the lab environment where the two VMs communicate directly.

---

#### 3. Configuring IP Settings on Ubuntu

Next, I configure the `enp0s8` interface within the Ubuntu VM to assign it an appropriate IP address and subnet mask. This configuration is essential for enabling network communication between the Ubuntu and Windows VMs.

In **Ubuntu**, I navigate to **Settings → Network → Ethernet** and select the `enp0s8` interface. I manually set the IP address to `192.168.50.100` and the subnet mask to `255.255.255.0`.

![3](https://imgur.com/pkPxnRR.png)
![4](https://imgur.com/aZ7seoL.png)

---

#### 4. Verifying IP Configuration on Ubuntu

To confirm that the changes were applied correctly, I open a terminal in the Ubuntu VM and run the `ifconfig` command. The output shows the updated IP address for the `enp0s8` interface, verifying that the VM is now properly configured.

![5](https://imgur.com/dADKQ19.png)

---

#### 5. Configuring Network Adapter Settings on Windows

Now, I move over to the **Windows 10 VM** to configure its network settings similarly. In the network settings, I find two adapters:
- **Ethernet (NAT)**: Used for internet connectivity.
- **Ethernet 2 (Lab Connection)**: The interface I'll use to communicate with the Ubuntu VM.

I configure the IP address for **Ethernet 2** to be `192.168.50.50` and set the subnet mask to `255.255.255.0`, matching the configuration on the Ubuntu VM.

![6](https://imgur.com/FPtzaGz.png)
![7](https://imgur.com/VfcJNtm.png)

---

#### 6. Testing Network Communication with Ping

After configuring the IP settings on both VMs, I perform a **ping test** to ensure the two systems can communicate. From the Ubuntu VM, I ping the Windows machine at `192.168.50.50`, and from the Windows VM, I ping the Ubuntu machine at `192.168.50.100`. Successful pings confirm that the VMs are properly networked.

![8](https://imgur.com/0LNeOHZ.png)

---

#### 7. Initiating Telnet Connection via PuTTY

Now that the network connection is set up, I use **PuTTY** on the Windows VM to establish a **Telnet** connection to the Ubuntu VM. In PuTTY, I enter the **IP address (192.168.50.100)** of the Ubuntu machine and choose the **Telnet** protocol, which operates on port **23**.

After confirming the details, I proceed to connect, and PuTTY opens a terminal window prompting for the Ubuntu login credentials. I enter the credentials, and the connection is established successfully.

![9](https://imgur.com/IDNKgW9.png)
![9.5](https://imgur.com/jBcDfR6.png)
![9.6](https://imgur.com/IK3c2JX.png)

---

#### 8. Capturing Telnet Traffic in Wireshark

Next, I open **Wireshark** on the Windows VM and select the **Ethernet 2** interface, where the Telnet traffic between the two VMs will be captured. I start the capture process, and immediately I see packets being exchanged between the systems over Telnet.

![10](https://imgur.com/8KqxhXT.png)
![11](https://imgur.com/XaUcQXK.png)

---

#### 9. Filtering Telnet Packets

To focus specifically on the **Telnet** packets, I use Wireshark's powerful filtering capabilities. I enter `telnet` into the filter bar and hit enter, which displays only the packets related to the Telnet communication.

![12](https://imgur.com/REhHekw.png)
![13](https://imgur.com/HuvR3zS.png)

---

#### 10. Analyzing the Telnet Traffic

I select one of the captured Telnet packets, right-click, and choose **Follow → TCP Stream** to examine the Telnet session in detail. This view shows the commands entered during the Telnet session and the corresponding responses from the Ubuntu machine.

![14](https://imgur.com/9FoBUdG.png)
![15](https://imgur.com/H5bTH53.png)

In this case, the **whoami** command was executed to confirm the user identity on the Ubuntu VM. While the username is visible, the password is encrypted—demonstrating the vulnerability of Telnet as an insecure protocol for remote access.

![16](https://imgur.com/ZZxuOu8.png)

---

### Conclusion

This project illustrates the inherent insecurity of Telnet, where credentials and commands are transmitted in plain text. As seen through the Wireshark packet analysis, Telnet should not be used in modern network environments where security is a concern. **SSH** (Secure Shell) is a far more secure alternative for remote connections, providing encryption and protecting sensitive data from being intercepted during transmission.

---

With these detailed steps, I've demonstrated the process of setting up network connections between virtual machines, initiating a Telnet session, and capturing the traffic using Wireshark for analysis.






