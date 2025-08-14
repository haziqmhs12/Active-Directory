# 👥 User Management

This section covers basic user management within the domain.

## 1. Creating a User by Copying

Copying an existing user is the fastest way to create a new user with the same privileges.

### Steps:
1. Open **Active Directory Users and Computers**
2. In the **"Users"** folder, right-click an existing user (e.g., Administrator) and select **"Copy"**
3. Fill in the new user's details and set a password

<div align="center">
   
![Create Copy](images/Create%20Copy.jpg)
</div>

> **Note:** The new user will have the same group memberships as the user you copied.

<div align="center">
   
![Result Copy](images/Result%20Copy.jpg)
</div>

## 2. Creating a User from Scratch

### Steps:
1. In the **"Users"** folder, right-click and select **"New"** > **"User"**
2. Fill in the user's information

<div align="center">
   
![Create Scratch](images/Create%20Scratch.jpg)
</div>

> **Note:** By default, this user will only be a member of Domain Users. You'll need to manually add them to any other groups (e.g., Administrators) as needed.

### Adding User to Groups:
1. Right-click the user and select **"Properties"**
2. Go to the **"Member Of"** tab
3. Click **"Add"** to assign the user to additional groups

<div align="center">

![Assign New Member](images/Asign%20New%20Member.jpg)
</div>

## 3. Enabling the Recycle Bin

The Active Directory Recycle Bin allows for the recovery of accidentally deleted objects.

### Steps:
1. Open **Active Directory Administrative Center**
2. Select your domain and click **"Enable Recycle Bin"** in the right-hand pane

<div align="center">

![Enable Recycle Bin](images/Enable%20Recycle%20Bin.jpg)
</div>

### If you receive an "Insufficient access rights" error:

<div align="center">
  
![Error Recycle Bin](images/Error%20Recycle%20Bin.jpg)
</div>

1. You'll need to add your account to the **"Enterprise Admins"** group
2. Open the properties of the user account
3. Go to the **"Member Of"** tab and add **"Enterprise Admins"**
<div align="center">
  
![Add Privilege](images/Add%20Priviledge.jpg)
</div>
4. Reboot the server

### After reboot:
- You can enable the recycle bin
- A new container called **"Deleted Objects"** will appear, where you can restore any deleted items
<div align="center">
  
![Recycle Bin](images/Recycle%20Bin.jpg)
</div>
