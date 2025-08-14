# Active Directory (AD) Homelab Project: Windows Server 2022

## 🎯 Project Goal

The primary goal of this project is to learn and understand Active Directory (AD) operations, Windows Server management, and network configuration. This serves as a personal homelab journey and a portfolio piece for future IT internships or job opportunities.

> **Disclaimer:** This is a learning environment and a lab setup. The configurations are not up to production safety standards, and security measures are intentionally simplified to focus on foundational concepts.

## 💻 Network Topology

The network for this project consists of three virtual machines (VMs) connected via NAT to the internet:

- One Windows Server 2022 VM for Active Directory
- One Windows Server VM for Splunk (future implementation)
- One Windows Desktop VM (client)

## ⚙️ Initial Server Setup

The first step is to set up the Windows Server 2022 VM.

### 1. Installation

1. Download the Windows Server 2022 ISO
2. Use VirtualBox to perform a fresh installation

### 2. Renaming the Computer

After installation, it's good practice to rename the computer from its default, random name to something more descriptive.

1. Go to **File Explorer** > right-click **"This PC"** > select **"Properties"**
2. Find and click **"Rename this PC"**
3. Change the name to something like `WinServer`. The PC will need to restart

### 3. Performance Settings

To ensure the VM runs smoothly, the performance settings were adjusted.

1. In the same **"Properties"** page, scroll down and find **"Advanced system settings"**
2. In the new window, go to the **"Advanced"** tab, find the **"Performance"** section, and click **"Settings"**
3. Choose **"Adjust for best performance"**

### 4. Static IP Configuration

A server should always have a static IP address.

1. Go to **Control Panel** > **Network and Sharing Center** > **Change adapter settings**
2. Right-click the network adapter and select **"Properties"**
3. Select **"Internet Protocol Version 4 (TCP/IPv4)"** and click **"Properties"**
4. Manually enter the IP address, Subnet mask, Default gateway, and DNS server address
5. Run `ipconfig` in the Command Prompt to verify the settings

## 🖥️ Active Directory & DNS Installation

Before installing AD, ensure the server has a strong administrator password and is updated.

### 1. Adding Roles

1. Open **Server Manager**
2. Go to **"Manage"** and select **"Add Roles and Features"**
3. Choose **"Role-based or feature-based installation"**
4. Select **"Active Directory Domain Services"** and **"DNS Server"**. DNS is crucial for AD to function correctly
5. Click **"Next"** and proceed with the default settings to install

### 2. Promoting to Domain Controller

After the roles are installed, the standalone server needs to be promoted to a domain controller. This process creates the Active Directory database, configures the domain, and integrates DNS.

1. In **Server Manager**, a notification will appear to **"Promote this server to a domain controller"**
2. Select **"Add a new forest"** and specify a **"Root domain name"** (e.g., `lab.local`)
3. Set a **DSRM (Directory Services Restore Mode)** password. This is a special password used for repairing or restoring AD
4. Complete the wizard, and the server will reboot

### 3. DNS Verification

After the reboot, it's important to verify that DNS is working.

1. Open **Command Prompt** and run:
   ```cmd
   nslookup lab.local
   nslookup google.com
   ```

A successful lookup of both will confirm that AD is resolving your local domain and that you have internet connectivity.
