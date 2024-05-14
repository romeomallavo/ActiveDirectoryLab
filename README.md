# Active Directory Lab Setup in VirtualBox

This guide provides step-by-step instructions for setting up an Active Directory lab environment using VirtualBox. The lab includes a Windows Server 2019 domain controller and a Windows 10 client machine.

## Table of Contents

1. [Install Oracle VirtualBox](#install-oracle-virtualbox)
2. [Download Windows ISOs](#download-windows-isos)
3. [Create Virtual Machines in VirtualBox](#create-virtual-machines-in-virtualbox)
4. [Install Operating Systems](#install-operating-systems)
5. [Configure the Domain Controller](#configure-the-domain-controller)
6. [Configure Networking and Services](#configure-networking-and-services)
7. [Create User Accounts with PowerShell Script](#create-user-accounts-with-powershell-script)
8. [Configure Windows 10 Client](#configure-windows-10-client)
9. [Verify Configuration](#verify-configuration)

## Install Oracle VirtualBox

### Download
1. Go to the Oracle VirtualBox website.
2. Capture a screenshot of the download page.

### Install
1. Run the installer.
2. Capture a screenshot of the installation process.

### Extension Pack
1. Download the Extension Pack.
2. Capture a screenshot of the download and installation of the Extension Pack.

## Download Windows ISOs

### Windows 10 ISO
1. Go to the Microsoft Windows 10 download page.
2. Capture a screenshot of the page where you select the version and language.
3. Capture a screenshot of the download process.

### Windows Server 2019 ISO
1. Go to the Microsoft evaluation center for Windows Server 2019.
2. Capture a screenshot of the page where you select the ISO.
3. Capture a screenshot of the download process.

## Create Virtual Machines in VirtualBox

### Domain Controller (Server 2019)
1. Open VirtualBox and click `New`.
2. Capture a screenshot of the New Virtual Machine wizard.
3. Configure settings (name, OS type, RAM, and network adapters).
4. Capture a screenshot of the configured settings.

### Client Machine (Windows 10)
1. Open VirtualBox and click `New`.
2. Capture a screenshot of the New Virtual Machine wizard.
3. Configure settings (name, OS type, RAM, and network adapters).
4. Capture a screenshot of the configured settings.

## Install Operating Systems

### Windows Server 2019
1. Start the `DC` VM and select the ISO.
2. Capture a screenshot of the OS installation steps.
3. Set a password for the Administrator account.
4. Capture a screenshot of the completed installation and initial setup.

### Windows 10
1. Start the `Client1` VM and select the ISO.
2. Capture a screenshot of the OS installation steps.
3. Create a local user account.
4. Capture a screenshot of the completed installation and initial setup.

## Configure the Domain Controller

### Set IP Addresses
1. Rename the network adapters.
2. Configure static IP for the internal network adapter.
3. Capture screenshots of the network adapter settings and IP configuration.

### Rename PC
1. Change the computer name to `DC`.
2. Capture a screenshot of the rename process.

### Install Active Directory Domain Services (AD DS)
1. Add the `Active Directory Domain Services` role.
2. Promote the server to a domain controller and create a new forest.
3. Capture screenshots of each step in the AD DS installation and configuration process.

### Create Domain Admin Account
1. Open `Active Directory Users and Computers`.
2. Create an OU and a new user.
3. Add the user to the `Domain Admins` group.
4. Capture screenshots of creating the OU, the user, and adding the user to the `Domain Admins` group.

## Configure Networking and Services

### Install and Configure NAT
1. Add the `Remote Access` role.
2. Configure NAT.
3. Capture screenshots of the role installation and NAT configuration.

### Configure DHCP
1. Add the `DHCP Server` role.
2. Create a DHCP scope.
3. Set the router option.
4. Capture screenshots of the DHCP server setup and scope configuration.

## Create User Accounts with PowerShell Script

### Script Preparation
1. Download and extract the PowerShell script and names file.
2. Capture screenshots of the downloaded files and extraction process.

### Modify Script
1. Edit the `names.txt` file.
2. Review the PowerShell script in the PowerShell ISE.
3. Capture screenshots of the script and names file.

### Run Script
1. Set the execution policy to unrestricted.
2. Run the script.
3. Capture screenshots of the script running and the resulting user creation.

## Configure Windows 10 Client

### Join Domain
1. Rename the computer to `Client1`.
2. Join the domain.
3. Capture screenshots of the rename process and domain join steps.

### Login with Domain Account
1. Use a domain account to log in.
2. Capture screenshots of the login process.

## Verify Configuration

### Network Connectivity
1. Ping the domain controller and an external website.
2. Capture screenshots of the command prompt with the ping results.

### DHCP Lease
1. Check the DHCP leases on the domain controller.
2. Capture a screenshot of the DHCP leases showing the client machine.

### Active Directory
1. Verify created users and computers in Active Directory.
2. Capture screenshots of the users and computers in Active Directory.

---

By following these steps and capturing the corresponding screenshots, you will have a comprehensive visual guide for setting up an Active Directory lab in VirtualBox.
