# Active Directory Lab Setup in VirtualBox | Add Users w/PowerShell

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
2. **Explanation**: VirtualBox is the software that will allow us to create and run virtual machines (VMs) on your host computer. Downloading it from the official website ensures you get the latest version.

### Install
1. Run the installer.
2. **Explanation**: Installing VirtualBox on your computer sets up the necessary environment to create and manage VMs.

### Extension Pack
1. Download the Extension Pack.
2. **Explanation**: The Extension Pack adds additional functionalities to VirtualBox, such as USB 2.0/3.0 support, RDP, and more, enhancing the capabilities of your virtual machines.

## Download Windows ISOs

### Windows 10 ISO
1. Go to the Microsoft Windows 10 download page.
2. **Explanation**: The Windows 10 ISO will be used to create a client machine in your lab environment. This client will interact with the domain controller to simulate a networked environment.

### Windows Server 2019 ISO
1. Go to the Microsoft evaluation center for Windows Server 2019.
2. **Explanation**: The Windows Server 2019 ISO will be used to create the domain controller. This server will manage the Active Directory services, which is the core component of this lab.

## Create Virtual Machines in VirtualBox

### Domain Controller (Server 2019)
1. Open VirtualBox and click `New`.
2. **Explanation**: Creating a new VM in VirtualBox for the domain controller is the first step in setting up the lab environment.
3. Configure settings (name, OS type, RAM, and network adapters).
   - **Name and OS Type**: Properly naming the VM and selecting the correct OS type helps in managing and configuring the VM.
   - **RAM**: Allocating enough RAM ensures the VM runs smoothly without performance issues.
   - **Network Adapters**: Configuring the network adapters is crucial for setting up the network environment. The domain controller will need access to both the internet and the internal network.

### Client Machine (Windows 10)
1. Open VirtualBox and click `New`.
2. **Explanation**: Creating a new VM for the client machine sets up a workstation that will join the domain managed by the domain controller.
3. Configure settings (name, OS type, RAM, and network adapters).
   - **Name and OS Type**: Properly naming the VM and selecting the correct OS type helps in managing and configuring the VM.
   - **RAM**: Allocating enough RAM ensures the VM runs smoothly without performance issues.
   - **Network Adapter**: Configuring the network adapter to connect to the internal network is necessary for the client to communicate with the domain controller.

## Install Operating Systems

### Windows Server 2019
1. Start the `DC` VM and select the ISO.
2. **Explanation**: Booting from the Windows Server 2019 ISO allows you to install the server operating system on the VM.
3. Set a password for the Administrator account.
   - **Explanation**: Setting a password for the Administrator account secures the server and is required for administrative access.

### Windows 10
1. Start the `Client1` VM and select the ISO.
2. **Explanation**: Booting from the Windows 10 ISO allows you to install the client operating system on the VM.
3. Create a local user account.
   - **Explanation**: Creating a local user account is part of the Windows setup process and allows initial access to the client machine.

## Configure the Domain Controller

### Set IP Addresses
1. Rename the network adapters.
   - **Explanation**: Renaming the network adapters helps in identifying them easily during configuration.
2. Configure static IP for the internal network adapter.
   - **Explanation**: Assigning a static IP to the internal network adapter ensures consistent network communication within the lab environment.

### Rename PC
1. Change the computer name to `DC`.
   - **Explanation**: Renaming the domain controller to a recognizable name like `DC` makes it easier to identify within the network.

### Install Active Directory Domain Services (AD DS)
1. Add the `Active Directory Domain Services` role.
   - **Explanation**: Installing AD DS on the server is essential for setting up the domain controller and managing domain resources.
2. Promote the server to a domain controller and create a new forest.
   - **Explanation**: Promoting the server to a domain controller and creating a new forest sets up the Active Directory environment.

