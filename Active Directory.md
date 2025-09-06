# Active Directory Setup Guide

This guide walks you through setting up Active Directory on a Windows Server virtual machine and connecting a Windows 10 target machine to the domain. Each step includes clear instructions and tips for a smooth lab experience.


---


## Prerequisites

- Two virtual machines:
  - **Windows Server** (for Active Directory Domain Services)
  - **Windows 10** (target machine to join the domain)
- Both VMs must be on the same virtual network.
- Administrative privileges on both VMs.
- Note the IP address of your Windows Server VM.


---


## 1. Setting Up Windows Server and Installing Active Directory Domain Services (AD DS)

1. **Start the Windows Server VM** and log in as an administrator.
2. **Open Server Manager** (opens automatically at startup).
3. In the top-right, click **Manage** > **Add Roles and Features**.
4. The "Add Roles and Features Wizard" opens.
   - Click **Next** on the "Before You Begin" screen.
   - Choose **Role-based or feature-based installation**, then click **Next**.
   - Select your server from the list and click **Next**.
   - In "Server Roles," check **Active Directory Domain Services**.
     - When prompted, click **Add Features**.
   - Click **Next** through the "Features" and "AD DS" pages.
   - On the "Confirmation" page, click **Install**.
5. Wait for the installation to complete.
6. (Optional) Review the installation summary for errors.

https://github.com/user-attachments/assets/edf7987d-f959-43bb-8da4-5e24ec6de322


---


## 2. Promoting the Server to a Domain Controller

1. In Server Manager, click the **flag** icon (notifications area).
2. Click **Promote this server to a domain controller**.
3. In the "Deployment Configuration" window:
   - Select **Add a new forest**.
   - Enter your desired root domain name, e.g., `mdfir.local`.
   - Click **Next**.
4. Set a **Directory Services Restore Mode (DSRM) password** and click **Next**.
5. On the "DNS Options" page, click **Next**.
6. On "Additional Options," confirm or edit the NetBIOS domain name (e.g., `MDFIR`) and click **Next**.
7. Click **Next** through the "Paths" and "Review Options" screens.
8. The system will run a prerequisites check. If all checks pass, click **Install**.
9. The server will restart automatically after installation.

https://github.com/user-attachments/assets/3a4ed9d7-eeed-4588-94ed-6f04d977f4e7


---


## 3. Connecting the Windows 10 Target Machine to the Domain

1. **Start and log in to the Windows Server VM. Leave it running.**
2. **Start the Windows 10 target VM.**
3. Open **Network & Internet Settings**.
   - Click **Change adapter options**.
   - Right-click your network adapter (e.g., Ethernet) and select **Properties**.
   - Double-click **Internet Protocol Version 4 (TCP/IPv4)**.
   - Change the **Preferred DNS server** to the Windows Server VM’s IP address (e.g., `192.168.10.7`).
   - Click **OK** to save.
4. Open **This PC** > **Properties**.
   - Scroll down and click **Advanced system settings**.
   - In the "System Properties" window, go to the **Computer Name** tab and click **Change**.
5. Under **Member of**, select **Domain** and enter your domain name (e.g., `MDFIR.LOCAL`).
6. When prompted, enter credentials:
   - **Username:** `Administrator`
   - **Password:** (the password you set during domain controller setup)
7. After joining the domain, restart the Windows 10 machine.

https://github.com/user-attachments/assets/891a1388-ecd1-4c34-b173-98b4ce1da235


---  


## 4. Logging in as an Active Directory User

1. After restart, on the Windows 10 login screen, select **Other user**.
2. Enter the Active Directory username and password created in the Windows Server's Active Directory Users and Computers.
3. Log in—the Windows 10 machine is now authenticated by Active Directory!

https://github.com/user-attachments/assets/8b3abfee-7c74-4dc1-8cf6-433c79dd3e67

---

## Additional Tips & Troubleshooting

- **Creating Users:**  
  Use the **Active Directory Users and Computers** tool on the Windows Server to create and manage users.

- **DNS Issues:**  
  Ensure the target machine uses the domain controller’s IP as its DNS server. This is critical for domain discovery and joining.

- **Admin Rights:**  
  You must have local administrator rights to join a machine to the domain.

- **Network Connectivity:**  
  Both VMs must be able to communicate—verify via ping or connectivity tests.

- **Resetting Passwords:**  
  Passwords can be changed from Active Directory Users and Computers on the domain controller.

---

## Summary Checklist

- [ ] Windows Server VM is running AD DS and promoted to domain controller.
- [ ] Windows 10 VM is configured to use the server’s IP as DNS.
- [ ] Windows 10 VM joined to the domain.
- [ ] Can log in to Windows 10 as an Active Directory user.

---

With these steps, your lab environment is ready for further Active Directory experiments and management tasks!

