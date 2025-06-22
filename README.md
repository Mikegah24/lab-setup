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


