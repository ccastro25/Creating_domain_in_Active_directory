# Creating_domain_in_Active_directory

## Adding Active Directory Options in Server Manager

I didn't have any Active Directory options within Server Manager. I tried to add it through Apps, but it did not work. Then, I tried the following command through PowerShell, and it worked: ```Install-WindowsFeature RSAT-AD-Tools```
![Install Active Directory Domain Services (AD DS)](https://github.com/user-attachments/assets/b03855e8-cd14-471f-b193-f0f5a870718b)

# Adding Domain to Active Directory



### 1. Install Active Directory Domain Services (AD DS)

- Open **Server Manager** and click on **Add Roles and Features** in the **Manage** tab.
- A window will pop up:
  - **Before You Begin**: Click **Next**.
  - **Installation Type**: Leave the default selection and click **Next**.
  - **Server Selection**: Leave the default selection and click **Next**.
  - **Server Roles**: Select **Active Directory Domain Services**.
- The **Add Roles and Features Wizard** window will appear:
  - Click **Add Features**.
- Now that you're back to the **Server Roles** tab, click **Next**.
- At the **AD DS** tab, click **Next**.
- At the **Confirmation** tab, select **Restart**:
  - Select **Restart the destination server automatically if required**.
  - Click **Install**.

![Install Active Directory Domain Services (AD DS)](https://github.com/user-attachments/assets/a223c59c-a438-4bd2-a910-b328a075781e)





### 2. Promote the Server to a Domain Controller
- After installation, you’ll see a notification flag at the top right. Click it and select **Promote this server to a domain controller**.
- Choose **Add a new forest** if it's a new domain. Enter the root domain name (e.g., `example.com`).

---

#### Do You Need to Have an Actual Domain to Set Up a Domain in Active Directory?

***No***, you don't need an actual internet domain to set up a domain in Active Directory. You can create a local domain for internal use. When setting up Active Directory, you can choose a unique domain name, such as `example.local` or `internal.companyname`, which will work within your network environment. This local domain won't be accessible from the internet but will function perfectly for managing resources and users within your local network.

---



- Click **Next** and set the **Domain Controller Options**, including the Directory Services Restore Mode (DSRM) password.
- Click **Next** through the DNS options and Additional Options screens.
- Review and confirm the **NetBIOS name**, which is typically a shorter name for the domain.
- Leave the default paths for the AD DS database, log files, and SYSVOL. Click **Next**.
- Review your selections and click **Install**.
![Edited Promote the Server to a Domain Controller](https://github.com/user-attachments/assets/dbca593c-5fe0-452e-b805-eac744ca0978)

### 3. Check for fully qualified domain name

- select Tools tab
- click on DNS
- DNS Manager window will appear
- double click on the small server Under DNS
- double click Foward Look Zones 
   - there you will see your Domain 
    a new forward lookup zone with the
    fully qualified domain name (FQDN) of 
    your new domain.

![Check for fully qualified domain name](https://github.com/user-attachments/assets/a2e2b9bf-6c30-41e3-a717-dcc9bd6740ae)




### 4. Check Domain Health

- Run `dcdiag` to check the health of your domain and ensure everything is configured correctly.
![Check Domain Health](https://github.com/user-attachments/assets/5f37b880-2ff6-4dbb-8909-b3516cff9edf)

# Congrats, you now have Active Directory and A local Domain
