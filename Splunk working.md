# Splunk Setup Guide

## Prerequisites

- Ubuntu system (with Splunk installed)
- Windows 10 virtual machine
- Both machines should be on the same network (like 192.168.10.x)
- 

---

## 1. Setting up Splunk Server

1. Start Ubuntu and run the Splunk server (make sure Splunk is actually running).
2. Boot up your Windows 10 VM.
3. On Windows 10, open a browser and go to:  
   `http://192.168.10.10:8000`  
   You should see the Splunk login page.
4. Log in with your Splunk credentials.
5. Go to **Settings** > **Indexer** > **Add New**.
   - Name it: `endpoint`
   - Hit save.
6. Now under **Settings**, go to **Forwarding and Receiving**.  
   Click **Add New** under "Receiving Data", use port `9997`, and save.


https://github.com/user-attachments/assets/d379e280-4a2a-46f0-bd11-19688e3a326c


---


## 2. Checking Splunk from a Host PC

1. On any host, open a browser and visit:  
   `http://192.168.10.10:8000`
2. Log in to Splunk.
3. Click on **Searching and Reporting**.
4. In the search bar, try this command and press Enter:  
   `index="endpoint"`
5. If you see events/logs show up, that means everything is working. If nothing shows, you might have missed a step or there's a typo somewhere.
6. On the left, under **Selected Fields**, click **host** to see which PC is sending logs to Splunk.


https://github.com/user-attachments/assets/0bb4e6ce-e532-4bb2-81ba-f76b14e86983


---


## Tips and Troubleshooting

- Double check firewall settings for ports 8000 (web) and 9997 (data).
- If you can’t access the web interface, try pinging the Ubuntu VM from the Windows VM.
- Sometimes, you might have to restart Splunk if things don’t appear right away.


---


*Hope this helps! Let me know if you get stuck or if I missed something obvious—sometimes it’s just a small thing.*
