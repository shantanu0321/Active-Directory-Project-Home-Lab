# Windows 10 Installation (Target Machine)

## 1. Download Windows 10 from official website

- Search Windows 10 on google and click on microsoft official website https://www.microsoft.com/en-in/software-download/windows10.

<img width="1335" height="667" alt="1" src="https://github.com/user-attachments/assets/586286a5-67cf-4106-a56c-44b0798ee268" />

- Download the Windows 10 installation media.

<img width="1359" height="705" alt="3" src="https://github.com/user-attachments/assets/94061ba5-88ca-407e-a419-298c75227bb4" />

- Download will start automatically.

<img width="368" height="177" alt="47" src="https://github.com/user-attachments/assets/345e5494-0e32-4f51-8a1c-14f44d2c95d7" />

---

## 2. Installation of Virtual Machine 

- Open the virtual box and click on the "**New**".

<img width="1359" height="701" alt="2 2" src="https://github.com/user-attachments/assets/573d8844-444e-4477-b99a-9eecfcb4b548" />

- Write the name of machine and add the location where you want to save the file and select the ISO file and check the box of "**Skip  Unattended Installation**" and click next.

<img width="758" height="595" alt="1 1" src="https://github.com/user-attachments/assets/72e6e738-51fc-4ba9-88a9-b2ec750db1cc" />

- Make "**Hardware**" setting according to your PC specifications and then go to "**Hard Disk**" settings.

<img width="842" height="612" alt="hardware settings" src="https://github.com/user-attachments/assets/e8ba98c6-0429-4374-ba23-41807857d300" />

- Make "**Hard Disk**" storage from 25GB to 50GB at least and click on finish.

<img width="841" height="605" alt="hard disk " src="https://github.com/user-attachments/assets/321f2865-7bfe-4dae-b3cf-455cb711c921" />

---

## 3. Setup of Windows 10 in VirtualBox

- Start the Virtual Machine.
  
<img width="846" height="602" alt="2 3" src="https://github.com/user-attachments/assets/9e9334c9-e192-48be-a1bb-fb01fb98656b" />


- Follow the steps shown in the video below.

https://github.com/user-attachments/assets/550a2142-379c-450c-be59-6ccc119396cf

---

## 4. Name change of the PC

- Open "**Start**" menu and search "**This PC**" and right click on it and go to "**Properties**"

- Now scroll down and click on the "**Rename PC**" and write the new name as "**Target Pc**" and save it and restart the PC.

https://github.com/user-attachments/assets/72ded7e2-b6f4-4f7a-8295-24c07e91e575


---

## 5. Sysmon Download & Install

- Open web browser and search "**sysmon windows server**" an click on the microsoft official link: https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon

- Click on **Download Sysmon** and your download will start automatically.

- Open new tab in the browser and search "**Sysmon olaf config**" click on the website: https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml and then click on `Raw` option and save it on the same folder where you extract
  the sysmon with the name  **sysmonconfig**.

- Extract the **Sysmon** downloaded file.

- Save the `sysmonconfig.xml` file in the folder where you extracted the **Sysmon**.


https://github.com/user-attachments/assets/e2c7f74e-310f-4589-b9fe-9234fef65df8


- Open the Command Prompt in **Administrator** mode and type `cd` and location of file where you extract the file and press enter.

- Type the command `.\Sysmon64.exe -i .\sysmonconfig.xml` and it will be installed.

https://github.com/user-attachments/assets/175c8a62-a333-4d3e-87ce-3887be8f1fef


## 6. Change the IP of the Windows 10

- Click on the **Ethertnet** icon on the taskbar and then click on **Network & Internet Settings**

- Click on **Change adapter options** and click on the **Ethernet** and click on the **Properties** and double click on the "**Internet Protocol Version 4 (TCP/IPv4) and click on use the following and write the following:

> IP Address- 192.168.10.100, 
> Subnet Mask - 255.255.255.0, 
> Default Gateway - 192.168.10.1, 
> Prefered DNS Server - 8.8.8.8

https://github.com/user-attachments/assets/12bb66a9-a96c-4634-bab9-4534e789d7b4


---

 ## 7. Splunk Forwader Download 

 - Open web browser and search **Splunk** and click on official website: https://www.splunk.com/
 
 - Do **Sign Up** and then **Login** in the website
 
 - Click on the **Platform** and then click on the **Free Trials & Download**

 - Find **Slpunk Forwarder** and click on **Get My Free Download**

 - Download the windows file compatible to your Pc.

https://github.com/user-attachments/assets/e78e21ec-b6b4-4d63-adcc-dd94c7311d6f


---

## 8. Splunk Forwarder Install 

- Start the Virtual Machine and open **File Explorer** and go to folder where you download the Splunk Forwarder

- Open the setup file.
  
- Check the box of liscense aggrement and click on the `next` option.
  
- Create the username - `admin` and check the box of "Generate the Password
  
- Leave the "Deployment Server" as blank.
  
- Set the "Receiving the Indexer" IP Address - `192.168.10.10` and set the host to `9997` and click on `next`.
  
- Click on install and your installation process will start.


https://github.com/user-attachments/assets/1b89685f-5139-4c1e-ae7f-5d76fd4cb4fd


---

## 9. Splunk Input Configuration

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

- Save this note pad in the the " Localdisk:C/Program File/Splunk Universal Forwarder/etc/system/local " and save it as inputs.conf in all file format, you can watch it in the below video

https://github.com/user-attachments/assets/1e4bc0c4-bf75-47e9-8fe0-b4be1c8b30f3

---


 
