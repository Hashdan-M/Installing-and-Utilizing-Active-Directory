<img src="https://janikvonrotz.ch/wp-content/uploads/2017/10/Active-Directory-Logo.jpg" width=37.5% height=37.5%>

<h1>Utilizing Active Directory</h1>

<h2>Description</h2>
Active Directory is a core tool for system administrators who need to manage Windows machines. Active Directory allows us to manage users, groups, machines, and the policies that apply to all of them in a centralized fashion.
In this lab, we'll interact with Active Directory, use it to add users and groups, edit users memberships as well as create a new group policy object (GPO).

<h2>Installing Active Directory</h2>
To install Active Directory (AD) on a Windows Server, follow these steps. This guide assumes you are using Windows Server 2019 or Windows Server 2022, but the process is similar for other recent versions.

### Prerequisites

1. **Server Operating System**: Ensure you have Windows Server installed.
2. **Static IP Address**: Set a static IP address for your server.
3. **Server Name**: Make sure your server has a unique name within your network.
4. **Administrative Privileges**: Ensure you have administrative rights to install software and configure settings.

### Installation Steps

#### 1. **Open Server Manager**

- Click on the **Start** button and open **Server Manager**.
- Alternatively, you can press `Windows + R`, type `servermanager`, and press Enter.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902137840/in/dateposted-public/" title="server manager"><img src="https://live.staticflickr.com/65535/53902137840_11850770fe_z.jpg" width="623" height="573" alt="server manager"/></a>

#### 2. **Add Roles and Features**

- In Server Manager, click on **Manage** in the top right corner and select **Add Roles and Features**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53901960458/in/dateposted-public/" title="roles and features"><img src="https://live.staticflickr.com/65535/53901960458_0f3c7f288d_z.jpg" width="623" height="436" alt="roles and features"/></a>

- Click **Next** on the **Before You Begin** page.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53901713366/in/dateposted-public/" title="before you begin"><img src="https://live.staticflickr.com/65535/53901713366_092b361536_z.jpg" width="623" height="382" alt="before you begin"/></a>

#### 3. **Select Installation Type**

- Choose **Role-based or feature-based installation** and click **Next**.

 <a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53900820477/in/dateposted-public/" title="installation type"><img src="https://live.staticflickr.com/65535/53900820477_cd011d70bc_z.jpg" width="624" height="388" alt="installation type"/></a>

#### 4. **Select Destination Server**

- Choose the server from the server pool where you want to install AD DS (Active Directory Domain Services) and click **Next**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53901979798/in/dateposted-public/" title="server selection"><img src="https://live.staticflickr.com/65535/53901979798_247ea9e9bb_z.jpg" width="623" height="431" alt="server selection"/></a>

#### 5. **Select Server Roles**

- On the **Select server roles** page, check **Active Directory Domain Services**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53901986518/in/dateposted-public/" title="select server roles"><img src="https://live.staticflickr.com/65535/53901986518_9fbe8edfc7_z.jpg" width="623" height="419" alt="select server roles"/>

- A dialog box will appear prompting you to add features required for AD DS. Click **Add Features**.
- Click **Next**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902096679/in/dateposted-public/" title="add features"><img src="https://live.staticflickr.com/65535/53902096679_35d08835d5_z.jpg" width="624" height="380" alt="add features"/></a>

#### 6. **Select Features**

- You can generally leave the default features selected. Click **Next**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53900866227/in/dateposted-public/" title="next"><img src="https://live.staticflickr.com/65535/53900866227_87a0338087_z.jpg" width="623" height="368" alt="next"/></a>

#### 7. **AD DS Information**

- Review the information about AD DS. Click **Next**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902027958/in/dateposted-public/" title="domain services"><img src="https://live.staticflickr.com/65535/53902027958_ed52d47662_z.jpg" width="623" height="424" alt="domain services"/></a>

#### 8. **Confirmation**

- Review your selections. Click **Install** to begin the installation.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902217845/in/dateposted-public/" title="confirm"><img src="https://live.staticflickr.com/65535/53902217845_797af1d380_z.jpg" width="624" height="420" alt="confirm"/></a>

