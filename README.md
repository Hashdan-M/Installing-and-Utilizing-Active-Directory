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

<h2>Managing Users and Groups</h2>
Once the above setup is done, you are now ready to experiment with Active Directory.

Open the ***Active Directory Administrative Center (ADAC)***. You can find it by typing "active" into the Windows start menu.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902198449/in/dateposted-public/" title="adac"><img src="https://live.staticflickr.com/65535/53902198449_0b0175a73c_z.jpg" width="371" height="640" alt="adac"/></a>

The ***Active Directory Administrative Center*** allows you to manage your Active Directory installation, by configuring users, groups, computers, and more.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902290830/in/dateposted-public/" title="adac1"><img src="https://live.staticflickr.com/65535/53902290830_91df6f28c6_b.jpg" width="1024" height="483" alt="adac1"/></a>

For this lab, we want to create a new user called ***Alex***. To do that, first click on the ***example (local)*** entry. This is the entry for the domain that your account can manage.

To create a ***new user***, take a look at the tasks list on the right. Under the ***Users*** section, there's a ***New*** menu entry, which opens a submenu to select what's the type of entity that you want to create. In this case, we want to create a new user, so click on the ***User*** option.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902120913/in/dateposted-public/" title="new user"><img src="https://live.staticflickr.com/65535/53902120913_04d959f109_w.jpg" width="365" height="319" alt="new user"/></a>

This will open a new window that lets you fill in a number of fields related to the new user. There are a lot of fields available, but only a couple are mandatory (indicated with the red star). You can leave the rest empty. The user that we are creating is called ***Alex***, with their username being also ***alex***.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53900974462/in/dateposted-public/" title="create user"><img src="https://live.staticflickr.com/65535/53900974462_f18f13c838_b.jpg" width="996" height="589" alt="create user"/></a>

Once you've entered the necessary data, click the ***OK*** button to have the user created.

If you click on the newly created account, you will see that where it displays the name of the user, the system says ***Alex (Disabled)***.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902237549/in/dateposted-public/" title="alex diabled"><img src="https://live.staticflickr.com/65535/53902237549_da9f692ff5_o.jpg" width="892" height="477" alt="alex diabled"/></a>

What happens if you right click on the entry and try to ***Enable*** it?

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53900994442/in/dateposted-public/" title="enable"><img src="https://live.staticflickr.com/65535/53900994442_be7aee1feb.jpg" width="473" height="159" alt="enable"/></a>

The system will not enable an account that doesn't have a good password. In this case, the password is empty because we haven't set it. Obviously, an empty password is not a good password.

You can set a password using the ***Reset password*** menu option.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53901902316/in/dateposted-public/" title="reset password"><img src="https://live.staticflickr.com/65535/53901902316_a4b741eee1.jpg" width="277" height="500" alt="reset password"/></a>

Enter the password and confirm password into the ***Reset Password*** window, and ***User must change password at next logon*** option is already checked, we ensure that the user will change their password when they log in. So now click on the ***OK*** button to set the password. The goal of this is that after they've logged in once, the system administrator will not know their new password.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53901909301/in/dateposted-public/" title="user must change password"><img src="https://live.staticflickr.com/65535/53901909301_f83d1d3562_w.jpg" width="384" height="194" alt="user must change password"/></a>

Once you've set a good password, you can retry enabling the account. This time it should work.

Let's now add a new group. We now want to add 2 groups called ***Python Developers*** and ***Developers***, then add the account we just created for ***Alex*** to the ***Python Developers*** group.

To create a new group, use the same menu that you used for creating a new user, but this time select the new ***Group*** option.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902277394/in/dateposted-public/" title="new group"><img src="https://live.staticflickr.com/65535/53902277394_c6b8c94c63_w.jpg" width="365" height="321" alt="new group"/></a>

This will open a similar window to the one that we saw before, but this time it requires the data for the ***Group*** rather than the user.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902282954/in/dateposted-public/" title="python developers"><img src="https://live.staticflickr.com/65535/53902282954_285a121868_o.jpg" width="718" height="592" alt="python developers"/></a>

We are creating a group called ***Python Developers*** and that's the only data that is mandatory. You can also add additional information in the ***Description*** and ***Notes***, if you want. Once you are done, click ***OK*** to have the group created.

Repeat the same process to create the ***Developers*** group

We have a ***Python Developers*** group, now we want to add it to the ***Developers*** group. We can do this by scrolling down to the new entry and then right clicking on the entry in the list and selecting the ***Add to another group*** entry.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902386470/in/dateposted-public/" title="add group"><img src="https://live.staticflickr.com/65535/53902386470_4f4db1926e_b.jpg" width="1024" height="430" alt="add group"/></a>

This will open a small window where we need to enter the name of the group. In this case, the group is called ***Developers***.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902209638/in/dateposted-public/" title="developers"><img src="https://live.staticflickr.com/65535/53902209638_95196630fa.jpg" width="455" height="250" alt="developers"/></a>

You can use the ***Check Names*** button to verify that you have entered the name correctly. If you have, it will underline the text. If the name is incorrect, it will show a window saying "Name Not Found."

Clicking the ***OK*** button will add the ***Python Developers*** group to the ***Developers*** group. We now want to do the same for adding ***Alex*** to ***Python Developers***. But we'll follow a different path.

In this case, we will double click the ***Python Developers*** entry in the list, which will open up an editing window for the group.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53901059417/in/dateposted-public/" title="members"><img src="https://live.staticflickr.com/65535/53901059417_cd594f28e2.jpg" width="500" height="497" alt="members"/></a>

You can scroll down until you find the ***Members*** section of this window, or you can click on the ***Members*** link on the left. This section allows us to manually add or remove members from the group.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53901967476/in/dateposted-public/" title="add to group"><img src="https://live.staticflickr.com/65535/53901967476_ddd2561248.jpg" width="500" height="497" alt="add to group"/></a>

In this case, what we want to do is to add ***Alex*** to the group, so click the ***Add*** button, enter ***Alex*** in the text field and then ***OK*** for the addition and ***OK*** for saving the changes. We've successfully added a new member, ***Alex***, into the Group!

