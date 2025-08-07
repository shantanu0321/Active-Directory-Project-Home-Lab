# Kali Linux


## 1. NAT Network Setup 

- Connect the Virtual Machine to the NAT Network to work in the safe environment.

https://github.com/user-attachments/assets/67a252dd-0141-466f-a16a-fb61e4151aa8

---


## 2. Linux IP Setup 

- Start Kali Linux in the Virtual Box.

- On the Home Screen right click on the Internet Option and Click on Double click on the **Edit connection**.

- On the bottom of the Network Connection interface click on the **setting** icon.

- Now on the **Editing Connection** interface click on **`IPv4`** in that interface change the **Method** from the "**Automatice (DHCP)**" to "**Manual**".

- Now click on "**Add**" and write the following:
 ```
  IP - 192.168.10.250 
```
```
 Netmask - 24
```
```
 Gateway - 192.168.10.1
```
```
 DNS Server 8.8.8.8 
```
 save this setting.

- Go to Home Screen of the Kali Linux and right click on the **Internet** icon and click on **Disconnect**
   it will stop internet access on the Machine.
  
- Once again on the Home screen click  right click on the **Internet** icon and click on **Connection**
  that is avaialble fot the PC it will start the internet access on the Machine.

- Now open the Terminal in the Linux and enter the command **`ip a`** it will show you the new IP Address you have entered.

- Now to check the that you are connected to the internet type command `ping 8.8.8.8` it will if everthing is correct then
   there will be no packet loss and all packets will be sent and received .
   
- Now update the kali linux by the command `sudo apt-get update && sudo apt-get upgrade`.


https://github.com/user-attachments/assets/e31b0921-12fc-4316-8466-62d446e0728a

---

## 3.
