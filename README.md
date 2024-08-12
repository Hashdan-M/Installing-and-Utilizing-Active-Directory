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

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/adac1.jfif"/></a>

For this lab, we want to create a new user called ***Alex***. To do that, first click on the ***example (local)*** entry. This is the entry for the domain that your account can manage.

To create a ***new user***, take a look at the tasks list on the right. Under the ***Users*** section, there's a ***New*** menu entry, which opens a submenu to select what's the type of entity that you want to create. In this case, we want to create a new user, so click on the ***User*** option.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/new%20user.jfif"/></a>

This will open a new window that lets you fill in a number of fields related to the new user. There are a lot of fields available, but only a couple are mandatory (indicated with the red star). You can leave the rest empty. The user that we are creating is called ***Alex***, with their username being also ***alex***.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/create%20user.jfif"/></a>

Once you've entered the necessary data, click the ***OK*** button to have the user created.

If you click on the newly created account, you will see that where it displays the name of the user, the system says ***Alex (Disabled)***.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/alex%20diabled.jfif"/></a>

What happens if you right click on the entry and try to ***Enable*** it?

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/enable.jfif"/></a>

The system will not enable an account that doesn't have a good password. In this case, the password is empty because we haven't set it. Obviously, an empty password is not a good password.

You can set a password using the ***Reset password*** menu option.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/reset%20password.png"/></a>

Enter the password and confirm password into the ***Reset Password*** window, and ***User must change password at next logon*** option is already checked, we ensure that the user will change their password when they log in. So now click on the ***OK*** button to set the password. The goal of this is that after they've logged in once, the system administrator will not know their new password.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/user%20must%20change%20password.jfif"/></a>

Once you've set a good password, you can retry enabling the account. This time it should work.

Let's now add a new group. We now want to add 2 groups called ***Python Developers*** and ***Developers***, then add the account we just created for ***Alex*** to the ***Python Developers*** group.

To create a new group, use the same menu that you used for creating a new user, but this time select the new ***Group*** option.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/new%20group.jfif"/></a>

This will open a similar window to the one that we saw before, but this time it requires the data for the ***Group*** rather than the user.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/python%20developers.jfif"/></a>

We are creating a group called ***Python Developers*** and that's the only data that is mandatory. You can also add additional information in the ***Description*** and ***Notes***, if you want. Once you are done, click ***OK*** to have the group created.

Repeat the same process to create the ***Developers*** group.

We have a ***Python Developers*** group, now we want to add it to the ***Developers*** group. We can do this by scrolling down to the new entry and then right clicking on the entry in the list and selecting the ***Add to another group*** entry.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/add%20group.jfif"/></a>

This will open a small window where we need to enter the name of the group. In this case, the group is called ***Developers***.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/developers.jfif"/></a>

You can use the ***Check Names*** button to verify that you have entered the name correctly. If you have, it will underline the text. If the name is incorrect, it will show a window saying "Name Not Found."

Clicking the ***OK*** button will add the ***Python Developers*** group to the ***Developers*** group. We now want to do the same for adding ***Alex*** to ***Python Developers***. But we'll follow a different path.

In this case, we will double click the ***Python Developers*** entry in the list, which will open up an editing window for the group.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/members.jfif"/></a>

You can scroll down until you find the ***Members*** section of this window, or you can click on the ***Members*** link on the left. This section allows us to manually add or remove members from the group.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/add%20to%20group.jfif"/></a>

In this case, what we want to do is to add ***Alex*** to the group, so click the ***Add*** button, enter ***Alex*** in the text field and then ***OK*** for the addition and ***OK*** for saving the changes. We've successfully added a new member, ***Alex***, into the Group!

<h2>Managing Group Policies</h2>

To manage group policies, we need to use the ***Group Policy Management*** application. You can find it by typing group into the Windows start menu.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/gpo.jfif"/></a>

This application allows you to set policies that will manage the way machines in your domain behave. You can apply these policies to the whole domain or to separate ***Organizational Units*** (OUs).

In our case, we want to add a new policy to the ***Developers*** OU that already exists in the domain. To do that, expand the tree until you reach the ***example.com*** domain tree and find the ***Developers*** OU inside it.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/create%20gpo.jfif"/></a>

To create a new policy, right click on the ***Developers*** option and select the first menu entry: ***Create a GPO in this domain and Link it here***.

When you click this option, you will be prompted to set a name for the policy and once you do, the policy will get added to the OU.

<img src="(https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/new%20wallpaper.jfif)"/></a>

We want to set a default wallpaper for the machines in the Developers OU, so we will call our policy **"New Wallpaper"**

Once created, we want to edit the policy, to do this, right-click on the entry and click on the first menu entry: ***Edit***.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/editor.jfif"/></a>

This will open a new application: the ***Group Policy Management Editor***. This application allows you to navigate and configure all settings that can be set in a group policy.

As we want to set the wallpaper, we need to navigate to this setting by going to: ***User Configuration > Policies > Administrative Templates > Desktop > Desktop***

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/desktop%20wallpaper.jfif"/></a>

This opens a list of possible settings that we can configure, including the ***Desktop Wallpaper***. To set the wallpaper to a specific value, double-click on the ***Desktop Wallpaper*** entry.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/wallpaper%20name.jfif"/></a>

The window that opens allows you to set the value of the wallpaper. To do that, first click on the ***Enabled*** button and then enter a path for the wallpaper. The path could be a local path in the machine or a network path on a server that shares files.

 In the ***Wallpaper Name*** section, enter a path for the wallpaper. For this lab, our path is ****C:\qwiklabs\wallpaper.jpg****.

Once you click ***OK***, the group policy is created and contains the values we want. To verify this, go back to the ***Group Policy Management*** application and click the ***Settings*** tab of the new policy.

<img src="https://github.com/Hashdan-M/Installing-and-Utilizing-Active-Directory/blob/e41fa922649a506b4eebcb24e71e0d04c0837625/Active%20Directory/new%20wallpaper1.jfif"/></a>

<h2>Conclusion</h2>

We've now seen how to install Active Directory and manage users, groups and group policies. There's a lot more to learn about AD, but these skills are the building blocks for administering a fleet of Windows computers.
