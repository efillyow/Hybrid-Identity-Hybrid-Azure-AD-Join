🏗️ Hybrid Identity + Hybrid Azure AD Join Lab

📌 Overview
This project simulates a real-world enterprise hybrid identity environment by integrating on-premises Active Directory with Microsoft Entra ID using Microsoft Entra Connect Sync.
The lab demonstrates:

Active Directory deployment in Azure
Identity synchronization to Entra ID
Hybrid Azure AD Join
Group Policy-based automation for device registration
Troubleshooting real-world hybrid join issues


🎯 Objectives

Deploy domain controller in Azure (DC01)
Create domain (corp.lab)
Sync users from AD → Entra ID
Configure Hybrid Azure AD Join
Automate device join using Group Policy
Validate device authentication
Troubleshoot hybrid join failures


🏗️ Architecture
DC01 (AD DS)
   ↓
Microsoft Entra Connect
   ↓
Microsoft Entra ID
   ↓
CLIENT01 / CLIENT02
(Hybrid Joined Devices)


🔧 Technologies Used

Microsoft Azure Virtual Machines
Active Directory Domain Services (AD DS)
Microsoft Entra ID
Microsoft Entra Connect Sync
Group Policy
Windows 10/11


⚙️ Configuration & Implementation

✅ Azure VM Deployment
Deployed virtual machines:

DC01 (Domain Controller)
CLIENT01 (initial test device)
CLIENT02 (automation validation)

📸
Screenshots/VMs-Created-DC01-CLIENT01-CLIENT02.png

✅ Active Directory Configuration

Installed AD DS
Created domain: corp.lab
Created user: etest

📸
Screenshots/ADUser-Signed-Into-OnPrem-VM-CLIENT01.png

✅ Domain Join
Joined CLIENT devices to domain.
📸
Screenshots/CLIENT01-Domain-Join-Success.png

✅ Remote Access Configuration
Configured RDP access for domain user.
📸
Screenshots/Allow-DomainUser-to-RemoteTo-CLIENT01.png

✅ Entra Connect Sync
Configured identity synchronization.
📸
Screenshots/Microsoft-Entra-Connect-Sync-Configuring.png
📸
Screenshots/ENTRA-User-Synced.png

✅ Hybrid Azure AD Join (Manual Validation)
Verified hybrid join using:
dsregcmd /status

📸
Screenshots/CLIENT01-Device-AzureAD-Joined-dsregcmdstatus.png

✅ Group Policy Automation
Created GPO:
Hybrid-AAD-Join

Enabled:
Register domain-joined computers as devices

📸
Screenshots/GPO-Hybrid-Join.png

✅ Automated Device Join (CLIENT02)
Tested automation using a fresh device:

Joined to domain
GPO applied automatically
Device successfully hybrid joined

📸
Screenshots/CLIENT02-Joined-Via-GPO.png

🧪 Testing & Validation





























ScenarioResultDomain Join✅ SuccessUser Sync✅ SuccessHybrid Join✅ SuccessGPO Application✅ SuccessAutomated Join✅ Success

🧠 Troubleshooting Highlights
🔴 Issue: Hybrid Join Failed (Event ID 304)
Error:
Device object not found

✅ Fix:

Forced Entra sync
Waited for device object creation


🔴 Issue: GPO Not Applying
✅ Fix:
gpresult /r /scope computer

Verified GPO applied correctly

🔴 Issue: DNS Resolution
✅ Fix:

Configured DC01 DNS forwarders
Ensured Azure endpoints resolved


🎯 Outcome

Successfully implemented hybrid identity
Automated device registration via GPO
Validated enterprise device onboarding process
Troubleshot real-world hybrid identity issues


💼 Skills Demonstrated

Active Directory Administration
Azure Infrastructure Deployment
Hybrid Identity Configuration
Group Policy Automation
Endpoint Identity Management
Troubleshooting (Event Viewer, Sync, GPO)
