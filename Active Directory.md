# Active Directory Setup


## 1. Server Manager Setup

- Open Windows Server (Virtual Machine) and server manager will be directly open as the VM starts.
- On the top right side of server manager dashboard click on the "**Manager**" and the click on the option "**Add roles and features**"
  it will open a "**Add roles and features wizard**" interface.
- Click on "**Next**" on the "**Before you begin**" interface.
- On the "**Installation Type**" interface select "**Role-based or feature-based installation**" and click on "**Next**".
- Click on "**Next**" on the "**Select Destination Server**" interface.
- On the "**Server roles**" interface check the box of "**Active Directory Domain Services**" and then new interface will appear and
  click on the "**Features**" and then click on the "**Next**".
- Click on "**Next**" on the "**Features**" interface.
- Click on "**Next**" on the "**AD DS**" interface.
- Click on "**Install**" on the "**Confirmation**" interface and the install will start automatically.
 
https://github.com/user-attachments/assets/edf7987d-f959-43bb-8da4-5e24ec6de322


---

## 2. Domain Controller Setup

- On the Windows Server interface click on the "**flag**" icon.
- Click on the "**Promote this server to Domain Controller**".
- On the "**Deployment**" interface mark the option "**Add a new forest**" and give the name of new domain as `**mdfir.local**`
  and click on "**Next**".
- On the "**Domain Controller Option**" now create a "**Password**" and click on "**Next**".
- Click on "**Next** on the "**DNS Option**" interface.
- Enter the NetBIOS name as `**MDFIR**` on the "**Additionals Options**" interface click on "**Next**".
- Click on "**Next**" on the "**Paths**" interface.
- Click on "**Next**" on the "**Review Options**" interface.
- Click on "**Install**" on the "**Prerequisites Check**" interface and your system will restart.

https://github.com/user-attachments/assets/3a4ed9d7-eeed-4588-94ed-6f04d977f4e7


---

## 3. Active Directory User Setup on Target Machine

- Open the windows server and keep it running in the background.
- Now start the Windows 10 (Target Machine) and open the "**Network & Internet Settings**".
- Click on the "**Change Adapter Options**".
- On the "**Network Selection**" interface Right-click on the "**Ethernet**" options and click on "**Properties**".
- On the "**Ethernet Options**" interface double click on the `Internet Protocol Version 4 (IPv4)`.
- Now change the "**Prefered DNS server**" from `8.8.8.8` to  Windows Server (VM) IP `192.168.10.7` and save this setting.
- Now open start menu search "**This PC**" and open it's "**Properties**".
- Now scroll down and open "**Advanced System Settings**".
- On the Advance system settings interface go to "**Computer Name**" and click on "**Change**".
- Now Change "**Member of**" from Workgroup to  Domain `MDFIR.LOCAL` as soon as you save this Windows Security will ask to
  to enter **Computer Name / Domain Change** in that enter `Administrator` and `Password that you have given for the Windows Server`
  and save this setting your system will restart.

https://github.com/user-attachments/assets/891a1388-ecd1-4c34-b173-98b4ce1da235


---  

## 4. Loging in as Active Directory User

- As soon as your Virtual Machine restart, go to "**Other Users**".
- Now enter the username as you have created in the Active Directory Windows Server Manager and password to
  get login in the TARGET-PC.

https://github.com/user-attachments/assets/8b3abfee-7c74-4dc1-8cf6-433c79dd3e67

---

# Now you can use the TARGET machine as any user you have created in the Active Directory Windows Server Manager by just entring its username and password.