- The installation will proceed, and once it's completed, you’ll see a notification indicating that the installation was successful.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902043633/in/dateposted-public/" title="installation progress"><img src="https://live.staticflickr.com/65535/53902043633_61fee6dd4a_z.jpg" width="624" height="378" alt="installation progress"/></a>

#### 9. **Promote the Server to a Domain Controller**

- After the installation, a notification will appear in Server Manager indicating that **Post-installation tasks** are needed. Click on **Promote this server to a domain controller**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53900893267/in/dateposted-public/" title="promote to dc"><img src="https://live.staticflickr.com/65535/53900893267_9dbf2ed09a_z.jpg" width="640" height="352" alt="promote to dc"/></a>

#### 10. **Configure AD DS**

- In the **Deployment Configuration** window:
  - **Add a new forest** if this is your first domain controller. Enter the **Root domain name** (e.g., `example.local`).
  - If you are adding a domain controller to an existing domain, select **Add a domain controller to an existing domain** and provide the necessary domain details.

- Click **Next**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902152649/in/dateposted-public/" title="deployment configuration"><img src="https://live.staticflickr.com/65535/53902152649_eb64614e81_z.jpg" width="640" height="468" alt="deployment configuration"/></a>

#### 11. **Domain Controller Options**

- Configure the domain controller options, including:
  - **Forest functional level**: Choose the appropriate level based on your needs.
  - **Domain functional level**: Choose the appropriate level based on your needs.
  - **Global Catalog** and **Read-Only Domain Controller (RODC)** options.
  - Set the **Directory Services Restore Mode (DSRM) password**.

- Click **Next**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53901805046/in/dateposted-public/" title="domain configuration options"><img src="https://live.staticflickr.com/65535/53901805046_398d915177_z.jpg" width="640" height="472" alt="domain configuration options"/></a>

#### 12. **DNS Options**

- Review the DNS options and click **Next**. If you encounter warnings about DNS delegation, you can usually proceed by addressing these later.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902246035/in/dateposted-public/" title="dns options"><img src="https://live.staticflickr.com/65535/53902246035_88dd78db40_z.jpg" width="640" height="468" alt="dns options"/></a>

#### 13. **Additional Options**

- Review additional options, such as the NetBIOS domain name. Click **Next**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902249900/in/dateposted-public/" title="additional options"><img src="https://live.staticflickr.com/65535/53902249900_298ef18956_z.jpg" width="640" height="473" alt="additional options"/></a>

#### 14. **Paths**

- Choose the paths for the AD database, log files, and SYSVOL folder. The default paths are generally fine. Click **Next**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53900913197/in/dateposted-public/" title="database path"><img src="https://live.staticflickr.com/65535/53900913197_e717c5c71b_z.jpg" width="640" height="470" alt="database path"/></a>

#### 15. **Review Options**

- Review your selections and click **Next**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902170474/in/dateposted-public/" title="review options"><img src="https://live.staticflickr.com/65535/53902170474_c6515770ca_z.jpg" width="640" height="472" alt="review options"/></a>

#### 16. **Prerequisites Check**

- The installer will perform a prerequisites check. Ensure all checks pass. Click **Install**.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902259780/in/dateposted-public/" title="prerequisites check"><img src="https://live.staticflickr.com/65535/53902259780_e1b0c60051_z.jpg" width="640" height="472" alt="prerequisites check"/></a>

#### 17. **Reboot**

- The server will automatically reboot once the installation and configuration are complete.

### Post-Installation

1. **Verify Installation**: Log in with domain credentials and use tools like **Active Directory Users and Computers** or **Active Directory Administrative Center** to ensure AD DS is functioning correctly.
2. **Additional Configuration**: Depending on your environment, you may need to configure Group Policy, set up additional domain controllers, or configure DNS settings.

Following these steps should set up Active Directory on your server. If you encounter issues or need more advanced configuration, Microsoft’s documentation or community forums can be helpful resources.
