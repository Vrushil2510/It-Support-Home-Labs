# Project 5 – Service Desk Ticketing & User Lifecycle Management

**Role simulated:** System Administrator
**Environment:** Atera PSA/ticketing platform, Microsoft 365 admin center, Exchange admin center, Microsoft Entra ID, and on-premises Active Directory (WAT-DC-01) in a hybrid-synced domain (LabConestoga.local / labconestoga.store), accessed from both technician and end-user (Windows 11 client) perspectives.

## Overview
This project simulates a full IT service desk workflow using Atera as the ticketing platform, covering three connected support tickets: a shared mailbox access request, a new employee's onboarding, and that same employee's eventual offboarding. It shows how a single support ticket triggers real changes across Active Directory, Microsoft Entra ID, Exchange Online, and Microsoft 365 licensing — and how those changes get verified and documented before a ticket is closed.

## Skills demonstrated
- IT service desk ticket management using Atera (creation, triage, replies, internal notes, resolution)
- End-user support communication, including requesting proper manager approval before granting access
- Exchange Online shared mailbox delegation (Full Access and Send As permissions)
- Permission validation through direct end-user testing rather than assuming a change worked
- New user onboarding: AD account creation, organizational attributes, manager assignment, and security group membership
- Microsoft 365 licence assignment and management
- Hybrid identity synchronization using Microsoft Entra Connect and Start-ADSyncSyncCycle
- User offboarding: mailbox-to-shared conversion, licence removal, and account disablement
- IT documentation practices, including internal ticket notes kept separate from customer-facing replies
- Cross-platform administration spanning Atera, Exchange admin center, Microsoft 365 admin center, Entra admin center, and on-prem Active Directory

