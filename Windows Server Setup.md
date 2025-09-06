# Windows Server Installation 

## 1. Download Windows Server from official website

- Search `Windows server iso download` on google and click on 1st microsoft official website https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022 .
  
- 
  
https://github.com/user-attachments/assets/6155bab4-570b-4fa6-a4fc-2ce3a4a2259a

---

## 2. Create a new VM in the VirtualBox

- Open the Virtualbox and click on New, then write the name of the new machine and make the settings according to the system as shown in the video.

https://github.com/user-attachments/assets/be0c2d59-2453-4325-bc4f-73a64eddb128

---

## 3. Setup the Windows Server

- Start the machine and install the Windows Server 2022 Standard Evaluation(Desktop Experience) and then Setup your username and password as shown in the video.

https://github.com/user-attachments/assets/4cc59460-0755-49d2-9e5c-773cebffe54f

---

## 4. Rename the Windows Server 

- Open the start menu and search `This PC` and right click on it and click on `Properties` and select the click on `Rename this PC` and
  change the name to `ADDC01` and restart the PC.

https://github.com/user-attachments/assets/7c366fcf-fe3c-4f60-8606-50f21649816e

---

## 5. NAT Network Setup

- Open VirtualBox and select the Window Server (Virtual Machine) and click on setting.

- Click on the Network and change **Attached to:** to NAT Network and it will be set to the network **AD Project**
  and click on **OK**.

https://github.com/user-attachments/assets/149cfe08-1eb0-452a-aaa8-580f90a9f000

---

## 6. Sysmon Download & Install

- Open web browser and search "**sysmon windows server**" an click on the microsoft official link: https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon

- Click on **Download Sysmon** and your download will start automatically.

- Open new tab in the browser and search "**Sysmon olaf config**" click on the website: https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml and then click on `Raw` option and save it on the PC as **sysmonconfig**.

- Extract the **Sysmon** downloaded file.

- Save the `sysmonconfig.xml` file in the folder where you extracted the **Sysmon**.

   
https://github.com/user-attachments/assets/9850bbba-18ef-4103-85ca-9f1254c7cc6f


- Open the Command Prompt in **Administrator** mode and type `cd` and location of file where you extract the file and press enter.

- Type the command `.\Sysmon64.exe -i .\sysmonconfig.xml` and it will be installed.


https://github.com/user-attachments/assets/65096418-a72c-4f63-9a93-c4312d0bc82e

---
    
## 7. Configure the IP Address of the Windows Server according to the NAT Network.

- Click on the Ethernet icon in the taskbar and click on the `Network & Internet Settings`.

  
- Click on the `Change adapter options` and right click on the `Ethernet` and click on the `Properties` and double click on the `Internet Protocol Version 4 (TCP/IPv4)` and click on the `Use the following` and write the following:


> IP Address- 192.168.10.7, 
> Subnet Mask - 255.255.255.0, 
> Default Gateway - 192.168.10.1, 
> Prefered DNS Server - 8.8.8.8

https://github.com/user-attachments/assets/550ece1b-a54c-4c53-af9b-17848177ed29

---

## 8. Install Splunk Forwarder 

- Open the web browser and search `Splunk` and open the official website https://www.splunk.com/en_us/download/universal-forwarder.html
and then Login on the website with the credentials you used to install it on Ubuntu Server.

- After loging in, click on the `Platform` and then click on the `Free Trials and Download`.
  
- Now download it according to your computer compatibility (64 bit or 32 bit) for Windows.

https://github.com/user-attachments/assets/f29a18fc-f3b6-442f-9125-da43b5d120fa

---

## 9. Install the Splunk in the Windows Server

- Open the setup file.
- Check the box of liscense aggrement and click on the `next` option.
- Create the username - `admin` and check the box of "Generate the Password"
- Leave the "Deployment Server" as blank.
- Set the "Receiving the Indexer" IP Address - `192.168.10.10` and set the host to `9997` and click on `next`.
- Click on install and your installation process will start.   
  
https://github.com/user-attachments/assets/22c71593-83ba-44ac-b5b0-193db7b86eb9

---

## 10. Configure the Splunk 

- Open the `Splunk Universal Forwader` folder in `Program File` in `Local Disck:C`
- Open the `etc` folder and in that open `system` folder and in that open `local ` folder.
- open the `start menu` and search `Notepad` and run it as `Administrator`.
- Paste this text in the notepad"

```
[WinEventLog://Application]

index = endpoint

disabled = false

[WinEventLog://Security]

index = endpoint

disabled = false

[WinEventLog://System]

index = endpoint

disabled = false

[WinEventLog://Microsoft-Windows-Sysmon/Operational]

index = endpoint

disabled = false

renderXml = true

source = XmlWinEventLog:Microsoft-Windows-Sysmon/Operational

```

- Save this note pad in the the " Localdisk:C/Program File/Splunk Universal Forwarder/etc/system/local " and save it as inputs.conf in all file format you can watch it in the below video

https://github.com/user-attachments/assets/02497c8f-9cf9-45a5-8f51-b311f2e91a34


  
