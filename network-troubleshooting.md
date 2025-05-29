# Network Troubleshooting Notes

A collection of essential commands, tools, and techniques for troubleshooting networks in Linux, Windows, and mixed environments. Useful for system administrators and IT professionals handling connectivity issues, diagnostics, and performance monitoring.

## 🌐 Network Basics

* **Check IP Configuration**

  * Linux: `ip a` or `ifconfig`
  * Windows: `ipconfig`
* **Check Default Gateway**

  * Linux: `ip route` or `route -n`
  * Windows: `ipconfig`
* **Check DNS Configuration**

  * Linux: `cat /etc/resolv.conf`
  * Windows: `ipconfig /all`

## 🔎 Connectivity Tests

* **Ping**

  * `ping <host>` – test basic reachability.
* **Traceroute**

  * Linux: `traceroute <host>` (may need to install)
  * Windows: `tracert <host>`
* **NSLookup/Dig**

  * Linux: `dig <host>` or `nslookup <host>`
  * Windows: `nslookup <host>`
* **Port Checking**

  * Linux: `nc -zv <host> <port>` or `telnet <host> <port>`
  * Windows: `Test-NetConnection <host> -Port <port>` (PowerShell)

## 🛠️ Common Tools

* **Nmap**

  * Port scanning: `nmap <host>`
  * OS detection: `nmap -O <host>`
* **Netcat (nc)**

  * Test listening ports: `nc -lvp <port>`
  * Send files: `nc <host> <port> < file`
* **Tcpdump/Wireshark**

  * Linux packet capture: `sudo tcpdump -i <interface>`
  * GUI analysis: Use Wireshark for packet analysis.
* **Netstat/SS**

  * Linux: `ss -tuln` or `netstat -tulnp`
  * Windows: `netstat -ano`

## 🌐 DNS Troubleshooting

* **Test DNS Resolution**

  * `nslookup <host>` or `dig <host>`
* **Flush DNS Cache**

  * Linux: `sudo systemd-resolve --flush-caches` (or `sudo resolvectl flush-caches`)
  * Windows: `ipconfig /flushdns`

## 📦 Packet Capture & Analysis

* **Capture Traffic**

  * `tcpdump -i <interface> -w capture.pcap`
* **Filter Examples**

  * Specific host: `tcpdump host <ip>`
  * Port: `tcpdump port 80`
  * Protocol: `tcpdump icmp`
* **Analyze with Wireshark**

  * Open `.pcap` file for detailed analysis.

## 🛡️ Firewall & Security Checks

* **Linux Firewall (UFW/iptables)**

  * List rules: `sudo ufw status` or `sudo iptables -L`
  * Allow port: `sudo ufw allow 22` or `sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT`
* **Windows Firewall**

  * Check rules: `Get-NetFirewallRule` (PowerShell)

## 🖥️ Network Services

* **Restart Networking**

  * Linux (systemd): `sudo systemctl restart NetworkManager`
  * Linux (Debian/Ubuntu): `sudo systemctl restart networking`
  * Windows: `Restart-Service -Name 'Dnscache'` or `net stop/start <service>`

## 🚦 Performance Testing

* **Speed Test (CLI)**

  * `speedtest-cli`
* **iperf**

  * Start server: `iperf3 -s`
  * Run client: `iperf3 -c <server_ip>`

## 📋 Quick Checklist

* ✅ Check cables and physical connections.
* ✅ Confirm IP configuration.
* ✅ Ping gateway and DNS servers.
* ✅ Check routes (`ip route` or `route print`).
* ✅ Test DNS resolution.
* ✅ Verify firewall rules.
* ✅ Scan for open ports (nmap).
* ✅ Capture packets if needed.

## 📝 Best Practices

* Document network topology.
* Label cables and ports.
* Implement monitoring (e.g., Nagios, Zabbix, PRTG).
* Backup configurations regularly.
* Apply firmware updates to network devices.
* Segment networks (VLANs) for security.

## 📌 Resources

* [Linux Networking Commands Cheat Sheet](https://cheatography.com/tag/linux-networking/)
* `man <command>` for detailed help.

---

*A practical guide for troubleshooting networks in Linux and Windows environments.*

