# lab-setup

## Lab Overview

| VM Name | Role              | OS             | Hostname |
|---------|-------------------|----------------|----------|
| DC1     | Domain Controller | Windows Server | dc1      |
| CLIENT1 | Domain Member     | Windows 10     | client1  |

- **Domain**: `tech.lab`
- **Network**: 
- **Platform**: `Azure`

***NOTE*** : ***Make sure both VMs are in the same, resource group, Network(Virtual Network), and Region.***

### DC-1: Domain Controller
- Set the name to DC-1
- Region East US-2(if applicable)
- Image: Windows Server 2022 Data Center: Hot patch


<img src="https://github.com/user-attachments/assets/915a2fa7-bd4a-4c3f-bae4-694c41040b7a" height="35%" width="35%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/user-attachments/assets/2ed88557-6d94-475e-9a69-d58c0fda6185" height="35%" width="35%" alt="Disk Sanitization Steps"/>

`Machine Creation > Accept license > Network > Create`

### Client-1

- Repeat the same Steps as DC-1
- Set the disk image to `Windows 10 Prp`

<img src="https://github.com/user-attachments/assets/20aa4878-cbbd-4cc1-bf92-350fb54417f6" height="35%" width="35%" alt="Disk Sanitization Steps"/>

### Set DC-1 IP address to static

`Networking settings> Network Interface/ Ip configuration >  ip config > static`


<img src="https://github.com/user-attachments/assets/3cf34f23-a3f7-4426-b249-fec69a426074" height="20%" width="20%" alt="Disk Sanitization Steps"/>

<img src="https://github.com/user-attachments/assets/001706e6-670f-4a9a-b9bc-5e11e78ed6c3" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<img src="https://github.com/user-attachments/assets/98801a0b-708b-4586-8a58-0ce55085cfd7" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<img src="https://github.com/user-attachments/assets/885b59ad-1b68-4074-b4a6-8c07faa1df32" height="50%" width="50%" alt="Disk Sanitization Steps"/>

### Set Client-1 DNS server to DC-1 ip address

`Network settings > Network Interface/ Ip configuration > DNS servers > Custom > save`

<img src="https://github.com/user-attachments/assets/260d9797-0c32-42a7-b8c1-119303f114b1" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/user-attachments/assets/3e5b2a66-2e25-410f-9e0a-bfaea3ce1b3a" height="50%" width="50%" alt="Disk Sanitization Steps"/>



***At this stage, we’re ready to promote the server to a Domain Controller. This is where we install Active Directory Domain Services (AD DS) and create our new domain homelab.local. This step establishes the foundation for centralized user, group, and policy management across our network.***

- Login into the Domain Controller using Remote Desktop.
- Enter IP address of the Domain Controller and login.
- login name with and password

If prompted about security certificate problem just select yes.

<img src="https://github.com/user-attachments/assets/7ed441c2-230b-4c79-a6c8-574922b2afd1" height="35%" width="35%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/user-attachments/assets/3e5b2a66-2e25-410f-9e0a-bfaea3ce1b3a" height="50%" width="50%" alt="Disk Sanitization Steps"/>

***Once the machine has loaded we are ready to install Active Directory Services***

### Step 1.

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



