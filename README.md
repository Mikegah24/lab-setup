<img src="https://github.com/user-attachments/assets/22c3bd7f-502f-4ea3-bd90-46030294f1a2" height="50%" width="50%" alt="Disk Sanitization Steps"/>

# On-Premises Active Directory Deployed in the Cloud (Azure)


This project outlines the implementation of on-premises Active Directory within Azure Virtual Machines.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Powershell

## Operating Sytems

- Windows Server 2022
- Windows 10 (21H2)


## Lab Overview

| VM Name | Role              | OS             | Hostname |
|---------|-------------------|----------------|----------|
| DC1     | Domain Controller | Windows Server | dc1      |
| CLIENT1 | Domain Member     | Windows 10     | client1  |

- **Domain**: `tech.lab`
- **Network**: `VNet`
- **Platform**: `Azure`

***NOTE*** : ***Make sure both VMs are in the same, resource group, Network(Virtual Network), and Region.***

# Step 1

### DC-1: Domain Controller
- Set the name to DC-1
- Region East US-2(if applicable)
- Image: Windows Server 2022 Data Center: Hot patch

- `Machine Creation > Accept license > Network > Create`



<img src="https://github.com/user-attachments/assets/915a2fa7-bd4a-4c3f-bae4-694c41040b7a" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/user-attachments/assets/2ed88557-6d94-475e-9a69-d58c0fda6185" height="50%" width="50%" alt="Disk Sanitization Steps"/>



### Client-1 Machine

- Repeat the same Steps as DC-1
- Set the disk image to `Windows 10 Pro`

<img src="https://github.com/user-attachments/assets/20aa4878-cbbd-4cc1-bf92-350fb54417f6" height="45%" width="45%" alt="Disk Sanitization Steps"/>

### Set DC-1 IP address to static

- `Networking settings> Network Interface/ Ip configuration >  ip config > static`


<img src="https://github.com/user-attachments/assets/3cf34f23-a3f7-4426-b249-fec69a426074" height="20%" width="20%" alt="Disk Sanitization Steps"/>

<img src="https://github.com/user-attachments/assets/001706e6-670f-4a9a-b9bc-5e11e78ed6c3" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<img src="https://github.com/user-attachments/assets/98801a0b-708b-4586-8a58-0ce55085cfd7" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<img src="https://github.com/user-attachments/assets/885b59ad-1b68-4074-b4a6-8c07faa1df32" height="50%" width="50%" alt="Disk Sanitization Steps"/>

# Step 2

### Set Client-1 DNS server to DC-1 ip address

- `Network settings > Network Interface/ Ip configuration > DNS servers > Custom > save`

<img src="https://github.com/user-attachments/assets/260d9797-0c32-42a7-b8c1-119303f114b1" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/user-attachments/assets/3e5b2a66-2e25-410f-9e0a-bfaea3ce1b3a" height="50%" width="50%" alt="Disk Sanitization Steps"/>



***At this stage, we’re ready to promote the server to a Domain Controller. This is where we install Active Directory Domain Services (AD DS) and create our new domain homelab.local. This step establishes the foundation for centralized user, group, and policy management across our network.***

# Step 3
- Login into the Domain Controller using Remote Desktop.
- Enter IP address of the Domain Controller and login.
- login name with and password

If prompted about security certificate problem just select yes.

<img src="https://github.com/user-attachments/assets/7ed441c2-230b-4c79-a6c8-574922b2afd1" height="35%" width="35%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/user-attachments/assets/3e5b2a66-2e25-410f-9e0a-bfaea3ce1b3a" height="50%" width="50%" alt="Disk Sanitization Steps"/>

***Once the machine has loaded we are ready to install Active Directory Services***

# Step 4

- On the server manager window, select Manage in the top right, then `Add roles and Features`
- Keep everything by default
- On the server `Select Server roles`, select, Active Directory and Domain Services, Add Features
- Accept restart the destination server automatically if required, Yes
- Then Install.

<img src="https://github.com/user-attachments/assets/0f4dd0f1-7660-47e2-8c72-6de176b3beb6" height="700%" width="700%" alt="Disk Sanitization Steps"/>

<img src="https://github.com/user-attachments/assets/d7d9934d-626b-4cbd-aae5-208806c07b5b" height="50%" width="50%" alt="Disk Sanitization Steps"/>


- **Now Promote promote the server by select the flag in the top right, and Promote**
- Select, add a new forest
- Now you name the Domain, Root domain name: `tech.lab` (or the name of your choice)
- Set a DSRM password
- You dont have to create a DNS delegation
- Install
- The DC will restart and you might lose connection.

<img src="https://github.com/user-attachments/assets/8ebc6dea-f7cf-4bb9-a80d-15d3e668508c" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<img src="https://github.com/user-attachments/assets/083194f4-61df-4057-a638-9790ed5f7366" height="50%" width="50%" alt="Disk Sanitization Steps"/>

# Step 5
## Now we can attach the Client computer to the DC
- Start the machine and login via Remote Desktop.
- Go to System, Advanced System Settings.
- System properties, Computer name, change name to Client-1, Select Change.
- On `Memeber of`, select Domain, and Enter domain name of the DC we created.
- Then, Enter domain account name and password
- IF successful, You shoud see a "Welcome to the tech.lab domain" prompt, then restart.

<img src="https://github.com/user-attachments/assets/265cec82-bb2b-45e7-8596-8b90ffd1562f" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<img src="https://github.com/user-attachments/assets/9cc540a0-0b4b-435e-a438-0e9dadec737d" height="50%" width="50%" alt="Disk Sanitization Steps"/>

**From now to login to the client you will have to do**: `tech.lab\your user account`

Just like this:

<img src="https://github.com/user-attachments/assets/d689eee8-320b-48e4-ab2d-a0a066119b03" height="35%" width="35%" alt="Disk Sanitization Steps"/>

### Verify that Client-1 is now part of the Domain...

- On the start menu, Select `Windows Administrative Tools Drop-down`
- Select Active Directory Users and Computers
- Select Drop-down on the domain controller
- Select Computers, and you should see Client-1.

<img src="https://github.com/user-attachments/assets/7ebd74f7-7093-465d-be25-70654f1a899c" height="50%" width="50%" alt="Disk Sanitization Steps"/>


***AND JUST LIKE THAT WE HAVE OUR DOMAIN AND USER COMPUTER SETUP!!!!!!!!!!!!!!***
