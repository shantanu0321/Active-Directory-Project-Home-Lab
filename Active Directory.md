# Active Directory Setup


## 1. Server Manager Setup

- Open Windows Server (Virtual Machine) and server manager will be directly open as the VM starts.
- On the top right side of server manager dashboard click on the **`Manager`** and the click on the option *`Add roles and features`*
  it will open a **`Add roles and features wizard`** interface.
- Click on **`Next`** on the **`Before you begin`** interface.
- On the **`Installation Type`** interface select *`Role-based or feature-based installation`* and click on **`Next`**.
- Click on **`Next`** on the **`Select Destination Server`** interface.
- On the **`Server roles`** interface check the box of *`Active Directory Domain Services`* and then new interface will appear and
  click on the *`Features`* and then click on the **`Next`**.
- Click on **`Next`** on the **`Features`** interface.
- Click on **`Next`** on the **`AD DS`** interface.
- Click on **`Install`** on the **`Confirmation`** interface and the install will start automatically.
 
https://github.com/user-attachments/assets/edf7987d-f959-43bb-8da4-5e24ec6de322

---

## 2. Domain Controller Setup

- On the Windows Server interface click on the **`flag`** icon.
- Click on the "**`Promote this server to Domain Controller`**".
- On the **`Deployment`** interface mark the option *`Add a new forest`* and give the name of new domain as **`mdfir.local`**
  and click on **`Next`**.
- On the **`Domain Controller Option`** enter the **`Password`** and click on **`Next`**.
- Click on **`Next`** on the **`DNS Option`** interface.
- Enter the NetBIOS name as *`MDFIR`* on the **`Additionals Options`** interface click on **`Next`**.
- Click on **`Next`** on the **`Paths`** interface.
- Click on **`Next`** on the **`Review Options`** interface.
- Click on **`Install`** on the **`Prerequisites Check`** interface and your system will restart.

https://github.com/user-attachments/assets/3a4ed9d7-eeed-4588-94ed-6f04d977f4e7

---

## 3. Active Directory User Setup

- 
