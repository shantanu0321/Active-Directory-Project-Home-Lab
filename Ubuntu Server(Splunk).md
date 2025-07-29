# Ubuntu Server Installation


## 1. Downloading Ubuntu Server

- Open google chrome and search " **Ubuntu** " and click on official website:  https://ubuntu.com/

- Click on the "**Products**" and click on "**Ubuntu Server**".
  
- Click on the "**Download Ubuntu Server**" and click on the "**Download 24.04.2 LTS**" or which ever version is
  used at the present time and your download will start  automatically.

https://github.com/user-attachments/assets/de818e95-6879-4085-aa76-1b62320dcde6

---

## 2. Install the Ubuntu Server in Virtualbox

- Open the virtualbox and click on **New**
  
- Now write the name of the new machine, and select the location where you want to install, and
  choose the ISO file of the Ubuntu Server, rest all the setting it will take automatically and check the box of "**Skip unattented installation**
  
- Make the "**hardware**" setting according to youe device and provide 100GB of space to the "**hardisk**" and finish the install.

https://github.com/user-attachments/assets/d6fa3c6f-d908-433f-81ba-a502872d8422

---

## 3. Setup the Ubuntu Server

- Start the Ubuntu server machine.
  
- While installation use Arrow keys for the setup.
  
- Watch the video for better understanding.
  
- After the installation run command `sudo apt-get update && sudo apt-get upgradxe`to update the server.
  
https://github.com/user-attachments/assets/146dd4f4-6ca4-42d2-89bc-59b9ff70e9b0

---

## 4. NAT Network Setup

- Watch the video for better understanding.

https://github.com/user-attachments/assets/665b8a5a-010c-4aee-9909-a58622599305

    
## 5. Setup the Ubuntu IP address

- Start the Virtual Machine and login in the server using the "**Username**" and "**Password**" you have given while installation.
  
- Get the `root` permission of the Virtual machine using command `sudo su` and then change the directory using the command `cd /etc/netplan`






- Type command `nano` and press Left Control + Tab on keyboard and it will appear `50-colud-init.yaml` and press enter.
 





- Change the setting in that file according to this :

```
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: no
      addresses : [192.168.10.10/24]
      nameservers: 
          addresses: [8.8.8.8]
      routes: 
          - to: default
            via: 192.168.10.1
```



The red part is created when we presss space bar on the keyboard.


- Save the setting by pressing `Left Control + O` and exit the file by pressing `Control + x`.
  
- Type the command `sudo netplan apply` and press enter it will show some warning sign but press enter.

- Type command `ip a` it will show your changed IP address.



---
  
## 6. Splunk Download

- In the host window open the chrome browser and search splunk and go to the official website : https://www.splunk.com/
  
- In the website do "sign up" and "login in" in the splunk then go to the "**Platform**" and right click on the "**Free Trials & Downloads**"

- Find Splunk Enterprise and right click on "**Get My Free Trial**"

- Now choose your installation package to `Linux`  and download the `.deb` version.

- Read the document and check the box of aggrement and access the program and your download will start automatically.

https://github.com/user-attachments/assets/4956448a-7569-4e6f-94b8-8e4fec0a0df3

---

## 7. Splunk setup in the Ubuntu server

- Start the virtual machine and login in the machine.
  
- Type command `sudo apt-get install virtualbox-guest-addititons-iso -y` and press enter and reboot the virtual machine.

- Start the virtual machine and type command `sudo apt-get install virtualbox-guest-utils -y` and press enter and
  reboot the virtual machine.

- Start the virtual machine and type command `sudo adduser "**mydfir**" vboxsf.

- 
