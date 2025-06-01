# Scan-Your-Local-Network-for-Open-Ports
Step 1: Install Nmap
Visit the official Nmap website: https://nmap.org/download.html

Download the appropriate installer for your OS:

Windows: Use the .exe installer.
Linux: Use sudo apt install nmap (Debian/Ubuntu) or sudo yum install nmap (Red Hat/CentOS).
Mac: Use brew install nmap if you have Homebrew installed.

Step 2: Find Your Local IP Range
Open a terminal or command prompt.

Run the command:
Windows: ipconfig
Linux/Mac: ifconfig or ip a
Example Output:
IPv4 Address: 192.168.1.5
Subnet Mask: 255.255.255.0

Step 3: Run TCP SYN Scan
nmap -sS 192.168.1.0/24

Step 4: Note Down IP Addresses and Open Ports
Nmap scan report for 192.168.1.1
Host is up.
PORT     STATE SERVICE
80/tcp   open  http
443/tcp  open  https

Nmap scan report for 192.168.1.10
Host is up.
PORT     STATE SERVICE
22/tcp   open  ssh

Step 5: Analyze with Wireshark (Optional)
Open Wireshark.
Start capturing packets on your Wi-Fi or Ethernet interface.
Then run your Nmap scan again.

Observe:
SYN packets being sent.
SYN-ACK (open) or RST (closed) responses.

| Port | Service | Description                  |
| ---- | ------- | ---------------------------- |
| 80   | HTTP    | Web server, often exposed    |
| 443  | HTTPS   | Secure web traffic           |
| 22   | SSH     | Remote login                 |
| 21   | FTP     | File Transfer Protocol       |
| 3306 | MySQL   | Database service (sensitive) |

Use websites like:

https://www.speedguide.net/port.php
https://nmap.org/book/services.html

Step 7: Identify Potential Security Risks
Example risks:
Port 22 open: May allow SSH brute-force attacks if not protected.
Port 80/443 open: Could expose web server vulnerabilities.
Unused open ports: Could be used by attackers for backdoors or lateral movement.

Mitigation:
Close unused ports.
Enable firewalls.
Use strong passwords and patch services.

Step 8: Save Scan Results
To save results:

As Text File:
nmap -sS 192.168.1.0/24 -oN scan_results.txt

As HTML File (Requires xsltproc):
nmap -sS 192.168.1.0/24 -oX scan.xml
xsltproc scan.xml -o scan.html

GitHub Repository Structure (Recommended):
nmap-port-scan-task/
├── README.md
├── scan_results.txt
├── scan.html
├── screenshots/
│   └── nmap_output.png
├── wireshark/
│   └── capture.pcapng (optional)

OUTCOMES:
“By completing this task, I successfully performed a TCP SYN scan using Nmap to identify active devices and open ports in my local network. I analyzed the scan results to understand the services running on these ports and assessed their potential security risks. This task provided hands-on experience in basic network reconnaissance and reinforced the importance of port-level security in a cybersecurity context.”
