# Kali Linux (Attacking Machine) Lab Setup

> **Note:**  
> For this lab, ensure all virtual machines (Windows 10, Windows Server, Kali Linux) are running, along with the Splunk server on the Ubuntu VM.

---

## 1. NAT Network Configuration

- Connect all virtual machines to a **NAT Network** in your virtualization platform to ensure a safe and isolated lab environment.
  
https://github.com/user-attachments/assets/67a252dd-0141-466f-a16a-fb61e4151aa8


---


## 2. Kali Linux IP Configuration

1. **Start Kali Linux** in VirtualBox.
2. On the desktop, right-click the **Network** icon and select **Edit Connections**.
3. Select your connection and click the **Settings** icon.
4. Go to the **IPv4** tab. Change the **Method** from `Automatic (DHCP)` to `Manual`.
5. Click **Add** and enter the following details:
    - **IP address:** `192.168.10.250`
    - **Netmask:** `24`
    - **Gateway:** `192.168.10.1`
    - **DNS Server:** `8.8.8.8`
6. Save the settings.
7. Right-click the **Network** icon again and click **Disconnect** to reset the connection, then reconnect.
8. Open a Terminal and verify your IP:
    ```bash
    ip a
    ```
9. Check internet connectivity:
    ```bash
    ping 8.8.8.8
    ```
    - If there is no packet loss, your setup is correct.
10. Update Kali Linux:
    ```bash
    sudo apt-get update && sudo apt-get upgrade
    ```

https://github.com/user-attachments/assets/e31b0921-12fc-4316-8466-62d446e0728a


---


## 3. Target Machine (Windows) RDP Setup

1. Start the **Target Machine** (e.g., Windows 10).
2. Open the **Start Menu**, search for “This PC,” and open **Properties**.
3. Scroll down and click **Advanced System Settings**.
4. In the **System Properties** window, go to the **Remote** tab.
5. Enable **Allow remote connections to this computer**.
6. Click **Select Users…** and then **Add…** to add users allowed for RDP.
7. Enter the desired user(s), click **Check Names**, and save.

https://github.com/user-attachments/assets/50394a04-ab92-481a-8f62-f2e182e52176


---


