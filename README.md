# IT Support Home Labs — L1/L2 Portfolio

5 self-hosted Windows Server labs simulating real L1/L2 IT support work — Active Directory design, Group Policy, file/print servers, Microsoft 365 & Entra ID hybrid sync, and full-cycle service desk ticketing (Atera) from onboarding to offboarding. Every task documented with screenshots and a written walkthrough, built to show hands-on competency, not just theory.

## About this repository

After completing my CompTIA A+ certification, I wanted practical, hands-on experience with the infrastructure that IT support and sysadmin teams actually manage day to day. I worked through *Entry Level IT Support Home Lab Projects for L1/L2 Engineers* by Om Luitel, rebuilding every lab myself in a virtualized Windows Server environment rather than just following along, then documented each project here.

## Projects

| # | Project | Key skills |
|---|---------|------------|
| 1 | [Active Directory OU Structure](01-Active-Directory-OU-Structure/README-project1.md) | AD OU design, user/group provisioning, hybrid Microsoft 365 sync |
| 2 | [Group Policy Management](02-Group-Policy-Management/README-project2.md) | GPO wallpaper deployment, account lockout policy, password policy |
| 3 | [File Server Management](03-File-Server-Management/README-project03.md) | NTFS & share permissions, security groups, Access-Based Enumeration, Shadow Copies |
| 4 | [Print Management](04-Print-Management/README-project4.md) | Print Server role, GPO printer deployment, Item-Level Targeting |
| 5 | [Service Desk Ticketing & User Lifecycle](05-Service-Desk-Ticketing-and-User-Lifecycle/README-project5.md) | Atera ticketing, Exchange mailbox delegation, onboarding/offboarding |

## Environment & tools

- **Windows Server** — Active Directory Domain Services, Group Policy Management, File and Storage Services, Print and Document Services
- **Windows 11** client machines
- **Microsoft 365 / Entra ID** — hybrid identity sync (Entra Connect)
- **Exchange Online** — shared mailboxes, delegation
- **Atera** — PSA / IT service desk ticketing
- **VMware Workstation** — lab virtualization

## How each project is documented

Every numbered folder contains its own `README.md` with:
- A role and environment summary
- A step-by-step walkthrough paired with screenshots
- A list of concrete skills demonstrated
- A short reflection on what the project taught me

## About me

Final-semester Computer Science student based in Ontario, looking to bring hands-on infrastructure and support experience into an IT Support, Junior Sysadmin, or Software role.
