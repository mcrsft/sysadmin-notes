# Advanced Windows Server Setup Notes

A practical guide for System Administrators handling advanced Windows Server setups, including best practices, PowerShell commands, Active Directory configurations, and common roles and features.

## 🏢 Active Directory (AD)

* **AD Domain Services (AD DS)**

  * Install role: `Install-WindowsFeature -Name AD-Domain-Services`
  * Promote server to DC: `Install-ADDSForest -DomainName <domain.local>`
  * Manage users: `New-ADUser`, `Set-ADUser`, `Remove-ADUser`
  * Manage groups: `New-ADGroup`, `Add-ADGroupMember`
  * Check replication: `repadmin /replsummary`
  * Force replication: `repadmin /syncall`

* **Group Policy (GPO)**

  * Open: `gpmc.msc`
  * Common GPOs: Password policies, logon scripts, software deployment.
  * Update GPOs: `gpupdate /force`
  * Check applied GPOs: `gpresult /R`

## 🖥️ Server Roles & Features

* **File Services**

  * Install role: `Install-WindowsFeature -Name FS-FileServer`
  * Create share: `New-SmbShare -Name <ShareName> -Path <Path>`
  * Set permissions: `Grant-SmbShareAccess`

* **DHCP Server**

  * Install: `Install-WindowsFeature DHCP -IncludeManagementTools`
  * Authorize server: `Add-DhcpServerInDC -DnsName <server> -IPAddress <ip>`
  * Manage scopes: `Add-DhcpServerv4Scope`, `Set-DhcpServerv4OptionValue`

* **DNS Server**

  * Install: `Install-WindowsFeature DNS -IncludeManagementTools`
  * Configure zones: `Add-DnsServerPrimaryZone`, `Add-DnsServerResourceRecordA`
  * Test DNS: `Resolve-DnsName <host>`

* **Hyper-V**

  * Install: `Install-WindowsFeature Hyper-V -IncludeManagementTools`
  * Create VM: `New-VM -Name <VMName> -MemoryStartupBytes 2GB -NewVHDPath <path> -NewVHDSizeBytes 50GB`
  * Start/Stop VM: `Start-VM`, `Stop-VM`

## 🔒 Security Best Practices

* **User Accounts & Permissions**

  * Principle of Least Privilege (PoLP).
  * Use Role-Based Access Control (RBAC).

* **Secure Remote Access**

  * Enable RDP: `Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -Name 'fDenyTSConnections' -Value 0`
  * Configure RDP via GPO.
  * Use Network Level Authentication (NLA).

* **Windows Firewall**

  * Open ports: `New-NetFirewallRule -DisplayName "Allow RDP" -Direction Inbound -Protocol TCP -LocalPort 3389 -Action Allow`
  * Check rules: `Get-NetFirewallRule`

* **Patching & Updates**

  * Check for updates: `sconfig`
  * Install updates: `Install-WindowsUpdate -AcceptAll -AutoReboot`

## 🖥️ PowerShell Essentials

* **System Information**

  * `Get-ComputerInfo`
  * `Get-WmiObject -Class Win32_OperatingSystem`
* **Network Configuration**

  * View IP: `Get-NetIPAddress`
  * Set static IP: `New-NetIPAddress`
* **Service Management**

  * Check services: `Get-Service`
  * Restart service: `Restart-Service <name>`

## 📦 Backups & Recovery

* **Windows Server Backup**

  * Install: `Install-WindowsFeature Windows-Server-Backup`
  * Backup example: `wbadmin start backup -backupTarget:E: -include:C: -allCritical -quiet`

* **System State Backup**

  * Backup: `wbadmin start systemstatebackup -backupTarget:E:`
  * Restore: `wbadmin start systemstaterecovery`

## 📋 Common Configurations

* **Time Sync**

  * Check NTP: `w32tm /query /status`
  * Configure: `w32tm /config /manualpeerlist:"time.windows.com" /syncfromflags:manual /reliable:yes /update`
  * Resync: `w32tm /resync`

* **Certificates (AD CS)**

  * Install ADCS: `Install-WindowsFeature AD-Certificate -IncludeManagementTools`
  * Configure via `certsrv.msc`

* **Storage Management**

  * Create partition: `New-Partition`
  * Format volume: `Format-Volume`
  * Set drive letter: `Set-Partition -DriveLetter D`

## 📌 Best Practices

* Document everything (topology, settings, changes).
* Regular backups (full and system state).
* Apply least privilege principles.
* Keep OS and roles updated.
* Use monitoring (e.g., Nagios, PRTG, Windows Admin Center).
* Plan for disaster recovery.

## 📝 Useful Tools

* Server Manager (`servermanager.exe`)
* Event Viewer (`eventvwr.msc`)
* Task Scheduler (`taskschd.msc`)
* Resource Monitor (`resmon`)
* Performance Monitor (`perfmon`)

## 📌 References

* [Microsoft Learn – Windows Server](https://learn.microsoft.com/en-us/windows-server/)
* `Get-Help <cmdlet>` for PowerShell command reference.

---

*A comprehensive guide for advanced Windows Server setup and management.*

