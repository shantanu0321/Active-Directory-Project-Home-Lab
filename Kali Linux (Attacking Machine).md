# Kali Linux

## 1. NAT Network Setup 

- Open Virtual Box and select the Kali Linux (Virtual Machine) and open **Settings**.
- On the setting interface go to the "**Network**" and change preferred network to NAT-Network and it will be connected by the network  

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
 DNS Server 8.8.8.8 /n
```
 save this setting.

- Go to Home Screen of the Kali Linux and right click on the **Internet** icon and click on **Disconnect** it will stop internet access on the Machine.
- Once again on the Home screen click  right click on the **Internet** icon and click on **Connection** that is avaialble fot the PC it will start the internet access on the Machine.
- Now open the Terminal in the Linux and enter the command **`ip a`** it will show you the new IP Address you have entered
