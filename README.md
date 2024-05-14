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
1. Go to the [Oracle VirtualBox website](https://www.virtualbox.org/wiki/Downloads).
2. ![Oracle VirtualBox Download Page](https://www.virtualbox.org/wiki/Downloads)

### Install
1. Run the installer.
2. ![VirtualBox Installation](https://i.imgur.com/8f0v0E4.png)

### Extension Pack
1. Download the Extension Pack.
2. ![VirtualBox Extension Pack](https://i.imgur.com/8aqf9H2.png)

## Download Windows ISOs

### Windows 10 ISO
1. Go to the [Microsoft Windows 10 download page](https://www.microsoft.com/en-us/software-download/windows10ISO).
2. ![Windows 10 Download Page](https://www.microsoft.com/en-us/software-download/windows10ISO)
3. ![Windows 10 Download Process](https://i.imgur.com/dW1GJZN.png)

### Windows Server 2019 ISO
1. Go to the [Microsoft evaluation center for Windows Server 2019](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019).
2. ![Windows Server 2019 Download Page](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019)
3. ![Windows Server 2019 Download Process](https://i.imgur.com/3Cd2L4X.png)

## Create Virtual Machines in VirtualBox

### Domain Controller (Server 2019)
1. Open VirtualBox and click `New`.
2. ![New VM Wizard](https://i.imgur.com/5uVqftN.png)
3. Configure settings (name, OS type, RAM, and network adapters).
4. ![VM Settings](https://i.imgur.com/j3FIxxU.png)

### Client Machine (Windows 10)
1. Open VirtualBox and click `New`.
2. ![New VM Wizard](https://i.imgur.com/5uVqftN.png)
3. Configure settings (name, OS type, RAM, and network adapters).
4. ![VM Settings](https://i.imgur.com/j3FIxxU.png)

## Install Operating Systems

### Windows Server 2019
1. Start the `DC` VM and select the ISO.
2. ![Server 2019 Installation](https://i.imgur.com/AhNXXal.png)
3. Set a password for the Administrator account.
4. ![Server 2019 Setup](https://i.imgur.com/z5qXy65.png)

### Windows 10
1. Start the `Client1` VM and select the ISO.
2. ![Windows 10 Installation](https://i.imgur.com/wdKvWyL.png)
3. Create a local user account.
4. ![Windows 10 Setup](https://i.imgur.com/uqo1q1z.png)

## Configure the Domain Controller

### Set IP Addresses
1. Rename the network adapters.
2. Configure static IP for the internal network adapter.
3. ![Network Adapter Settings](https://i.imgur.com/cYMYfLV.png)
4. ![IP Configuration](https://i.imgur.com/O8QJtlf.png)

### Rename PC
1. Change the computer name to `DC`.
2. ![Rename PC](https://i.imgur.com/XoT0XEU.png)

### Install Active Directory Domain Services (AD DS)
1. Add the `Active Directory Domain Services` role.
2. Promote the server to a domain controller and create a new forest.
3. ![AD DS Role Installation](https://i.imgur.com/T4gnLje.png)
4. ![Promote to Domain Controller](https://i.imgur.com/kF6OpIc.png)

### Create Domain Admin Account
1. Open `Active Directory Users and Computers`.
2. Create an OU and a new user.
3. Add the user to the `Domain Admins` group.
4. ![AD Users and Computers](https://i.imgur.com/lEKI6WN.png)
5. ![Create OU](https://i.imgur.com/7Ubwvjv.png)
6. ![Create User](https://i.imgur.com/bXpDbuU.png)
7. ![Add to Domain Admins](https://i.imgur.com/8okdG5V.png)

## Configure Networking and Services

### Install and Configure NAT
1. Add the `Remote Access` role.
2. Configure NAT.
3. ![Remote Access Role Installation](https://i.imgur.com/FN7eZcU.png)
4. ![Configure NAT](https://i.imgur.com/VzM5o0m.png)

### Configure DHCP
1. Add the `DHCP Server` role.
2. Create a DHCP scope.
3. Set the router option.
4. ![DHCP Role Installation](https://i.imgur.com/7dV0XV2.png)
5. ![Create DHCP Scope](https://i.imgur.com/SOeDSEk.png)
6. ![Set Router Option](https://i.imgur.com/Y0t9A2X.png)

## Create User Accounts with PowerShell Script

### Script Preparation
1. Download and extract the PowerShell script and names file.
2. ![Downloaded Files](https://i.imgur.com/UfDNX8a.png)
3. ![Extracted Files](https://i.imgur.com/Wb7KuKl.png)

### Modify Script
1. Edit the `names.txt` file.
2. Review the PowerShell script in the PowerShell ISE.
3. ![Edit Names File](https://i.imgur.com/jjQ3KhE.png)
4. ![PowerShell Script](https://i.imgur.com/ODDtybw.png)

### Run Script
1. Set the execution policy to unrestricted.
2. Run the script.
3. ![Set Execution Policy](https://i.imgur.com/Fg1A5El.png)
4. ![Running Script](https://i.imgur.com/pNFWGAD.png)

## Configure Windows 10 Client

### Join Domain
1. Rename the computer to `Client1`.
2. Join the domain.
3. ![Rename Client](https://i.imgur.com/OxTZZOU.png)
4. ![Join Domain](https://i.imgur.com/Xbd6C54.png)

### Login with Domain Account
1. Use a domain account to log in.
2. ![Login with Domain Account](https://i.imgur.com/mu3UxtQ.png)

## Verify Configuration

### Network Connectivity
1. Ping the domain controller and an external website.
2. ![Ping Results](https://i.imgur.com/7QsX3P8.png)

### DHCP Lease
1. Check the DHCP leases on the domain controller.
2. ![DHCP Leases](https://i.imgur.com/Fw8B5a3.png)

### Active Directory
1. Verify created users and computers in Active Directory.
2. ![AD Users](https://i.imgur.com/E4xgS6x.png)
3. ![AD Computers](https://i.imgur.com/gfKONjQ.png)

---

By following these steps and capturing the corresponding screenshots, you will have a comprehensive visual guide for setting up an Active Directory lab in VirtualBox.
