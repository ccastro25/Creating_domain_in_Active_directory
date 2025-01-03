# Creating_domain_in_Active_directory

## Adding Active Directory Options in Server Manager

I didn't have any Active Directory options within Server Manager. I tried to add it through Apps, but it did not work. Then, I tried the following command through PowerShell, and it worked: ```Install-WindowsFeature RSAT-AD-Tools```
# Adding Domain to Active Directory



### 1. Install Active Directory Domain Services (AD DS)

- Open **Server Manager** and click on **Add Roles and Features**.
- Follow the wizard to install **Active Directory Domain Services**.

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
- Specify the paths for the AD DS database, log files, and SYSVOL. Click **Next**.
- Review your selections and click **Install**.

### 3. Configure DNS

- Open **DNS Manager** from Server Manager.
- Create a new forward lookup zone with the fully qualified domain name (FQDN) of your new domain.


### 5. Check Domain Health

- Run `dcdiag` to check the health of your domain and ensure everything is configured correctly.

### 6. Join Computers to the Domain

- On the client computer, go to **System Properties > Computer Name > Change**.
- Select **Domain**, enter the domain name, and click **OK**.
- Provide domain credentials when prompted.
- Restart the computer to complete the process.
