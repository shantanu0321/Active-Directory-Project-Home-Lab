# Kali Linux


Note-: All the Virtual Machine: Windows 10, Windows Server, Kali Linux and must be running for the attack along with Splunk Server in the Ubuntu (Virtual Machine). 


---


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

- Now to check the that you are connected to the internet open Terminal and type command `ping 8.8.8.8` it will if everthing is correct      then there will be no packet loss and all packets will be sent and received .
   
- Now update the kali linux by the command `sudo apt-get update && sudo apt-get upgrade`.

https://github.com/user-attachments/assets/e31b0921-12fc-4316-8466-62d446e0728a


---


## 3. Target Machine Setup

- Start Target Machine and on start menu search **"This Pc"** and open **"Properties"**.

- Now scroll down on the settings and click on **"Advanced System Settings"**.

- Now on the **"System Properties"** and on the top right side of it click on the **"Remote"**.

- Now on that **"Allow remote connections to this computer"** and click on **"Select users"**.

- Now on the **"Remote Desktop Users"** interface click on **"Add..."**.

- Now write the name of the **"Users"** and and click on the **"Check Names"** and it will automatically add the name and save it.
  
https://github.com/user-attachments/assets/50394a04-ab92-481a-8f62-f2e182e52176


---


## 4. Password File Generation

- Open Terminal in kali and type command **`cd Desktop`** (`cd` command is used to change the directory,
   and `Desktop` is name of the directory)

- Now type following command:

   `mkdir ad-project` (`mkdir` this command is used to create a new directory and `ad-project` is directory name).
   
   `cd` (To get to back to home directory).
   
   `cd /usr/share` (To change the directory location to **"usr/share"** from **"home"** )
   
   `cd wordlists` (To get in the wordlists directory that is present in the **"usr/share"**)
   
   `ls` (This command is used to know about the lists files and directories in the current directory)
   
- Now type the command `cp rockyou.txt ~/Desktop/ad-project` (`cp` is used to copy files and directories,
  it duplicates the content of a source file or directory to a specified destination) in this `cp` to copy `rockyou.txt` is file name and `~/Desktop/ad-project` it is the loaction where the dupliacte content is copied.
   
   `clear` (This command is used to clear the Terminal window.)
   
   `cd` (When ever this command is used it will get you back to the **"home"** directory.)
   
   `cd Desktop/ad-project` (To get in the ad-project directory present in the **"Desktop"** directory.)
   
   `ls` (To check whether the copied file is present in the **"ad-project"** directory or not.)
   
   If the file is present then everthing is good or else there is some mistake you have done and it had
   been copied in the wrong directory.)
   
- Now type command `head -n 20 rockyou.txt > password.txt` (`head` command main purpose is to display the beginning of a file or data)
`-n` this option followed by an integer `20` to specify the number of lines to display, `rockyou.txt` is the name of file whose lines it will display, and  ` > password.txt` is a new file where the first 20 lines from "**rockyou.txt"** to**"password.txt"** is going to be copied.
  
  `ls` (To check the list whether the new **"password.txt"** is saved or not.)
  
  `nano passwords.txt` (`nano` command is used to edit a `.txt` file)
  
- Now write the password for any of the Active Directory User in it and then press `CTRL+O` to save the `password.txt` file and
  press `CTRL+X` to exit from the nano editer.

https://github.com/user-attachments/assets/e2a092fc-5e40-4f08-a728-329b49eeb516


---


## 5. Dictionary Attack

- Open Terminal in Kali Linux and type follofwing command :

  `cd Desktop/ad-project` (To go to the location of **"ad-project"** directory)

  `ls` (To check the list of all the passwords.txt file )

-  Now type command `hydra -l jennyj -P passwords.txt rdp://192.168.10.100 -t 1` to start the password attack

  In this `hydra` is the tool used for dictionary attack and `-l` is used to input the login username and `-P` is used to input the  **"password.txt"** for the attack `rdp://192.168.10.100` is used to make **"Remote Desktop Connection"** with the given IP address 
 `-t` yo run TASKS number `1` of connects in parallel per target

- There you can see the result with login name and password for `jennyj` this is how you can use it for password cracking.

- You can try other Active Directory Users for the attack with the same command but after `-l` change the username who you wanna test.

- You can make a new `.txt` file with command `touch login.txt`  (`touch` is command to make `.txt` file and `login.txt` is the name of file) and save it with Active Directory usernames. 

- Now type the command `hydra -L login.txt -P passwords.txt rdp://192.168.10.100 -t 1` here the `-L`.

- It will show the results of the attack .


https://github.com/user-attachments/assets/cfb8a722-c421-4429-a004-153ea8bd96de


---

## 6. Network Attack Information

- Open Windows 10 or Windows Server any of the Virtual machine and open the web browser and open splunk server by `192.168.10.10:8000`.

- In splunk server go to apps and click on **"Search & Reporting"** and on the search bar type `index="endpoint" jennyj` it will show all the logs and events.

- On the left side of the log events menu click on the **"EventCode"** it will show all the events occur on the system.


- On the EventCode interface it will show the event there you can see `4625` search this event code on web browser it will show you `An Accounts failed to logon on` (you can search all the event code on the browser).

- When you click on the `4625` you can see logged event and if multiple times any account is logged on on a same time or within 2-3 seconds that's that it's an attack.

- On the event code you can see `4624` you can search this event code on browser it will show you `An Account was successfully logged on`.

- Now you can open any log event and scrool down and you can see the on which `workstation ` the account was logged on with the `IP address` (In my case it will i was attacking with Kali Linux so it shows `Kali` with my station's IP address - `192.168.10.250`.


https://github.com/user-attachments/assets/37c1ef54-11bb-4b35-be7e-8e9de5cc9e5b


---
