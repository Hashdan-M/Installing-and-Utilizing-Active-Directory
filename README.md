<img src="https://janikvonrotz.ch/wp-content/uploads/2017/10/Active-Directory-Logo.jpg" width=37.5% height=37.5%>

<h1>Installing & Utilizing Active Directory</h1>

<h2>Description</h2>
Active Directory is a core tool for system administrators who need to manage Windows machines. Active Directory allows us to manage users, groups, machines, and the policies that apply to all of them in a centralized fashion.
In this lab, we'll install Active Directory, use it to add users and groups, edit users memberships as well as create a new group policy object (GPO).

<h2>Installing Active Directory</h2>
To install Active Directory (AD) on a Windows Server, follow these steps. This guide assumes you are using Windows Server 2019 or Windows Server 2022, but the process is similar for other recent versions. You can use virtualization software such as Virtualbox or VMWare to install the Windows OS inside of your PC.

### Prerequisites

1. **Server Operating System**: Ensure you have Windows Server installed.
2. **Static IP Address**: Set a static IP address for your server.
3. **Server Name**: Make sure your server has a unique name within your network.
4. **Administrative Privileges**: Ensure you have administrative rights to install software and configure settings.

### Installation Steps

#### 1. **Open Server Manager**

- Click on the **Start** button and open **Server Manager**.
- Alternatively, you can press `Windows + R`, type `servermanager`, and press Enter.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/server%20manager.jpg"/></a>

#### 2. **Add Roles and Features**

- In Server Manager, click on **Manage** in the top right corner and select **Add Roles and Features**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/roles%20and%20features.jpg"/></a>

- Click **Next** on the **Before You Begin** page.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/before%20you%20begin.jpg"/></a>

#### 3. **Select Installation Type**

- Choose **Role-based or feature-based installation** and click **Next**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/installation%20type.jpg"/></a>

#### 4. **Select Destination Server**

- Choose the server from the server pool where you want to install AD DS (Active Directory Domain Services) and click **Next**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/server%20selection.jpg"/></a>

#### 5. **Select Server Roles**

- On the **Select server roles** page, check **Active Directory Domain Services**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/select%20server%20roles.jpg"/>

- A dialog box will appear prompting you to add features required for AD DS. Click **Add Features**.
- Click **Next**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/add%20features.jpg"/></a>

#### 6. **Select Features**

- You can generally leave the default features selected. Click **Next**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/next.jpg"/></a>

#### 7. **AD DS Information**

- Review the information about AD DS. Click **Next**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/domain%20services.jpg"/></a>

#### 8. **Confirmation**

- Review your selections. Click **Install** to begin the installation.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/confirm.jpg"/></a>

- The installation will proceed, and once it's completed, you’ll see a notification indicating that the installation was successful.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/installation%20progress.jpg"/></a>

#### 9. **Promote the Server to a Domain Controller**

- After the installation, a notification will appear in Server Manager indicating that **Post-installation tasks** are needed. Click on **Promote this server to a domain controller**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/promote%20to%20dc.png"/></a>

#### 10. **Configure AD DS**

- In the **Deployment Configuration** window:
  - **Add a new forest** if this is your first domain controller. Enter the **Root domain name** (e.g., `example.local`).
  - If you are adding a domain controller to an existing domain, select **Add a domain controller to an existing domain** and provide the necessary domain details.

- Click **Next**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/deployment%20configuration.png"/></a>

#### 11. **Domain Controller Options**

- Configure the domain controller options, including:
  - **Forest functional level**: Choose the appropriate level based on your needs.
  - **Domain functional level**: Choose the appropriate level based on your needs.
  - **Global Catalog** and **Read-Only Domain Controller (RODC)** options.
  - Set the **Directory Services Restore Mode (DSRM) password**.

- Click **Next**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/domain%20configuration%20options.png"/></a>

#### 12. **DNS Options**

- Review the DNS options and click **Next**. If you encounter warnings about DNS delegation, you can usually proceed by addressing these later.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/dns%20options.png"/></a>

#### 13. **Additional Options**

- Review additional options, such as the NetBIOS domain name. Click **Next**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/additional%20options.png"/></a>

#### 14. **Paths**

- Choose the paths for the AD database, log files, and SYSVOL folder. The default paths are generally fine. Click **Next**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/database%20path.png"/></a>

#### 15. **Review Options**