## Walkthrough
### 1. Explored the Atera service desk from both the admin and customer perspective
Reviewed the Atera admin portal, including Service Portal configuration options, alongside the end-user-facing Atera customer portal where Harry H could view and submit his own support tickets.
![Atera admin portal and Harry's customer ticket portal side by side](screenshots/01-explore-atera-admin-portal-and-customer-view.png)

### 2. Submitted a ticket requesting shared mailbox access
As Harry H, submitted a new ticket through the Atera customer portal requesting access to the HR@LabConestoga.store shared mailbox.
![New ticket form requesting shared mailbox access](screenshots/02-harry-submits-shared-mailbox-access-request.png)

### 3. Verified the ticket was created
Confirmed the new ticket (#2 – Request for shared mailbox access) appeared correctly in both the technician's ticket queue and Harry's own My Tickets view.
![Ticket #2 visible in both the admin queue and customer portal](screenshots/03-verify-ticket-created-admin-and-customer-view.png)

### 4. Requested access level details and manager approval
As the assigned technician, replied to the ticket asking Harry to specify the exact level of access required and to attach his manager's approval before any access was granted — a basic access-control checkpoint.
![Technician reply requesting access level and manager approval](screenshots/04-technician-requests-access-level-and-approval.png)

### 5. Reviewed the technician's reply as the end user
Logged in as Harry and reviewed the technician's reply in Outlook, confirming the notification-to-email integration between Atera and the mailbox was working.
![Harry reading the technician's reply email in Outlook](screenshots/05-harry-reads-technician-reply-in-outlook.png)

### 6. Replied with the requested details and approval
As Harry, replied via Outlook specifying that Full Access and Send As permissions were needed, with the manager's approval attached as requested.
![Harry's Outlook reply specifying access requirements](screenshots/06-harry-replies-with-access-details-and-approval.png)

### 7. Confirmed the ticket was updated with Harry's reply
Verified Harry's reply synced back into the ticket conversation, with the ticket status remaining Open while awaiting technician action.
![Ticket conversation updated with Harry's reply](screenshots/07-ticket-updated-with-harry-reply-awaiting.png)

### 8. Reviewed the HR shared mailbox in Exchange admin center
Opened the HR shared mailbox in Exchange admin center to review its general details before making any permission changes.
![HR shared mailbox general settings in Exchange admin center](screenshots/08-review-hr-shared-mailbox-general-settings.png)

### 9. Granted Harry Full Access and Send As permissions
Added Harry H as a delegate on the HR shared mailbox, granting both Send As and Full Access (Read and manage) permissions as he had requested.
![Send As and Full Access permissions granted to Harry](screenshots/09-grant-harry-full-access-and-send-as-permissions.png)

### 10. Closed the ticket confirming access was granted
Replied to the ticket confirming that access to the HR shared mailbox had been provisioned, then closed the ticket.
![Ticket closed with confirmation reply](screenshots/10-close-ticket-confirming-mailbox-access-granted.png)

### 11. Tested the new access from Harry's account
As Harry, used Outlook's "Open another mailbox" feature to test whether the newly granted permissions actually worked.
![Open another mailbox dialog in Outlook](screenshots/11-harry-tests-access-open-another-mailbox.png)

### 12. Verified successful access to the shared mailbox
Confirmed Harry could successfully open and browse the HR shared mailbox, validating that the permissions were applied correctly.
![HR shared mailbox opened successfully in Harry's Outlook](screenshots/12-verify-harry-successfully-opens-hr-mailbox.png)

### 13. Documented the resolution with an internal note
Added an internal note to the ticket, not visible to the customer, summarizing the exact steps taken: logging into Exchange admin center, locating the mailbox, and granting the specific permissions — good ITSM record-keeping practice.
![Internal note documenting the resolution steps](screenshots/13-internal-note-documenting-mailbox-access-steps.png)

### 14. Submitted an onboarding request for a new hire
As Harry (now acting as the hiring manager), submitted a new ticket requesting the onboarding of a new Junior HR Officer, Andrew Smith, including a request to grant him access to the HR shared mailbox.
![Onboarding request ticket for new hire Andrew Smith](screenshots/14-harry-submits-onboarding-request-andrew-smith.png)

### 15. Created the new user's Active Directory account
Created Andrew Smith's user account in Active Directory under the HR Department OU and recorded his initial login credentials for secure handoff.
![New Object - User wizard creating Andrew Smith's AD account](screenshots/15-create-ad-user-account-andrew-smith.png)

### 16. Set the new user's organizational details
Configured Andrew Smith's Job Title, Department, and Manager (Harry H) on the Organization tab of his AD user properties.
![Andrew Smith's Organization tab in Active Directory](screenshots/16-set-andrew-smith-organization-details-and-manager.png)

### 17. Added the new user to the HR_Team security group
Added Andrew Smith to the HR_Team security group so he would inherit the same shared mailbox and resource permissions as the rest of the HR department.
![HR_Team group membership including Andrew Smith](screenshots/17-add-andrew-smith-to-hr-team-security-group.png)

### 18. Verified the account synced to Microsoft Entra ID
Confirmed Andrew Smith's new AD account had successfully synced through to Microsoft Entra ID as a cloud user via the hybrid identity sync.
![Andrew Smith listed as a synced user in Entra admin center](screenshots/18-verify-andrew-smith-synced-to-entra-id.png)

### 19. Assigned a Microsoft 365 licence
Assigned Andrew Smith a Microsoft 365 Business Premium with Copilot licence in the Microsoft 365 admin center so he could access email and productivity tools from day one.
![Microsoft 365 licence assignment for Andrew Smith](screenshots/19-assign-microsoft-365-license-to-andrew-smith.png)

### 20. Configured shared mailbox permissions for the new user
Navigated to the Exchange admin center to confirm and apply Andrew Smith's delegated Send As and Full Access permissions to the HR shared mailbox.
![Shared mailbox permissions for Andrew Smith in Exchange admin center](screenshots/20-configure-shared-mailbox-permissions.png)

### 21–22. Replied to the onboarding ticket confirming setup
Drafted and then sent a reply on the onboarding ticket confirming the account had been created, credentials stored securely, and access to the HR shared mailbox granted as requested.
![Draft reply confirming account creation](screenshots/21-draft-reply-confirming-account-creation.png)
![Sent reply confirming account and mailbox access](screenshots/22-send-reply-confirming-account-and-mailbox-access.png)

### 23. Documented the onboarding resolution with an internal note
Added an internal note summarizing all onboarding actions taken: AD account creation and Entra sync, licence assignment, and shared mailbox permissions granted.
![Internal note documenting onboarding steps](screenshots/23-internal-note-documenting-onboarding-steps.png)

### 24. Submitted an offboarding request
As Harry, submitted a new ticket requesting that Andrew Smith's access be revoked ahead of his last day, since he had decided to leave the company.
![Offboarding request ticket for Andrew Smith](screenshots/24-harry-submits-offboarding-request-andrew-smith.png)

### 25. Converted the departing user's mailbox to shared
Converted Andrew Smith's mailbox from a regular user mailbox to a shared mailbox in Exchange admin center, preserving his email history for the HR team while removing his personal licence dependency.
![Converting Andrew Smith's mailbox to a shared mailbox](screenshots/25-convert-andrew-smith-mailbox-to-shared.png)

### 26. Removed the Microsoft 365 licence
Removed Andrew Smith's Microsoft 365 licence in the admin center now that his mailbox no longer required one, freeing the licence for reassignment.
![Andrew Smith's account shown as Unlicensed](screenshots/26-remove-microsoft-365-license-from-andrew-smith.png)

### 27. Disabled the Active Directory account
Disabled Andrew Smith's Active Directory account to immediately prevent any further sign-ins, following standard offboarding security practice.
![Confirmation that Andrew Smith's AD account has been disabled](screenshots/27-disable-andrew-smith-ad-account.png)

### 28. Forced a directory sync to push the changes
Ran Start-ADSyncSyncCycle with a Delta sync from PowerShell to push the disabled account status from on-prem AD to Microsoft Entra ID immediately, rather than waiting for the next scheduled sync.
![PowerShell running a Delta Active Directory sync cycle](screenshots/28-run-delta-sync-to-push-ad-changes.png)

### 29. Verified sign-in was blocked
Confirmed in the Microsoft 365 admin center that Andrew Smith's account now showed Sign-in blocked, validating that the disablement had synced through correctly.
![Andrew Smith's account showing Sign-in blocked](screenshots/29-verify-sign-in-blocked-for-andrew-smith.png)

### 30. Documented the offboarding resolution with an internal note
Added a final internal note to the offboarding ticket summarizing the mailbox conversion, licence removal, and account disablement before closing it out.
![Internal note documenting offboarding steps](screenshots/30-internal-note-documenting-offboarding-steps.png)

## What I learned
Working through all three tickets back to back made it click just how much of IT support is coordination rather than any single technical task. Granting mailbox access wasn't just a permissions checkbox — it started with asking the right clarifying questions and getting approval on record before touching anything, which is exactly the kind of judgment call a recruiter can't see from a certificate alone. Onboarding and offboarding the same employee end to end also showed me how many systems actually need to talk to each other for one person's employment lifecycle: AD, Entra ID, Exchange, and licensing all had to be touched, in the right order, and then verified rather than assumed. Running the Delta sync manually instead of waiting for the scheduled cycle was a small thing, but it drove home that offboarding security matters on the order of minutes, not hours. And writing internal notes on every ticket, separate from what the customer sees, felt like the most "real job" part of this whole project — it's the difference between doing the work and being able to prove exactly what you did if someone asks later.
