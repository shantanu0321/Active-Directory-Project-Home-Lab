# Splunk Setup


## 1. Splunk Working  

- Open Ubuntu and run  `Splunk server`.
- Start Windows 10 virtual machine and open web browser and search: `192.168.10.10:8000` it will open splunk login website.
- Click on **Settings** and click on `indexer` and click on **add new** and type name `endpoint` and save it.
- Click on **Settings** again and click on `Forwarding and receiving` and click on **add new** on the `Reciving data`
   and type `9997` and save it.

https://github.com/user-attachments/assets/d379e280-4a2a-46f0-bd11-19688e3a326c

---

## 2. SplunK Host PC Worlking
 
- Open web browser and search: `192.168.10.10:8000` and login in the splunk website.
- Click **Searching and Reporting** and click on the search bar and type command `index="endpoint"` and search it.
- If it shows the the events log then everything is done perfectly or else something is wrong.
- In the events log go to left side on **selected fields** and click on **host** abd it will show you the name of the PC
   that is connected to splunk server.


https://github.com/user-attachments/assets/0bb4e6ce-e532-4bb2-81ba-f76b14e86983


  