- Review your selections and click **Next**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/review%20options.png"/></a>

#### 16. **Prerequisites Check**

- The installer will perform a prerequisites check. Ensure all checks pass. Click **Install**.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/prerequisites%20check.png"/></a>

#### 17. **Reboot**

- The server will automatically reboot once the installation and configuration are complete.

<h2>Managing Users and Groups</h2>
Once the above setup is done, you are now ready to experiment with Active Directory.

Open the ***Active Directory Administrative Center (ADAC)***. You can find it by typing "active" into the Windows start menu.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/a79e2327bb9356dc120dcca6adc375695e27f8a9/Active%20Directory/adac.jfif"/></a>

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

Repeat the same process to create the ***Developers*** group.

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

<h2>Managing Group Policies</h2>

To manage group policies, we need to use the ***Group Policy Management*** application. You can find it by typing group into the Windows start menu.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53901085647/in/dateposted-public/" title="gpo"><img src="https://live.staticflickr.com/65535/53901085647_9c3e43dafe_o.jpg" width="392" height="681" alt="gpo"/></a>

This application allows you to set policies that will manage the way machines in your domain behave. You can apply these policies to the whole domain or to separate ***Organizational Units*** (OUs).

In our case, we want to add a new policy to the ***Developers*** OU that already exists in the domain. To do that, expand the tree until you reach the ***example.com*** domain tree and find the ***Developers*** OU inside it.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902348679/in/dateposted-public/" title="create gpo"><img src="https://live.staticflickr.com/65535/53902348679_7d6d669768_o.jpg" width="1076" height="528" alt="create gpo"/></a>

To create a new policy, right click on the ***Developers*** option and select the first menu entry: ***Create a GPO in this domain and Link it here***.

When you click this option, you will be prompted to set a name for the policy and once you do, the policy will get added to the OU.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902441080/in/dateposted-public/" title="new wallpaper"><img src="https://live.staticflickr.com/65535/53902441080_64b0468376_o.jpg" width="752" height="527" alt="new wallpaper"/></a>

We want to set a default wallpaper for the machines in the Developers OU, so we will call our policy **"New Wallpaper"**

Once created, we want to edit the policy, to do this, right-click on the entry and click on the first menu entry: ***Edit***.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902449480/in/dateposted-public/" title="editor"><img src="https://live.staticflickr.com/65535/53902449480_3d0c10bd16_b.jpg" width="1024" height="505" alt="editor"/></a>

This will open a new application: the ***Group Policy Management Editor***. This application allows you to navigate and configure all settings that can be set in a group policy.

As we want to set the wallpaper, we need to navigate to this setting by going to: ***User Configuration > Policies > Administrative Templates > Desktop > Desktop***

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53903629153/in/dateposted-public/" title="desktop wallpaper"><img src="https://live.staticflickr.com/65535/53903629153_ea6efe94a8_b.jpg" width="988" height="566" alt="desktop wallpaper"/></a>

This opens a list of possible settings that we can configure, including the ***Desktop Wallpaper***. To set the wallpaper to a specific value, double-click on the ***Desktop Wallpaper*** entry.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53902477237/in/dateposted-public/" title="wallpaper name"><img src="https://live.staticflickr.com/65535/53902477237_20ee80d659_z.jpg" width="640" height="594" alt="wallpaper name"/></a>

The window that opens allows you to set the value of the wallpaper. To do that, first click on the ***Enabled*** button and then enter a path for the wallpaper. The path could be a local path in the machine or a network path on a server that shares files.

 In the ***Wallpaper Name*** section, enter a path for the wallpaper. For this lab, our path is ****C:\qwiklabs\wallpaper.jpg****.

Once you click ***OK***, the group policy is created and contains the values we want. To verify this, go back to the ***Group Policy Management*** application and click the ***Settings*** tab of the new policy.

<a data-flickr-embed="true" href="https://www.flickr.com/photos/201152865@N02/53903642748/in/dateposted-public/" title="new wallpaper"><img src="https://live.staticflickr.com/65535/53903642748_f67efe8bfc_b.jpg" width="1024" height="428" alt="new wallpaper"/></a>

<h2>Conclusion</h2>

We've now seen how to install Active Directory and manage users, groups and group policies. There's a lot more to learn about AD, but these skills are the building blocks for administering a fleet of Windows computers.