### Create Domain Admin Account
1. Open `Active Directory Users and Computers`.
2. Create an OU and a new user.
   - **Explanation**: Organizational Units (OUs) help in organizing and managing user accounts. Creating a new user account for administrative tasks ensures security and proper access control.
3. Add the user to the `Domain Admins` group.
   - **Explanation**: Adding the user to the `Domain Admins` group grants administrative privileges needed to manage the domain.

## Configure Networking and Services

### Install and Configure NAT
1. Add the `Remote Access` role.
   - **Explanation**: Adding the Remote Access role allows the server to manage network address translation (NAT), which is necessary for internal network clients to access external resources.
2. Configure NAT.
   - **Explanation**: Configuring NAT ensures that internal network traffic is properly routed to the internet.

### Configure DHCP
1. Add the `DHCP Server` role.
   - **Explanation**: The DHCP Server role is necessary for automatically assigning IP addresses to client machines within the internal network.
2. Create a DHCP scope.
   - **Explanation**: Creating a DHCP scope defines the range of IP addresses that the server can assign to clients.
3. Set the router option.
   - **Explanation**: Setting the router option ensures that clients receive the correct default gateway information, enabling proper network communication.

## Create User Accounts with PowerShell Script

### Script Preparation
1. Download and extract the PowerShell script and names file.
   - **Explanation**: The PowerShell script automates the creation of multiple user accounts, saving time and ensuring consistency.

### Modify Script
1. Edit the `names.txt` file.
   - **Explanation**: Adding your own name to the `names.txt` file personalizes the lab and ensures your account is created.
2. Review the PowerShell script in the PowerShell ISE.
   - **Explanation**: Reviewing the script helps in understanding its functionality and ensuring it meets your requirements.

### Run Script
1. Set the execution policy to unrestricted.
   - **Explanation**: Setting the execution policy allows the script to run without restrictions, which is necessary for it to execute properly.
2. Run the script.
   - **Explanation**: Running the script creates the user accounts in Active Directory.

## Configure Windows 10 Client

### Join Domain
1. Rename the computer to `Client1`.
   - **Explanation**: Renaming the client machine helps in identifying it within the network.
2. Join the domain.
   - **Explanation**: Joining the domain allows the client machine to be managed by the domain controller and access domain resources.

### Login with Domain Account
1. Use a domain account to log in.
   - **Explanation**: Logging in with a domain account verifies that the client machine is properly joined to the domain and that the user accounts are functional.

## Verify Configuration

### Network Connectivity
1. Ping the domain controller and an external website.
   - **Explanation**: Pinging the domain controller and an external website verifies network connectivity and proper configuration of the network settings.

### DHCP Lease
1. Check the DHCP leases on the domain controller.
   - **Explanation**: Checking the DHCP leases confirms that the client machine received an IP address from the DHCP server.

### Active Directory
1. Verify created users and computers in Active Directory.
   - **Explanation**: Verifying the created users and computers ensures that the PowerShell script executed correctly and that the Active Directory setup is functional.

---

By following these steps, you will have a comprehensive guide for setting up an Active Directory lab in VirtualBox.

## Skills and Technologies Learned

- **Active Directory and Windows Server Administration**: Gain hands-on experience in configuring and managing Active Directory Domain Services (AD DS), setting up a domain controller, creating and managing organizational units (OUs), user accounts, and group policies. Learn to deploy DHCP and DNS services within a Windows Server 2019 environment.

- **Virtualization and Networking**: Develop practical skills in using Oracle VirtualBox for creating and managing virtual machines (VMs). Learn to configure network settings, including NAT and internal networks, to simulate a real-world enterprise network. Understand IP addressing, DHCP scope creation, and network connectivity troubleshooting.

- **Automation with PowerShell**: Enhance your scripting abilities by using PowerShell to automate the creation and management of Active Directory user accounts. Learn to write and execute scripts to streamline administrative tasks, improving efficiency and demonstrating proficiency in automation within a Windows environment.
