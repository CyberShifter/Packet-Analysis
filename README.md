# Wireshark-Packet-Analysis
---
---
Overview 
---
---

I will be.......

---
---
**Some tools/software that I will be using for this project include:**
```
1.Oracle Virtual Box (This will be my hypervisor)
2. Windows 10 (I'll be using this as an ISO file within VirtualBox)
3. Ubuntu (I'll also be using this as an ISO file within VirtualBox)
4. Wireshark (Tool that I will be using to capture packets)
5. Putty (Will be the termianl that I utilize)
```
---
---
1. I open my hypersivor and open both my Windows VM and my Ubuntu VM
![1](https://imgur.com/MnAcRLX.png)
---
2. As you can see I have opened both Operating Systems up and if you look at the Ubuntu side, exactly where my mouse is hovered(the network settings), you will see that I have 2 interfaces, _Ethernet (enp0s3)_ and _Ethernet (enp0s8)_, i'm connected to the (enp0s3) which is my NAT connection, and the (enp0s8) isn't connected, which is my Internet lab connection. 
![2](https://imgur.com/uM4fsMW.png)

The enp0s3 interface connection is connected to my physical host, which is my main pc. The enp0s8 interface connection will be for other lab setups just to communicate with my Windows 10 VM.

---
3. Now inside of Ubuntu, I will go into settings --> Network --> Ethernet --> Navigate towards the _enp0s8_ interface
![3](https://imgur.com/pkPxnRR.png)

While I'm there, I will click on the _IPv4_ pane and make configurations to the IP address and Subnet mask so that the VM can communicate with my  
