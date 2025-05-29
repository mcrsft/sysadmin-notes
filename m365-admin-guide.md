# Microsoft 365 Admin Notes

A collection of notes and best practices for System Administrators managing Microsoft 365 environments. Suitable for use as quick references, checklists, or foundational documentation.

## 📂 Identity & Access Management

* **User Accounts**

  * Create users in M365 Admin Center or via Azure AD.
  * Bulk import via CSV or PowerShell (`New-MsolUser`).
  * Enforce MFA for all users via Conditional Access or Security Defaults.
* **Licensing**

  * Assign per user in Admin Center → Users → Active Users.
  * Licenses determine access (e.g., Business Premium vs. E3/E5).
* **Groups**

  * Types: Security, Microsoft 365, Distribution.
  * M365 Groups power Teams, Planner, SharePoint.
* **Admin Roles**

  * Follow Principle of Least Privilege.
  * Common roles: Global Admin, User Admin, Exchange Admin, SharePoint Admin, Teams Admin.
  * Use PIM (Privileged Identity Management) for time-limited access (Azure AD P2).

## 📧 Exchange Online

* **Mailboxes**

  * User Mailbox vs. Shared Mailbox (Shared <50GB = no license).
  * Delegate access: Full Access, Send As, Send on Behalf.
* **Mail Flow**

  * Configure Mail Flow Rules (Transport Rules) for DLP, signatures, disclaimers.
  * Use Connectors for hybrid Exchange/3rd-party services.
* **Anti-Spam/Phish**

  * Configure via Microsoft Defender for Office 365.
  * Manage Quarantine Policies, Spam Filters, Allow/Block Lists.
* **Email Retention**

  * Use Retention Policies in Compliance Center.
  * Litigation Hold is a legal lock.

## 🏢 SharePoint & OneDrive

* **Sites & Storage**

  * SharePoint sites link to Teams & Groups.
  * OneDrive: 1TB per user (default, expandable).
* **Permissions**

  * Use Groups for permissions, not individuals.
  * Site Owners, Members, Visitors.
* **Sharing**

  * Configure External Sharing (org-wide settings).
  * Limit anonymous sharing.

## 💬 Microsoft Teams

* **Teams & Channels**

  * Teams link to M365 Groups.
  * Channels: Standard, Private, Shared.
* **Policies**

  * Configure via Teams Admin Center: meetings, messaging, apps.
  * External & guest access controlled per-org & per-Team.
* **Calling**

  * Requires Phone System license.
  * Set up via Voice in Teams Admin Center.

## 🔍 Security & Compliance

* **Defender for M365**

  * Configure Threat Policies: anti-phish, anti-malware, safe links, safe attachments.
  * Review Secure Score regularly.
* **Compliance Center**

  * DLP, Information Protection, eDiscovery, Insider Risk.
* **Audit Logs**

  * Enable audit logging in Compliance Center.
* **Conditional Access**

  * Enforce MFA, device compliance, location-based access.
* **Secure Baselines**

  * Follow Microsoft Security Baselines.

## 🖥️ Device Management (Intune)

* **MDM/Intune**

  * Enroll devices via Company Portal.
  * Deploy compliance policies: PIN, encryption, antivirus.
* **App Protection**

  * Protect data at the app level (MAM) for BYOD.
* **Autopilot**

  * Automate provisioning of Windows 10/11 devices.

## 🛠️ Admin Tools & PowerShell

* **Admin Centers**

  * M365 Admin: Users, licensing, basic settings.
  * Exchange Admin: Mail flow, mailboxes.
  * Teams Admin: Policies, meetings, apps.
  * SharePoint Admin: Sites, storage, sharing.
* **PowerShell Modules**

  * MSOnline (`Connect-MsolService`)
  * AzureAD (`Connect-AzureAD`)
  * ExchangeOnline (`Connect-ExchangeOnline`)
  * Teams (`Connect-MicrosoftTeams`)
  * SharePoint (`Connect-SPOService`)
* **Common Cmdlets**

  * `Get-MsolUser`, `Set-MsolUserLicense`
  * `Get-Mailbox`, `Set-Mailbox`
  * `Get-TeamsPolicy`, `Grant-CsTeamsPolicy`

## 📝 General Best Practices

* Enable MFA for all users.
* Regularly review Audit Logs & Sign-in Reports.
* Periodically review licensing to avoid over/under-provisioning.
* Follow naming conventions for groups, mailboxes, policies.
* Document policies, user setups, security configurations.
* Monitor Microsoft 365 Roadmap for updates.

## 📌 Contributing

Want to contribute? Feel free to submit pull requests or open issues!

---

*A curated guide for System Administrators managing Microsoft 365 environments.*

