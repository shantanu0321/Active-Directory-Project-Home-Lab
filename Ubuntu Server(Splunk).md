# Ubuntu Server Installation


## 1. Downloading Ubuntu Server

-

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

- Type command `sudo apt-get install virtualbox`.
  
- Type command `sudo apt-get install virtualbox-guest-addititons-iso -y` and press enter and type `sudo reboot` and reboot the virtual machine.

- Start the virtual machine and type command `sudo apt-get install virtualbox-guest-utils -y` and press enter and type `sudo
  reboot` ane reboot the virtual machine.

https://github.com/user-attachments/assets/b7131ff4-82b0-48b2-9363-5f56442d8ce7


- Go to the `Devices` on the top of the virtual machine and click on `shared folder` then go to `share folder settings` and add the         **folder where you downloaded the Ubuntu Server** and give the name to it and tick all the 3 options:
  
  > Read-only  ✔
  > Auto-Mount ✔
  > Make Permanent ✔
  
https://github.com/user-attachments/assets/229278a7-c036-45c7-96f0-56fb79898423


- Start the virtual machine and type command `sudo adduser "**mydfir**" vboxsf`  prerss enter.

https://github.com/user-attachments/assets/a29ad5d1-4553-448e-8343-474b06dc0e46


- Type command `mkdir share` and press enter.

- Type command `sudo mount -t vboxsf -o uid=1000,gid=1000 UbuntuServer (**Folder name you saved on the share folder settings**) share /` and press enter.

- Type command `cd share`  press enter.

- Type command `sudo dpkg -i (deb. server name)`(it can be done by pressing left control + tab) press enter.

- Type command `cd /opt/splunk` press enter.

- Type command `sudo -u splunk bash` press enter.

- Type command `cd bin` press enter.

- Type command `./splunk start` and it will ask you to set `administrator username` and `password` for the login of splunk server.

https://github.com/user-attachments/assets/a54500a9-ce90-4a55-8bfa-913945808b04


- To check your server is working or not, just open the Windows 10 or Windows Server anyone
 
- Open web browser in it and search the IP address of your ubuntu machine `192.168.10.10:8000` and the end result of this will show splunk login interface.

- Login in the website with the administrator username and password you have given.

https://github.com/user-attachments/assets/360d75d3-fc25-4154-a32b-74e5d2a3cdf0


- Every time you want to start the server you start the machine and type command:

   ```
   cd share
   cd /opt/splunk/
   sudo -u splunk bash
   cd bin
   ./splunk start
   ```
   These command will start the splunk server, but you have to enter it every time.
