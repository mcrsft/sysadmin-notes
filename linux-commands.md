# Linux SysAdmin Notes

A collection of essential commands, tips, and best practices for System Administrators managing Linux systems. This guide covers common tools, system administration tasks, and command-line techniques useful for daily operations.

## 🛠️ System Basics

* **User Management**

  * Add user: `useradd <username>`
  * Set password: `passwd <username>`
  * Delete user: `userdel -r <username>`
  * List users: `cut -d: -f1 /etc/passwd`

* **Group Management**

  * Add group: `groupadd <groupname>`
  * Add user to group: `usermod -aG <group> <user>`
  * Check groups: `groups <user>`

* **File Permissions**

  * View permissions: `ls -l`
  * Change permissions: `chmod <mode> <file>`
  * Change owner: `chown <user>:<group> <file>`
  * Numeric permissions: `chmod 755 <file>`

## 🖥️ System Monitoring

* **Process Management**

  * List processes: `ps aux` or `top` or `htop`
  * Kill process: `kill <pid>` or `killall <process>`
  * Background job control: `bg`, `fg`, `jobs`

* **Disk & Memory**

  * Disk usage: `df -h`
  * Directory size: `du -sh <dir>`
  * Memory usage: `free -h`

* **Network**

  * Check IP: `ip a` or `ifconfig`
  * Ping: `ping <host>`
  * Open ports: `ss -tuln`
  * DNS lookup: `dig <host>` or `nslookup <host>`

## 📦 Package Management

* **Debian/Ubuntu (APT)**

  * Update repos: `sudo apt update`
  * Upgrade system: `sudo apt upgrade`
  * Install package: `sudo apt install <pkg>`
  * Remove package: `sudo apt remove <pkg>`

* **RedHat/CentOS/Fedora (DNF/YUM)**

  * Update system: `sudo dnf update` or `sudo yum update`
  * Install package: `sudo dnf install <pkg>`
  * Remove package: `sudo dnf remove <pkg>`

## 🔒 Security & Access

* **SSH**

  * Connect: `ssh <user>@<host>`
  * Copy files: `scp <src> <user>@<host>:<dest>`
  * Generate key pair: `ssh-keygen`
  * Manage known hosts: `~/.ssh/known_hosts`

* **Firewall**

  * UFW (Ubuntu):

    * Enable: `sudo ufw enable`
    * Allow port: `sudo ufw allow 22`
    * Status: `sudo ufw status`
  * Firewalld (RHEL):

    * Start: `sudo systemctl start firewalld`
    * Open port: `sudo firewall-cmd --add-port=80/tcp --permanent`
    * Reload: `sudo firewall-cmd --reload`

## 📂 File Management

* **Navigation**

  * Current directory: `pwd`
  * List files: `ls -l`
  * Change directory: `cd <dir>`

* **File Operations**

  * Copy: `cp <src> <dest>`
  * Move: `mv <src> <dest>`
  * Delete: `rm <file>`
  * Create file: `touch <file>`
  * Create directory: `mkdir <dir>`

* **Archiving & Compression**

  * Tar: `tar -czvf archive.tar.gz <files>`
  * Extract: `tar -xzvf archive.tar.gz`
  * Zip: `zip archive.zip <files>`
  * Unzip: `unzip archive.zip`

## 📝 System Management

* **Services**

  * Start service: `sudo systemctl start <service>`
  * Enable at boot: `sudo systemctl enable <service>`
  * Check status: `sudo systemctl status <service>`

* **Logs**

  * View logs: `journalctl -xe` or `cat /var/log/syslog`
  * Tail log: `tail -f <logfile>`

* **Crontab (Scheduling)**

  * Edit crontab: `crontab -e`
  * List cron jobs: `crontab -l`
  * Cron format: `* * * * * /path/to/script`

## 🧪 Scripting Basics

* **Bash Scripting**

  * Start script with: `#!/bin/bash`
  * Variables: `VAR=value`
  * Conditionals: `if [ ]; then ... fi`
  * Loops: `for`, `while`

## 📌 Best Practices

* Use `sudo` for administrative tasks.
* Keep systems updated: `apt upgrade` or `dnf upgrade`.
* Set strong passwords.
* Use SSH keys instead of passwords for remote access.
* Backup critical data regularly.
* Document server configurations and changes.

## 🚀 Useful Resources

* [Linux Command Reference](https://linuxcommand.org)
* `man <command>` – built-in help system.
* `--help` flag for command-specific options.

---

*A practical guide for Linux system administrators.*

